# `TerrainComp.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+180/-31` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Awake() [Method Body Modified]`
- `CheckSnow() [Method Body Modified]`
- `ComputePaintMaskHash() [Method Body Modified]`
- `DoOperation() [Method Body Modified]`
- `FindTerrainCompiler() [Method Body Modified]`
- `IncrementSnowMask() [Method Body Modified]`
- `Initialize() [Method Body Modified]`
- `IsAreaReadyForSnow() [Method Body Modified]`
- `Load() [Method Body Modified]`
- `PaintCleared() [Method Body Modified]`
- `Update() [Method Body Modified]`
- `UpgradeTerrain() [Method Body Modified]`
- `private IEnumerator IncrementSnowMask(float amount)`
- `private bool IsAreaReadyForSnow()`
- `private void CheckSnow()`
- `public bool SetSnowMask(float depth = -1f, bool checkCovered = false)`
- `public void SetSnowMask(float depth = -1f)`

---

## 📝 Code Diff

```diff
--- a/TerrainComp.cs
+++ b/TerrainComp.cs
@@ -1,13 +1,19 @@
+using System;
+using System.Collections;
 using System.Collections.Generic;
 using System.Linq;
+using Unity.Collections;
+using Unity.Jobs;
 using UnityEngine;
 
 public class TerrainComp : MonoBehaviour
 {
-	private const int terrainCompVersion = 1;
+	private const int terrainCompVersion = 2;
 
 	private int m_lastHash;
 
+	private static readonly List<ZDO> s_tmpZdos = new List<ZDO>();
+
 	private static List<float> m_neighborHeights = new List<float>();
 
 	private static readonly List<TerrainComp> s_instances = new List<TerrainComp>();
@@ -44,12 +50,28 @@
 
 	private float m_lastOpRadius;
 
+	private double m_lastSnowTimerIncrement;
+
 	private List<Heightmap> m_neighbors;
 
 	private TerrainComp[,] m_neighborGrid;
 
+	private static int s_snowBlockRayMask = 0;
+
+	private float m_snowUpdateTimer;
+
+	private float m_snowRecoverTimeMinutes = 120f;
+
+	private static int m_lastSnowCheckFrame;
+
+	private bool[] m_snowSettled;
+
 	private void Awake()
 	{
+		if (s_snowBlockRayMask == 0)
+		{
+			s_snowBlockRayMask = LayerMask.GetMask("piece");
+		}
 		m_nview = GetComponent<ZNetView>();
 		m_hmap = Heightmap.FindHeightmap(transform.position);
 		if (m_hmap == null)
@@ -115,6 +137,7 @@
 		if (m_nview.IsValid())
 		{
 			CheckLoad();
+			CheckSnow();
 		}
 	}
 
@@ -130,6 +153,7 @@
 		m_modifiedPaint = new bool[m_pitch * m_pitch];
 		m_paintMask = new Color[m_pitch * m_pitch];
 		m_paintMask = m_hmap.GetPaintMask().GetPixels();
+		m_snowSettled = new bool[m_pitch * m_pitch];
 	}
 
 	private int ComputePaintMaskHash()
@@ -163,7 +187,7 @@
 		}
 		m_lastHash = num;
 		ZPackage zPackage = new ZPackage();
-		zPackage.Write(1);
+		zPackage.Write(2);
 		zPackage.Write(m_operations);
 		zPackage.Write(m_lastOpPoint);
 		zPackage.Write(m_lastOpRadius);
@@ -189,6 +213,7 @@
 				zPackage.Write(m_paintMask[j].a);
 			}
 		}
+		zPackage.Write(m_lastSnowTimerIncrement);
 		byte[] bytes = Utils.Compress(zPackage.GetArray());
 		m_nview.GetZDO().Set(ZDOVars.s_TCData, bytes);
 		m_lastDataRevision = m_nview.GetZDO().DataRevision;
@@ -228,17 +253,17 @@
 			return false;
 		}
 		ZPackage zPackage = new ZPackage(Utils.Decompress(byteArray));
-		zPackage.ReadInt();
+		int num = zPackage.ReadInt();
 		m_operations = zPackage.ReadInt();
 		m_lastOpPoint = zPackage.ReadVector3();
 		m_lastOpRadius = zPackage.ReadSingle();
-		int num = zPackage.ReadInt();
-		if (num != m_modifiedHeight.Length)
+		int num2 = zPackage.ReadInt();
+		if (num2 != m_modifiedHeight.Length)
 		{
 			ZLog.LogWarning("Terrain data load error, height array missmatch");
 			return false;
 		}
-		for (int i = 0; i < num; i++)
+		for (int i = 0; i < num2; i++)
 		{
 			m_modifiedHeight[i] = zPackage.ReadBool();
 			if (m_modifiedHeight[i])
@@ -252,8 +277,8 @@
 				m_smoothDelta[i] = 0f;
 			}
 		}
-		int num2 = zPackage.ReadInt();
-		for (int j = 0; j < num2; j++)
+		int num3 = zPackage.ReadInt();
+		for (int j = 0; j < num3; j++)
 		{
 			m_modifiedPaint[j] = zPackage.ReadBool();
 			if (m_modifiedPaint[j])
@@ -268,31 +293,94 @@
 				m_paintMask[j] = color;
 			}
 		}
-		if (num2 == m_width * m_width)
+		if (num >= 2)
+		{
+			m_lastSnowTimerIncrement = zPackage.ReadDouble();
+		}
+		Array.Clear(m_snowSettled, 0, m_snowSettled.Length);
+		if (num3 == m_width * m_width)
 		{
 			Color[] array = new Color[m_paintMask.Length];
 			m_paintMask.CopyTo(array, 0);
 			bool[] array2 = new bool[m_modifiedPaint.Length];
 			m_modifiedPaint.CopyTo(array2, 0);
-			int num3 = m_width + 1;
+			int num4 = m_width + 1;
 			for (int k = 0; k < m_paintMask.Length; k++)
 			{
-				int num4 = k / num3;
-				int num5 = (k + 1) / num3;
-				int num6 = k - num4;
-				if (num4 == m_width)
-				{
-					num6 -= m_width;
-				}
-				if (k > 0 && (k - num4) % m_width == 0 && (k + 1 - num5) % m_width == 0)
-				{
-					num6--;
-				}
-				m_paintMask[k] = array[num6];
-				m_modifiedPaint[k] = array2[num6];
+				int num5 = k / num4;
+				int num6 = (k + 1) / num4;
+				int num7 = k - num5;
+				if (num5 == m_width)
+				{
+					num7 -= m_width;
+				}
+				if (k > 0 && (k - num5) % m_width == 0 && (k + 1 - num6) % m_width == 0)
+				{
+					num7--;
+				}
+				m_paintMask[k] = array[num7];
+				m_modifiedPaint[k] = array2[num7];
 			}
 		}
 		return true;
+	}
+
+	private bool IsAreaReadyForSnow()
+	{
+		Vector2s zone = ZoneSystem.GetZone(transform.position);
+		if (!ZoneSystem.instance.IsZoneLoaded(zone))
+		{
+			return false;
+		}
+		ZNetScene instance = ZNetScene.instance;
+		for (int i = -1; i <= 1; i++)
+		{
+			for (int j = -1; j <= 1; j++)
+			{
+				Vector2s vector2s = new Vector2s(zone.x + j, zone.y + i);
+				if (!ZoneSystem.instance.IsZoneLoaded(vector2s))
+				{
+					continue;
+				}
+				s_tmpZdos.Clear();
+				ZDOMan.instance.FindSectorObjects(vector2s, new SimulationDistance(0, 0), s_tmpZdos);
+				foreach (ZDO s_tmpZdo in s_tmpZdos)
+				{
+					if (instance.IsPrefabZDOValid(s_tmpZdo) && !instance.FindInstance(s_tmpZdo))
+					{
+						return false;
+					}
+				}
+			}
+		}
+		return true;
+	}
+
+	private void CheckSnow()
+	{
+		if (!m_nview.IsOwner())
+		{
+			return;
+		}
+		m_snowUpdateTimer -= Time.deltaTime;
+		if (!(m_snowUpdateTimer <= 0f) || m_lastSnowCheckFrame == Time.frameCount)
+		{
+			return;
+		}
+		if (!IsAreaReadyForSnow())
+		{
+			m_snowUpdateTimer++;
+			return;
+		}
+		m_lastSnowCheckFrame = Time.frameCount;
+		m_snowUpdateTimer = 60f;
+		if (WorldGenerator.instance.GetBiome(transform.position.x, transform.position.z) == Heightmap.Biome.DeepNorth)
+		{
+			double num = ZNet.instance.GetTimeSeconds() - m_lastSnowTimerIncrement;
+			float amount = (float)(0.5799999833106995 * num / (double)(m_snowRecoverTimeMinutes * 60f));
+			m_lastSnowTimerIncrement = ZNet.instance.GetTimeSeconds();
+			StartCoroutine(IncrementSnowMask(amount));
+		}
 	}
 
 	public static TerrainComp FindTerrainCompiler(Vector3 pos)
@@ -417,10 +505,11 @@
 		if (m_initialized)
 		{
 			InternalDoOperation(pos, rot, modifier);
-			bool paintOnly = modifier.m_paintCleared && !modifier.m_level && !modifier.m_raise && !modifier.m_smooth;
-			Save(paintOnly);
-			m_hmap.Poke(1, paintOnly);
-			if ((bool)ClutterSystem.instance)
+			bool flag = modifier.m_paintCleared && !modifier.m_level && !modifier.m_raise && !modifier.m_smooth;
+			Save(flag);
+			m_hmap.Poke(1, flag);
+			bool flag2 = !flag || modifier.m_paintStrength > 0.1f;
+			if ((bool)ClutterSystem.instance & flag2)
 			{
 				ClutterSystem.instance.ResetGrass(pos, modifier.GetRadius());
 			}
@@ -676,6 +765,7 @@
 					}
 					color2.a = a2;
 					m_modifiedPaint[num10] = true;
+					m_snowSettled[num10] = false;
 					m_paintMask[num10] = color2;
 					if (x3 == 0)
 					{
@@ -745,6 +835,7 @@
 						GetNearestVertex(terrainComp, x3, y3, out var ox2, out var oy2);
 						int num13 = getIndex(ox2, oy2);
 						terrainComp.m_modifiedPaint[num13] = true;
+						terrainComp.m_snowSettled[num13] = false;
 						terrainComp.m_paintMask[num13] = color2;
 						bool paintOnly = settings.m_paintCleared && !settings.m_level && !settings.m_raise && !settings.m_smooth;
 						terrainComp.m_hmap.Poke(1, paintOnly);
@@ -953,6 +1044,7 @@
 				if (!(color == paintMask))
 				{
 					andCreateTerrainCompiler.m_modifiedPaint[num10] = true;
+					andCreateTerrainCompiler.m_snowSettled[num10] = false;
 					andCreateTerrainCompiler.m_paintMask[num10] = color;
 					num7++;
 				}
@@ -968,22 +1060,79 @@
 		return true;
 	}
 
-	public void SetSnowMask(float depth = -1f)
-	{
+	public bool SetSnowMask(float depth = -1f, bool checkCovered = false)
+	{
+		bool result = false;
 		for (int i = 0; i < m_paintMask.Length; i++)
 		{
 			m_modifiedPaint[i] = true;
+			m_snowSettled[i] = false;
 			int x = i % m_pitch;
 			int y = i / m_pitch;
 			Vector3 vector = m_hmap.VertexMaskToWorld(x, y);
-			WorldGenerator.instance.GetBiomeHeight(Heightmap.Biome.DeepNorth, vector.x, vector.y, out var mask);
+			WorldGenerator.instance.GetBiomeHeight(Heightmap.Biome.DeepNorth, vector.x, vector.z, out var mask);
 			if (depth != -1f)
 			{
 				mask.g = depth;
 			}
-			m_paintMask[i] = mask;
+			m_paintMask[i].g = mask.g;
 		}
 		Save();
 		m_hmap.Poke(1);
+		return result;
+	}
+
+	private IEnumerator IncrementSnowMask(float amount)
+	{
+		QueryParameters queryParameters = new QueryParameters
+		{
+			layerMask = s_snowBlockRayMask,
+			hitTriggers = QueryTriggerInteraction.Ignore
+		};
+		List<int> modifiedIndex = new List<int>();
+		for (int i = 0; i < m_paintMask.Length; i++)
+		{
+			if (m_modifiedPaint[i] && !m_snowSettled[i])
+			{
+				modifiedIndex.Add(i);
+			}
+		}
+		int count = modifiedIndex.Count;
+		if (count == 0)
+		{
+			yield break;
+		}
+		NativeArray<RaycastCommand> commands = new NativeArray<RaycastCommand>(count, Allocator.TempJob);
+		NativeArray<RaycastHit> hits = new NativeArray<RaycastHit>(count, Allocator.TempJob);
+		for (int j = 0; j < count; j++)
+		{
+			int num = modifiedIndex[j];
+			Vector3 vector = m_hmap.VertexMaskToWorld(num % m_pitch, num / m_pitch);
+			commands[j] = new RaycastCommand(vector + Vector3.up * 100f, Vector3.down, queryParameters);
+		}
+		JobHandle handle = RaycastCommand.ScheduleBatch(commands, hits, 1);
+		yield return null;
+		handle.Complete();
+		for (int k = 0; k < count; k++)
+		{
+			int num2 = modifiedIndex[k];
+			if (hits[k].collider == null)
+			{
+				WorldGenerator.instance.GetBiomeHeight(Heightmap.Biome.DeepNorth, commands[k].from.x, commands[k].from.z, out var mask);
+				float g = m_paintMask[num2].g;
+				if (g >= mask.g)
+				{
+					m_snowSettled[num2] = true;
+					continue;
+				}
+				float num3 = Mathf.Min(g + amount, mask.g);
+				m_paintMask[num2].g = num3;
+				m_modifiedPaint[num2] = num3 < mask.g - 0.0001f;
+			}
+		}
+		Save(paintOnly: true);
+		m_hmap.Poke(1, paintOnly: true);
+		commands.Dispose();
+		hits.Dispose();
 	}
 }
```

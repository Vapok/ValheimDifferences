# `TerrainComp.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+83/-14` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `private void Start()`
- `private void TryCleanInvalidTCs()`
- `public static List<TerrainComp> FindAllTerrainCompilers(Vector3 pos)`
- `public static bool ValidTCForAllAffectedHeightmaps(Vector3 pos, float radius)`

---

## 📝 Code Diff

```diff
--- a/TerrainComp.cs
+++ b/TerrainComp.cs
@@ -1,4 +1,5 @@
 using System.Collections.Generic;
+using System.Linq;
 using UnityEngine;
 
 public class TerrainComp : MonoBehaviour
@@ -11,6 +12,8 @@
 
 	private static readonly List<TerrainComp> s_instances = new List<TerrainComp>();
 
+	private static readonly HashSet<TerrainComp> s_duplicateInstances = new HashSet<TerrainComp>();
+
 	private bool m_initialized;
 
 	private int m_width;
@@ -48,27 +51,58 @@
 	private void Awake()
 	{
 		m_nview = GetComponent<ZNetView>();
-		m_hmap = Heightmap.FindHeightmap(base.transform.position);
+		m_hmap = Heightmap.FindHeightmap(transform.position);
 		if (m_hmap == null)
 		{
 			ZLog.LogWarning("Terrain compiler could not find hmap");
 			return;
 		}
-		TerrainComp terrainComp = FindTerrainCompiler(base.transform.position);
+		TerrainComp terrainComp = FindTerrainCompiler(transform.position);
 		if ((bool)terrainComp)
 		{
-			ZLog.LogWarning("Found another terrain compiler in this area, removing it");
-			if (terrainComp.m_nview.IsValid() && !terrainComp.m_nview.HasOwner())
-			{
-				terrainComp.m_nview.ClaimOwnership();
-			}
-			ZNetScene.instance.Destroy(terrainComp.gameObject);
-			s_instances.Remove(terrainComp);
+			s_duplicateInstances.Add(terrainComp);
+			s_duplicateInstances.Add(this);
 		}
 		s_instances.Add(this);
 		m_nview.Register<ZPackage>("RPC_ApplyOperation", RPC_ApplyOperation);
 		Initialize();
 		CheckLoad();
+	}
+
+	private void Start()
+	{
+		TryCleanInvalidTCs();
+	}
+
+	private void TryCleanInvalidTCs()
+	{
+		if (s_duplicateInstances.Count == 0)
+		{
+			return;
+		}
+		s_duplicateInstances.TryGetValue(this, out var actualValue);
+		Vector3 position = transform.position;
+		Vector3? vector = actualValue?.transform.position;
+		if (position != vector)
+		{
+			return;
+		}
+		List<TerrainComp> list = s_duplicateInstances.OrderBy((TerrainComp x) => x.m_operations).ToList();
+		for (int num = 0; num < list.Count - 1; num++)
+		{
+			TerrainComp terrainComp = list[num];
+			if (terrainComp.m_nview.IsValid() && !terrainComp.m_nview.HasOwner())
+			{
+				terrainComp.m_nview.ClaimOwnership();
+			}
+			ZNetScene.instance.Destroy(terrainComp.gameObject);
+			s_instances.Remove(terrainComp);
+			ZLog.LogWarning($"Removed duplicate terrain compiler with {terrainComp.m_operations} operations performed on it.");
+		}
+		TerrainComp terrainComp2 = list[list.Count - 1];
+		int count = FindAllTerrainCompilers(terrainComp2.transform.position).Count;
+		s_duplicateInstances.Clear();
+		ZLog.Log($"There should only be one terrainCompiler found at this area now, is that correct? [{count == 1}]. Amount of operations the terrain compiler that was kept: [{FindTerrainCompiler(terrainComp2.transform.position).m_operations}]");
 	}
 
 	private void OnDestroy()
@@ -275,6 +309,36 @@
 		return null;
 	}
 
+	public static List<TerrainComp> FindAllTerrainCompilers(Vector3 pos)
+	{
+		List<TerrainComp> list = new List<TerrainComp>();
+		foreach (TerrainComp s_instance in s_instances)
+		{
+			float num = s_instance.m_size / 2f;
+			Vector3 position = s_instance.transform.position;
+			if (pos.x >= position.x - num && pos.x <= position.x + num && pos.z >= position.z - num && pos.z <= position.z + num)
+			{
+				list.Add(s_instance);
+			}
+		}
+		return list;
+	}
+
+	public static bool ValidTCForAllAffectedHeightmaps(Vector3 pos, float radius)
+	{
+		List<Heightmap> list = new List<Heightmap>();
+		Heightmap.FindHeightmap(pos, radius, list);
+		int num = 0;
+		foreach (Heightmap item in list)
+		{
+			if ((bool)FindTerrainCompiler(item.transform.position))
+			{
+				num++;
+			}
+		}
+		return num == list.Count;
+	}
+
 	public void ApplyToHeightmap(Texture2D clearedMask, List<float> heights, float[] baseHeights, float[] levelOnlyHeights, Heightmap hm)
 	{
 		if (!m_initialized)
@@ -314,6 +378,11 @@
 
 	public void ApplyOperation(TerrainOp modifier)
 	{
+		if (!m_nview.IsValid())
+		{
+			ZLog.LogError("Attempted to apply operation on invalid TerrainComp");
+			return;
+		}
 		ZPackage zPackage = new ZPackage();
 		zPackage.Write(modifier.transform.position);
 		zPackage.Write(modifier.m_settings.m_rotation);
@@ -384,7 +453,7 @@
 	private void LevelTerrain(Vector3 worldPos, float radius, bool square)
 	{
 		m_hmap.WorldToVertex(worldPos, out var x, out var y);
-		Vector3 vector = worldPos - base.transform.position;
+		Vector3 vector = worldPos - transform.position;
 		float num = radius / m_hmap.m_scale;
 		int num2 = Mathf.CeilToInt(num);
 		int num3 = m_width + 1;
@@ -411,7 +480,7 @@
 	private void RaiseTerrain(Vector3 worldPos, float radius, float delta, bool square, float power)
 	{
 		m_hmap.WorldToVertex(worldPos, out var x, out var y);
-		Vector3 vector = worldPos - base.transform.position;
+		Vector3 vector = worldPos - transform.position;
 		float num = radius / m_hmap.m_scale;
 		int num2 = Mathf.CeilToInt(num);
 		int num3 = m_width + 1;
@@ -473,7 +542,7 @@
 	private void SmoothTerrain(Vector3 worldPos, float radius, bool square, float power)
 	{
 		m_hmap.WorldToVertex(worldPos, out var x, out var y);
-		float b = worldPos.y - base.transform.position.y;
+		float b = worldPos.y - transform.position.y;
 		float num = radius / m_hmap.m_scale;
 		int num2 = Mathf.CeilToInt(num);
 		Vector2 a = new Vector2(x, y);
@@ -507,7 +576,7 @@
 			worldPos.z -= 0.5f;
 		}
 		bool isChangingSnow = WorldGenerator.IsDeepnorth(worldPos.x, worldPos.z) && settings.m_paintType == TerrainModifier.PaintType.Cultivate;
-		float num = worldPos.y - base.transform.position.y;
+		float num = worldPos.y - transform.position.y;
 		m_hmap.WorldToVertexMask(worldPos, out var x, out var y);
 		float num2 = settings.m_paintRadius / m_hmap.m_scale;
 		int num3 = Mathf.CeilToInt(num2);
@@ -718,7 +787,7 @@
 		{
 			m_neighbors.Clear();
 			Heightmap.FindHeightmap(worldPos, radius, m_neighbors);
-			Vector3 position = base.transform.position;
+			Vector3 position = transform.position;
 			foreach (Heightmap neighbor in m_neighbors)
 			{
 				Vector3 position2 = neighbor.transform.position;
```

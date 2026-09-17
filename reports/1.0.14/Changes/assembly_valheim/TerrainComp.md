# `TerrainComp.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+20/-13` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `private TerrainComp GetNeighbor(Vector3 worldPos, int x, int y, float radius)`
- `private TerrainComp TryGetNeighbor(Vector3 worldPos, int x, int y, float radius)`

---

## 📝 Code Diff

```diff
--- a/TerrainComp.cs
+++ b/TerrainComp.cs
@@ -58,7 +58,14 @@
 		if ((bool)terrainComp)
 		{
 			ZLog.LogWarning("Found another terrain compiler in this area, removing it");
-			ZNetScene.instance.Destroy(terrainComp.gameObject);
+			if (m_nview.IsValid() && !m_nview.HasOwner())
+			{
+				m_nview.ClaimOwnership();
+			}
+			if (m_nview.IsOwner())
+			{
+				ZNetScene.instance.Destroy(terrainComp.gameObject);
+			}
 		}
 		s_instances.Add(this);
 		m_nview.Register<ZPackage>("RPC_ApplyOperation", RPC_ApplyOperation);
@@ -516,7 +523,7 @@
 				if ((bool)heightmap)
 				{
 					heightmap.WorldToVertexMask(worldPos, out var x2, out var y2);
-					color = getMask(heightmap, heightmap.GetAndCreateTerrainCompiler(), x2, y2, getIndex(x2, y2));
+					color = getMask(heightmap, FindTerrainCompiler(heightmap.transform.position), x2, y2, getIndex(x2, y2));
 				}
 			}
 			else
@@ -665,16 +672,16 @@
 					{
 						return false;
 					}
-					TerrainComp neighbor = GetNeighbor(worldPos, ox, oy, settings.m_paintRadius);
-					if (neighbor != null)
-					{
-						GetNearestVertex(neighbor, x3, y3, out var ox2, out var oy2);
+					TerrainComp terrainComp = TryGetNeighbor(worldPos, ox, oy, settings.m_paintRadius);
+					if (terrainComp != null)
+					{
+						GetNearestVertex(terrainComp, x3, y3, out var ox2, out var oy2);
 						int num13 = getIndex(ox2, oy2);
-						neighbor.m_modifiedPaint[num13] = true;
-						neighbor.m_paintMask[num13] = color2;
+						terrainComp.m_modifiedPaint[num13] = true;
+						terrainComp.m_paintMask[num13] = color2;
 						bool paintOnly = settings.m_paintCleared && !settings.m_level && !settings.m_raise && !settings.m_smooth;
-						neighbor.Save(paintOnly);
-						neighbor.m_hmap.Poke(1, paintOnly);
+						terrainComp.Save(paintOnly);
+						terrainComp.m_hmap.Poke(1, paintOnly);
 					}
 					return true;
 				}
@@ -696,7 +703,7 @@
 		}
 		static Color getMask(Heightmap hmap, TerrainComp tc, int x4, int y4, int index)
 		{
-			if (hmap.m_doLateUpdate != 1)
+			if (hmap.m_doLateUpdate != 1 || !(tc != null))
 			{
 				return hmap.GetPaintMask(x4, y4);
 			}
@@ -704,7 +711,7 @@
 		}
 	}
 
-	private TerrainComp GetNeighbor(Vector3 worldPos, int x, int y, float radius)
+	private TerrainComp TryGetNeighbor(Vector3 worldPos, int x, int y, float radius)
 	{
 		if (m_neighborGrid == null)
 		{
@@ -720,7 +727,7 @@
 				Vector3 position2 = neighbor.transform.position;
 				int num = ((!(position2.x < position.x)) ? ((!(position2.x > position.x)) ? 1 : 2) : 0);
 				int num2 = ((!(position2.z < position.z)) ? ((!(position2.z > position.z)) ? 1 : 2) : 0);
-				m_neighborGrid[num, num2] = neighbor.GetAndCreateTerrainCompiler();
+				m_neighborGrid[num, num2] = FindTerrainCompiler(neighbor.transform.position);
 			}
 		}
 		return m_neighborGrid[x, y];
```

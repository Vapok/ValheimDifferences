# `TerrainLod.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/TerrainLod.cs
+++ b/TerrainLod.cs
@@ -74,10 +74,10 @@
 
 	private void CreateMesh(float scale, int width, Vector3 offset)
 	{
-		GameObject obj = new GameObject("lodMesh");
-		obj.transform.position = offset;
-		obj.transform.SetParent(base.transform);
-		Heightmap heightmap = obj.AddComponent<Heightmap>();
+		GameObject gameObject = new GameObject("lodMesh");
+		gameObject.transform.position = offset;
+		gameObject.transform.SetParent(transform);
+		Heightmap heightmap = gameObject.AddComponent<Heightmap>();
 		m_heightmaps.Add(new HeightmapWithOffset(heightmap, offset));
 		heightmap.m_scale = scale;
 		heightmap.m_width = width;
```

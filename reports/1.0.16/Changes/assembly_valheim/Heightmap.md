# `Heightmap.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+22/-22` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Heightmap.cs
+++ b/Heightmap.cs
@@ -195,23 +195,23 @@
 		m_meshFilter = GetComponent<MeshFilter>();
 		if (!m_meshFilter)
 		{
-			m_meshFilter = base.gameObject.AddComponent<MeshFilter>();
+			m_meshFilter = gameObject.AddComponent<MeshFilter>();
 		}
 		m_meshRenderer = GetComponent<MeshRenderer>();
 		if (!m_meshRenderer)
 		{
-			m_meshRenderer = base.gameObject.AddComponent<MeshRenderer>();
+			m_meshRenderer = gameObject.AddComponent<MeshRenderer>();
 		}
 		m_meshRenderer.motionVectorGenerationMode = MotionVectorGenerationMode.Camera;
 		m_renderGroupSubscriber = GetComponent<RenderGroupSubscriber>();
 		if (!m_renderGroupSubscriber)
 		{
-			m_renderGroupSubscriber = base.gameObject.AddComponent<RenderGroupSubscriber>();
+			m_renderGroupSubscriber = gameObject.AddComponent<RenderGroupSubscriber>();
 		}
 		m_renderGroupSubscriber.Group = RenderGroup.Overworld;
 		if (m_material == null)
 		{
-			base.enabled = false;
+			enabled = false;
 		}
 		ApplySettings();
 	}
@@ -426,7 +426,7 @@
 		Initialize();
 		int num = m_width + 1;
 		int num2 = num * num;
-		Vector3 position = base.transform.position;
+		Vector3 position = transform.position;
 		if (m_buildData == null || m_buildData.m_baseHeights.Count != num2 || m_buildData.m_center != position || m_buildData.m_scale != m_scale || m_buildData.m_worldGen != WorldGenerator.instance)
 		{
 			m_buildData = HeightmapBuilder.instance.RequestTerrainSync(position, m_width, m_scale, m_isDistantLod, WorldGenerator.instance);
@@ -543,7 +543,7 @@
 				ApplyModifier(item, array, array2);
 			}
 		}
-		TerrainComp terrainComp = (m_isDistantLod ? null : TerrainComp.FindTerrainCompiler(base.transform.position));
+		TerrainComp terrainComp = (m_isDistantLod ? null : TerrainComp.FindTerrainCompiler(transform.position));
 		if ((bool)terrainComp)
 		{
 			if (array == null)
@@ -576,7 +576,7 @@
 	{
 		Vector3 position = modifier.transform.position;
 		float num = modifier.GetRadius() + 0.1f;
-		Vector3 position2 = base.transform.position;
+		Vector3 position2 = transform.position;
 		float num2 = (float)m_width * m_scale * 0.5f;
 		if (position.x + num > position2.x + num2)
 		{
@@ -601,7 +601,7 @@
 	{
 		Vector3 position = modifier.transform.position;
 		float num = modifier.GetRadius() + 4f;
-		Vector3 position2 = base.transform.position;
+		Vector3 position2 = transform.position;
 		float num2 = (float)m_width * m_scale * 0.5f;
 		if (position.x + num < position2.x - num2)
 		{
@@ -725,7 +725,7 @@
 			m_collider.sharedMesh = m_collisionMesh;
 		}
 		float num5 = (float)m_width * m_scale * 0.5f;
-		m_bounds.SetMinMax(base.transform.position + new Vector3(0f - num5, num3, 0f - num5), base.transform.position + new Vector3(num5, num2, num5));
+		m_bounds.SetMinMax(transform.position + new Vector3(0f - num5, num3, 0f - num5), transform.position + new Vector3(num5, num2, num5));
 		m_boundingSphere.position = m_bounds.center;
 		m_boundingSphere.radius = Vector3.Distance(m_boundingSphere.position, m_bounds.max);
 	}
@@ -739,7 +739,7 @@
 		}
 		WorldGenerator instance = WorldGenerator.instance;
 		int num = m_width + 1;
-		Vector3 vector = base.transform.position + new Vector3((float)((double)m_width * (double)m_scale * -0.5), 0f, (float)((double)m_width * (double)m_scale * -0.5));
+		Vector3 vector = transform.position + new Vector3((float)((double)m_width * (double)m_scale * -0.5), 0f, (float)((double)m_width * (double)m_scale * -0.5));
 		s_tempVertices.Clear();
 		s_tempUVs.Clear();
 		s_tempIndices.Clear();
@@ -780,7 +780,7 @@
 	private void SmoothTerrain2(Vector3 worldPos, float radius, bool square, float[] levelOnlyHeights, float power, bool playerModifiction)
 	{
 		WorldToVertex(worldPos, out var x, out var y);
-		float b = (float)(double)(worldPos.y - base.transform.position.y);
+		float b = (float)(double)(worldPos.y - transform.position.y);
 		float num = (float)(double)(radius / m_scale);
 		int num2 = Mathf.CeilToInt(num);
 		Vector2 a = new Vector2(x, y);
@@ -828,7 +828,7 @@
 			height = 0f;
 			return false;
 		}
-		height = (float)((double)m_buildData.m_baseHeights[y * num + x] + (double)base.transform.position.y);
+		height = (float)((double)m_buildData.m_baseHeights[y * num + x] + (double)transform.position.y);
 		return true;
 	}
 
@@ -841,7 +841,7 @@
 			height = 0f;
 			return false;
 		}
-		height = (float)((double)m_heights[y * num + x] + (double)base.transform.position.y);
+		height = (float)((double)m_heights[y * num + x] + (double)transform.position.y);
 		return true;
 	}
 
@@ -870,7 +870,7 @@
 	{
 		worldPos.x -= 0.5f;
 		worldPos.z -= 0.5f;
-		float num = worldPos.y - base.transform.position.y;
+		float num = worldPos.y - transform.position.y;
 		WorldToVertexMask(worldPos, out var x, out var y);
 		float num2 = radius / m_scale;
 		int num3 = Mathf.CeilToInt(num2);
@@ -1002,7 +1002,7 @@
 
 	public void WorldToVertex(Vector3 worldPos, out int x, out int y)
 	{
-		Vector3 vector = worldPos - base.transform.position;
+		Vector3 vector = worldPos - transform.position;
 		int num = m_width / 2;
 		x = Mathf.FloorToInt(vector.x / m_scale + 0.5f) + num;
 		y = Mathf.FloorToInt(vector.z / m_scale + 0.5f) + num;
@@ -1010,7 +1010,7 @@
 
 	public void WorldToVertexMask(Vector3 worldPos, out int x, out int y)
 	{
-		Vector3 vector = worldPos - base.transform.position;
+		Vector3 vector = worldPos - transform.position;
 		int num = (m_width + 1) / 2;
 		x = Mathf.FloorToInt(vector.x / m_scale + 0.5f + (float)num);
 		y = Mathf.FloorToInt(vector.z / m_scale + 0.5f + (float)num);
@@ -1021,13 +1021,13 @@
 		int num = m_width / 2;
 		float x2 = ((float)(x - num) - 0.5f) * m_scale;
 		float z = ((float)(y - num) - 0.5f) * m_scale;
-		return new Vector3(x2, 0f, z) + base.transform.position;
+		return new Vector3(x2, 0f, z) + transform.position;
 	}
 
 	private void WorldToNormalizedHM(Vector3 worldPos, out float x, out float y)
 	{
 		float num = (float)m_width * m_scale;
-		Vector3 vector = worldPos - base.transform.position;
+		Vector3 vector = worldPos - transform.position;
 		x = vector.x / num + 0.5f;
 		y = vector.z / num + 0.5f;
 	}
@@ -1035,7 +1035,7 @@
 	private void LevelTerrain(Vector3 worldPos, float radius, bool square, float[] baseHeights, float[] levelOnly, bool playerModifiction)
 	{
 		WorldToVertexMask(worldPos, out var x, out var y);
-		Vector3 vector = worldPos - base.transform.position;
+		Vector3 vector = worldPos - transform.position;
 		float num = (float)((double)radius / (double)m_scale);
 		int num2 = Mathf.CeilToInt(num);
 		int num3 = m_width + 1;
@@ -1108,7 +1108,7 @@
 	public bool IsPointInside(Vector3 point, float radius = 0f)
 	{
 		float num = (float)((double)m_width * (double)m_scale * 0.5);
-		Vector3 position = base.transform.position;
+		Vector3 position = transform.position;
 		if ((float)((double)point.x + (double)radius) >= (float)((double)position.x - (double)num) && (float)((double)point.x - (double)radius) <= (float)((double)position.x + (double)num) && (float)((double)point.z + (double)radius) >= (float)((double)position.z - (double)num) && (float)((double)point.z - (double)radius) <= (float)((double)position.z + (double)num))
 		{
 			return true;
@@ -1355,12 +1355,12 @@
 
 	public TerrainComp GetAndCreateTerrainCompiler()
 	{
-		TerrainComp terrainComp = TerrainComp.FindTerrainCompiler(base.transform.position);
+		TerrainComp terrainComp = TerrainComp.FindTerrainCompiler(transform.position);
 		if ((bool)terrainComp)
 		{
 			return terrainComp;
 		}
-		return UnityEngine.Object.Instantiate(m_terrainCompilerPrefab, base.transform.position, Quaternion.identity).GetComponent<TerrainComp>();
+		return UnityEngine.Object.Instantiate(m_terrainCompilerPrefab, transform.position, Quaternion.identity).GetComponent<TerrainComp>();
 	}
 
 	public static string BiomeToString(Biome biome)
```

# `TerrainOp.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+8/-8` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/TerrainOp.cs
+++ b/TerrainOp.cs
@@ -122,7 +122,7 @@
 			return;
 		}
 		List<Heightmap> list = new List<Heightmap>();
-		Heightmap.FindHeightmap(base.transform.position, GetRadius(), list);
+		Heightmap.FindHeightmap(transform.position, GetRadius(), list);
 		foreach (Heightmap item in list)
 		{
 			item.GetAndCreateTerrainCompiler().ApplyOperation(this);
@@ -132,7 +132,7 @@
 			ZLog.Log($"Painting on {list.Count} heightmaps");
 		}
 		OnPlaced();
-		UnityEngine.Object.Destroy(base.gameObject);
+		UnityEngine.Object.Destroy(gameObject);
 	}
 
 	public float GetRadius()
@@ -142,19 +142,19 @@
 
 	private void OnPlaced()
 	{
-		m_onPlacedEffect.Create(base.transform.position, Quaternion.identity);
-		if ((bool)m_spawnOnPlaced && (m_spawnAtMaxLevelDepth || !Heightmap.AtMaxLevelDepth(base.transform.position + Vector3.up * m_settings.m_levelOffset)) && UnityEngine.Random.value <= m_chanceToSpawn)
+		m_onPlacedEffect.Create(transform.position, Quaternion.identity);
+		if ((bool)m_spawnOnPlaced && (m_spawnAtMaxLevelDepth || !Heightmap.AtMaxLevelDepth(transform.position + Vector3.up * m_settings.m_levelOffset)) && UnityEngine.Random.value <= m_chanceToSpawn)
 		{
 			Vector3 vector = UnityEngine.Random.insideUnitCircle * 0.2f;
-			GameObject obj = UnityEngine.Object.Instantiate(m_spawnOnPlaced, base.transform.position + Vector3.up * 0.5f + vector, Quaternion.identity);
-			obj.GetComponent<ItemDrop>().m_itemData.m_stack = UnityEngine.Random.Range(1, m_maxSpawned + 1);
-			obj.GetComponent<Rigidbody>().linearVelocity = Vector3.up * 4f;
+			GameObject gameObject = UnityEngine.Object.Instantiate(m_spawnOnPlaced, transform.position + Vector3.up * 0.5f + vector, Quaternion.identity);
+			gameObject.GetComponent<ItemDrop>().m_itemData.m_stack = UnityEngine.Random.Range(1, m_maxSpawned + 1);
+			gameObject.GetComponent<Rigidbody>().linearVelocity = Vector3.up * 4f;
 		}
 	}
 
 	private void OnDrawGizmosSelected()
 	{
-		Gizmos.matrix = Matrix4x4.TRS(base.transform.position + Vector3.up * m_settings.m_levelOffset, Quaternion.identity, new Vector3(1f, 0f, 1f));
+		Gizmos.matrix = Matrix4x4.TRS(transform.position + Vector3.up * m_settings.m_levelOffset, Quaternion.identity, new Vector3(1f, 0f, 1f));
 		if (m_settings.m_level)
 		{
 			Gizmos.color = Color.green;
```

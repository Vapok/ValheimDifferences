# `TerrainModifier.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+10/-10` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/TerrainModifier.cs
+++ b/TerrainModifier.cs
@@ -80,8 +80,8 @@
 		s_instances.Add(this);
 		s_needsSorting = true;
 		m_nview = GetComponent<ZNetView>();
-		m_wasEnabled = base.enabled;
-		if (base.enabled)
+		m_wasEnabled = enabled;
+		if (enabled)
 		{
 			if (m_triggerOnPlaced)
 			{
@@ -119,7 +119,7 @@
 		}
 		if ((bool)ClutterSystem.instance)
 		{
-			ClutterSystem.instance.ResetGrass(base.transform.position, GetRadius());
+			ClutterSystem.instance.ResetGrass(transform.position, GetRadius());
 		}
 	}
 
@@ -148,14 +148,14 @@
 
 	private void OnPlaced()
 	{
-		RemoveOthers(base.transform.position, GetRadius() / 4f);
-		m_onPlacedEffect.Create(base.transform.position, Quaternion.identity);
-		if ((bool)m_spawnOnPlaced && (m_spawnAtMaxLevelDepth || !Heightmap.AtMaxLevelDepth(base.transform.position + Vector3.up * m_levelOffset)) && Random.value <= m_chanceToSpawn)
+		RemoveOthers(transform.position, GetRadius() / 4f);
+		m_onPlacedEffect.Create(transform.position, Quaternion.identity);
+		if ((bool)m_spawnOnPlaced && (m_spawnAtMaxLevelDepth || !Heightmap.AtMaxLevelDepth(transform.position + Vector3.up * m_levelOffset)) && Random.value <= m_chanceToSpawn)
 		{
 			Vector3 vector = Random.insideUnitCircle * 0.2f;
-			GameObject obj = Object.Instantiate(m_spawnOnPlaced, base.transform.position + Vector3.up * 0.5f + vector, Quaternion.identity);
-			obj.GetComponent<ItemDrop>().m_itemData.m_stack = Random.Range(1, m_maxSpawned + 1);
-			obj.GetComponent<Rigidbody>().linearVelocity = Vector3.up * 4f;
+			GameObject gameObject = Object.Instantiate(m_spawnOnPlaced, transform.position + Vector3.up * 0.5f + vector, Quaternion.identity);
+			gameObject.GetComponent<ItemDrop>().m_itemData.m_stack = Random.Range(1, m_maxSpawned + 1);
+			gameObject.GetComponent<Rigidbody>().linearVelocity = Vector3.up * 4f;
 		}
 	}
 
@@ -238,7 +238,7 @@
 
 	private void OnDrawGizmosSelected()
 	{
-		Gizmos.matrix = Matrix4x4.TRS(base.transform.position + Vector3.up * m_levelOffset, Quaternion.identity, new Vector3(1f, 0f, 1f));
+		Gizmos.matrix = Matrix4x4.TRS(transform.position + Vector3.up * m_levelOffset, Quaternion.identity, new Vector3(1f, 0f, 1f));
 		if (m_level)
 		{
 			Gizmos.color = Color.green;
```

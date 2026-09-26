# `SpawnPrefab.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SpawnPrefab.cs
+++ b/SpawnPrefab.cs
@@ -11,7 +11,7 @@
 		m_nview = GetComponentInParent<ZNetView>();
 		if (m_nview == null)
 		{
-			ZLog.LogWarning("SpawnerPrefab cant find netview " + base.gameObject.name);
+			ZLog.LogWarning("SpawnerPrefab cant find netview " + gameObject.name);
 		}
 		else
 		{
@@ -23,11 +23,11 @@
 	{
 		if (m_nview.IsValid() && m_nview.IsOwner())
 		{
-			string text = "HasSpawned_" + base.gameObject.name;
+			string text = "HasSpawned_" + gameObject.name;
 			if (!m_nview.GetZDO().GetBool(text))
 			{
-				ZLog.Log("SpawnPrefab " + base.gameObject.name + " SPAWNING " + m_prefab.name);
-				Object.Instantiate(m_prefab, base.transform.position, base.transform.rotation);
+				ZLog.Log("SpawnPrefab " + gameObject.name + " SPAWNING " + m_prefab.name);
+				Object.Instantiate(m_prefab, transform.position, transform.rotation);
 				m_nview.GetZDO().Set(text, value: true);
 			}
 			CancelInvoke("TrySpawn");
```

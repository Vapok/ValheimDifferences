# `SoftReferencePrefabSpawner.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `SpawnPrefab() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/SoftReferencePrefabSpawner.cs
+++ b/SoftReferencePrefabSpawner.cs
@@ -45,6 +45,6 @@
 
 	private void SpawnPrefab()
 	{
-		SoftReferenceableAssets.Utils.Instantiate(m_prefab, transform.parent).name = m_prefab.Name;
+		m_prefab.Instantiate(transform.parent).name = m_prefab.name;
 	}
 }
```

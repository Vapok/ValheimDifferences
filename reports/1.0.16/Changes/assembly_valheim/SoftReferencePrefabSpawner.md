# `SoftReferencePrefabSpawner.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SoftReferencePrefabSpawner.cs
+++ b/SoftReferencePrefabSpawner.cs
@@ -16,7 +16,7 @@
 		if (m_spawnAsynchronously)
 		{
 			m_currentlyLoading = true;
-			m_prefab.LoadAsync(delegate(AssetID assetID, LoadResult result)
+			m_prefab.LoadAsync((AssetID assetID, LoadResult result) =>
 			{
 				m_currentlyLoading = false;
 				if (result == LoadResult.Succeeded)
@@ -24,13 +24,13 @@
 					SpawnPrefab();
 				}
 				m_prefab.Release();
-				Object.Destroy(base.gameObject);
+				Object.Destroy(gameObject);
 			});
 		}
 		else
 		{
 			SpawnPrefab();
-			Object.Destroy(base.gameObject);
+			Object.Destroy(gameObject);
 		}
 	}
 
@@ -45,6 +45,6 @@
 
 	private void SpawnPrefab()
 	{
-		SoftReferenceableAssets.Utils.Instantiate(m_prefab, base.transform.parent).name = m_prefab.Name;
+		SoftReferenceableAssets.Utils.Instantiate(m_prefab, transform.parent).name = m_prefab.Name;
 	}
 }
```

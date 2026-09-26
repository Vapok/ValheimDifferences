# `SpawnOnDamaged.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SpawnOnDamaged.cs
+++ b/SpawnOnDamaged.cs
@@ -23,7 +23,7 @@
 	{
 		if ((bool)m_spawnOnDamage)
 		{
-			UnityEngine.Object.Instantiate(m_spawnOnDamage, base.transform.position, Quaternion.identity);
+			UnityEngine.Object.Instantiate(m_spawnOnDamage, transform.position, Quaternion.identity);
 		}
 	}
 }
```

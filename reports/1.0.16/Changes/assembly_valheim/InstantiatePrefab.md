# `InstantiatePrefab.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/InstantiatePrefab.cs
+++ b/InstantiatePrefab.cs
@@ -12,7 +12,7 @@
 	{
 		if (m_attach)
 		{
-			Object.Instantiate(m_prefab, base.transform).transform.SetAsFirstSibling();
+			Object.Instantiate(m_prefab, transform).transform.SetAsFirstSibling();
 		}
 		else
 		{
```

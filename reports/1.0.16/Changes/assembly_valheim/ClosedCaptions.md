# `ClosedCaptions.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ClosedCaptions.cs
+++ b/ClosedCaptions.cs
@@ -64,7 +64,7 @@
 		{
 			m_instance = this;
 			Valid = true;
-			foreach (Transform item in base.transform)
+			foreach (Transform item in transform)
 			{
 				Object.Destroy(item.gameObject);
 			}
```

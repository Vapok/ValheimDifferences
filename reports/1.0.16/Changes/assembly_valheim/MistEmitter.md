# `MistEmitter.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MistEmitter.cs
+++ b/MistEmitter.cs
@@ -39,7 +39,7 @@
 
 	private void PlaceOne()
 	{
-		if (!GetRandomPoint(base.transform.position, m_totalRadius, out var p))
+		if (!GetRandomPoint(transform.position, m_totalRadius, out var p))
 		{
 			return;
 		}
```

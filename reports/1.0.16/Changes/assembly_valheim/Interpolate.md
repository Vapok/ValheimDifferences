# `Interpolate.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+9/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Interpolate.cs
+++ b/Interpolate.cs
@@ -250,7 +250,15 @@
 			{
 				current = 0;
 			}
-			int previous = ((current != 0) ? (current - 1) : (loop ? last : current));
+			int previous;
+			if (current != 0)
+			{
+				previous = current - 1;
+			}
+			else
+			{
+				previous = (loop ? last : current);
+			}
 			int start = current;
 			int end = ((current != last) ? (current + 1) : ((!loop) ? current : 0));
 			int next = ((end != last) ? (end + 1) : ((!loop) ? end : 0));
```

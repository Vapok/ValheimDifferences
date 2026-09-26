# `Utils.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Utils.cs
+++ b/Utils.cs
@@ -1159,11 +1159,11 @@
 			return (false, Vector2s.zero);
 		}
 		Vector2s item = new Vector2s((short)v.x, (short)v.z);
-		bool num = ((float)item.x).Equals(v.x);
-		bool flag = ((float)item.y).Equals(v.z);
-		if (num)
-		{
-			if (flag)
+		bool flag = ((float)item.x).Equals(v.x);
+		bool flag2 = ((float)item.y).Equals(v.z);
+		if (flag)
+		{
+			if (flag2)
 			{
 				return (true, item);
 			}
@@ -1178,7 +1178,7 @@
 				return (true, item);
 			}
 		}
-		if (flag)
+		if (flag2)
 		{
 			if (v.x < -20000f)
 			{
```

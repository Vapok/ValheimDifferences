# `NetworkingUtils/IPv4Address.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/NetworkingUtils/IPv4Address.cs
+++ b/NetworkingUtils/IPv4Address.cs
@@ -116,12 +116,12 @@
 			int num2 = ((i < 3) ? stringRepresentation.IndexOf('.') : stringRepresentation.Length);
 			if (num2 < 0)
 			{
-				result = default(IPv4Address);
+				result = default;
 				return false;
 			}
 			if (!byte.TryParse(stringRepresentation.Slice(0, num2), out var result2))
 			{
-				result = default(IPv4Address);
+				result = default;
 				return false;
 			}
 			num <<= 8;
```

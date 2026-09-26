# `NetworkingUtils/IPv6Address.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/NetworkingUtils/IPv6Address.cs
+++ b/NetworkingUtils/IPv6Address.cs
@@ -178,14 +178,14 @@
 			{
 				if (stringRepresentation[num] != ':')
 				{
-					result = default(IPv6Address);
+					result = default;
 					return false;
 				}
 				flag = false;
 				num++;
 				if (num >= stringRepresentation.Length)
 				{
-					result = default(IPv6Address);
+					result = default;
 					return false;
 				}
 			}
@@ -195,14 +195,14 @@
 				{
 					if (stringRepresentation.Length <= num + 1 || stringRepresentation[num + 1] != ':')
 					{
-						result = default(IPv6Address);
+						result = default;
 						return false;
 					}
 					num++;
 				}
 				else if (b >= 0)
 				{
-					result = default(IPv6Address);
+					result = default;
 					return false;
 				}
 				num++;
@@ -218,7 +218,7 @@
 					{
 						if (b < 0)
 						{
-							result = default(IPv6Address);
+							result = default;
 							return false;
 						}
 						num3 = stringRepresentation.Length;
@@ -233,13 +233,13 @@
 					num3 = stringRepresentation.Length;
 					if (num3 - num <= 0)
 					{
-						result = default(IPv6Address);
+						result = default;
 						return false;
 					}
 				}
 				if (!ushort.TryParse(stringRepresentation.Slice(num, num3 - num), NumberStyles.HexNumber, CultureInfo.InvariantCulture, out var result3))
 				{
-					result = default(IPv6Address);
+					result = default;
 					return false;
 				}
 				span[b2] = result3;
```

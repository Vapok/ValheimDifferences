# `StringExtensionMethods.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/StringExtensionMethods.cs
+++ b/StringExtensionMethods.cs
@@ -63,7 +63,7 @@
 	{
 		int num = 5381;
 		int num2 = num;
-		for (int i = 0; i < str.Length && str[i] != 0; i += 2)
+		for (int i = 0; i < str.Length && str[i] != '\0'; i += 2)
 		{
 			num = ((num << 5) + num) ^ str[i];
 			if (i == str.Length - 1 || str[i + 1] == '\0')
```

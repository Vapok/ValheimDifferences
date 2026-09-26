# `FileReader.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/FileReader.cs
+++ b/FileReader.cs
@@ -36,9 +36,9 @@
 					FileHelpers.Unmount();
 					throw new FileNotFoundException();
 				}
-				bool num = FileHelpers.CloudStorage.ReadFile(path, out var data);
+				bool flag = FileHelpers.CloudStorage.ReadFile(path, out var data);
 				FileHelpers.Unmount();
-				if (!num)
+				if (!flag)
 				{
 					throw new Exception("Connected Storage file missing");
 				}
```

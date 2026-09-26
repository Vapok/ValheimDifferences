# `UnityEngine.PostProcessing/DitheringModel.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/DitheringModel.cs
+++ b/UnityEngine.PostProcessing/DitheringModel.cs
@@ -10,7 +10,7 @@
 	[StructLayout(LayoutKind.Sequential, Size = 1)]
 	public struct Settings
 	{
-		public static Settings defaultSettings => default(Settings);
+		public static Settings defaultSettings => default;
 	}
 
 	[SerializeField]
```

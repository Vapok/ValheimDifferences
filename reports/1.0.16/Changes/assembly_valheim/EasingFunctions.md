# `Valheim.UI/EasingFunctions.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/EasingFunctions.cs
+++ b/Valheim.UI/EasingFunctions.cs
@@ -15,7 +15,7 @@
 	{
 		return type switch
 		{
-			EasingType.Linear => null, 
+			EasingType.Linear => (Func<float, float>)null, 
 			EasingType.SineIn => SineIn, 
 			EasingType.SineOut => SineOut, 
 			EasingType.SineInOut => SineInOut, 
```

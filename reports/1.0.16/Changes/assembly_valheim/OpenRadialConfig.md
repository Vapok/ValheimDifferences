# `OpenRadialConfig.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/OpenRadialConfig.cs
+++ b/OpenRadialConfig.cs
@@ -13,7 +13,7 @@
 
 	public void InitRadialConfig(RadialBase radial)
 	{
-		radial.OnInteractionDelay = delegate(float delay)
+		radial.OnInteractionDelay = (float delay) =>
 		{
 			PlayerController.SetTakeInputDelay(delay);
 		};
```

# `UnityStandardAssets.ImageEffects/Twirl.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/Twirl.cs
+++ b/UnityStandardAssets.ImageEffects/Twirl.cs
@@ -15,6 +15,6 @@
 
 	private void OnRenderImage(RenderTexture source, RenderTexture destination)
 	{
-		ImageEffects.RenderDistortion(base.material, source, destination, angle, center, radius);
+		ImageEffects.RenderDistortion(material, source, destination, angle, center, radius);
 	}
 }
```

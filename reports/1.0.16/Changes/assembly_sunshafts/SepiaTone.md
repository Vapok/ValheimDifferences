# `UnityStandardAssets.ImageEffects/SepiaTone.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/SepiaTone.cs
+++ b/UnityStandardAssets.ImageEffects/SepiaTone.cs
@@ -8,6 +8,6 @@
 {
 	private void OnRenderImage(RenderTexture source, RenderTexture destination)
 	{
-		Graphics.Blit(source, destination, base.material);
+		Graphics.Blit(source, destination, material);
 	}
 }
```

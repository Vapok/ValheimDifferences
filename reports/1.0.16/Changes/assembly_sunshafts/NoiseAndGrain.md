# `UnityStandardAssets.ImageEffects/NoiseAndGrain.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/NoiseAndGrain.cs
+++ b/UnityStandardAssets.ImageEffects/NoiseAndGrain.cs
@@ -65,7 +65,7 @@
 			Graphics.Blit(source, destination);
 			if (null == noiseTexture)
 			{
-				Debug.LogWarning("Noise & Grain effect failing as noise texture is not assigned. please assign.", base.transform);
+				Debug.LogWarning("Noise & Grain effect failing as noise texture is not assigned. please assign.", transform);
 			}
 			return;
 		}
```

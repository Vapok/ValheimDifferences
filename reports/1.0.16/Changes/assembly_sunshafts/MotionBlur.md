# `UnityStandardAssets.ImageEffects/MotionBlur.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/MotionBlur.cs
+++ b/UnityStandardAssets.ImageEffects/MotionBlur.cs
@@ -43,10 +43,10 @@
 			RenderTexture.ReleaseTemporary(temporary);
 		}
 		blurAmount = Mathf.Clamp(blurAmount, 0f, 0.92f);
-		base.material.SetTexture("_MainTex", accumTexture);
-		base.material.SetFloat("_AccumOrig", 1f - blurAmount);
+		material.SetTexture("_MainTex", accumTexture);
+		material.SetFloat("_AccumOrig", 1f - blurAmount);
 		accumTexture.MarkRestoreExpected();
-		Graphics.Blit(source, accumTexture, base.material);
+		Graphics.Blit(source, accumTexture, material);
 		Graphics.Blit(accumTexture, destination);
 	}
 }
```

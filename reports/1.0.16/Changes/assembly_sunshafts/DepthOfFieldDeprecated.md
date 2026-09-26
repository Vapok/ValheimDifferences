# `UnityStandardAssets.ImageEffects/DepthOfFieldDeprecated.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/DepthOfFieldDeprecated.cs
+++ b/UnityStandardAssets.ImageEffects/DepthOfFieldDeprecated.cs
@@ -84,7 +84,7 @@
 
 	private float widthOverHeight = 1.25f;
 
-	private float oneOverBaseSize = 0.001953125f;
+	private float oneOverBaseSize = 2f / 1024f;
 
 	public bool bokeh;
 
@@ -231,7 +231,7 @@
 			flag = flag && focalPoint > _camera.nearClipPlane + Mathf.Epsilon;
 		}
 		widthOverHeight = 1f * (float)source.width / (1f * (float)source.height);
-		oneOverBaseSize = 0.001953125f;
+		oneOverBaseSize = 2f / 1024f;
 		dofMaterial.SetFloat("_ForegroundBlurExtrude", foregroundBlurExtrude);
 		dofMaterial.SetVector("_CurveParams", new Vector4(simpleTweakMode ? (1f / focalStartCurve) : focalStartCurve, simpleTweakMode ? (1f / focalEndCurve) : focalEndCurve, num2 * 0.5f, focalDistance01));
 		dofMaterial.SetVector("_InvRenderTargetSize", new Vector4(1f / (1f * (float)source.width), 1f / (1f * (float)source.height), 0f, 0f));
```

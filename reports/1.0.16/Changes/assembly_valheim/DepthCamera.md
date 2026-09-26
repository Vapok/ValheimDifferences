# `DepthCamera.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/DepthCamera.cs
+++ b/DepthCamera.cs
@@ -27,13 +27,13 @@
 			position.x = Mathf.Round(position.x);
 			position.y = Mathf.Round(position.y);
 			position.z = Mathf.Round(position.z);
-			base.transform.position = position;
+			transform.position = position;
 			float lodBias = QualitySettings.lodBias;
 			QualitySettings.lodBias = 10f;
 			m_camera.RenderWithShader(m_depthShader, "RenderType");
 			QualitySettings.lodBias = lodBias;
 			Shader.SetGlobalTexture("_SkyAlphaTexture", m_texture);
-			Shader.SetGlobalVector("_SkyAlphaPosition", base.transform.position);
+			Shader.SetGlobalVector("_SkyAlphaPosition", transform.position);
 		}
 	}
 }
```

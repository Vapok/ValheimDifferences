# `UnityStandardAssets.ImageEffects/ScreenSpaceAmbientOcclusion.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/ScreenSpaceAmbientOcclusion.cs
+++ b/UnityStandardAssets.ImageEffects/ScreenSpaceAmbientOcclusion.cs
@@ -74,14 +74,14 @@
 		if (!SystemInfo.supportsImageEffects || !SystemInfo.SupportsRenderTextureFormat(RenderTextureFormat.Depth))
 		{
 			m_Supported = false;
-			base.enabled = false;
+			enabled = false;
 			return;
 		}
 		CreateMaterials();
 		if (!m_SSAOMaterial || m_SSAOMaterial.passCount != 5)
 		{
 			m_Supported = false;
-			base.enabled = false;
+			enabled = false;
 		}
 		else
 		{
@@ -108,7 +108,7 @@
 	{
 		if (!m_Supported || !m_SSAOShader.isSupported)
 		{
-			base.enabled = false;
+			enabled = false;
 			return;
 		}
 		CreateMaterials();
@@ -138,9 +138,9 @@
 		}
 		m_SSAOMaterial.SetVector("_NoiseScale", new Vector3((float)renderTexture.width / (float)num2, (float)renderTexture.height / (float)num3, 0f));
 		m_SSAOMaterial.SetVector("_Params", new Vector4(m_Radius, m_MinZ, 1f / m_OcclusionAttenuation, m_OcclusionIntensity));
-		bool num4 = m_Blur > 0;
-		Graphics.Blit(num4 ? null : source, renderTexture, m_SSAOMaterial, (int)m_SampleCount);
-		if (num4)
+		bool flag = m_Blur > 0;
+		Graphics.Blit(flag ? null : source, renderTexture, m_SSAOMaterial, (int)m_SampleCount);
+		if (flag)
 		{
 			RenderTexture temporary = RenderTexture.GetTemporary(source.width, source.height, 0);
 			m_SSAOMaterial.SetVector("_TexelOffsetScale", new Vector4((float)m_Blur / (float)source.width, 0f, 0f, 0f));
```

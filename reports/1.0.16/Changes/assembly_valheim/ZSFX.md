# `ZSFX.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+12/-12` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZSFX.cs
+++ b/ZSFX.cs
@@ -266,23 +266,23 @@
 		Camera mainCamera = Utils.GetMainCamera();
 		if (m_distanceReverb && m_audioSource.spatialBlend != 0f && mainCamera != null)
 		{
-			float num = Vector3.Distance(mainCamera.transform.position, base.transform.position);
-			bool num2 = Mister.InsideMister(base.transform.position);
-			float num3 = (m_useCustomReverbDistance ? m_customReverbDistance : 64f);
-			float num4 = Mathf.Clamp01(num / num3);
-			float b = Mathf.Clamp01(m_audioSource.maxDistance / num3) * Mathf.Clamp01(num / m_audioSource.maxDistance);
-			float num5 = Mathf.Max(num4, b);
-			if (num2)
-			{
-				num5 = Mathf.Lerp(num5, 0f, num4);
-				m_reverbPitchModifier = 0.5f * num4;
+			float num = Vector3.Distance(mainCamera.transform.position, transform.position);
+			bool flag = Mister.InsideMister(transform.position);
+			float num2 = (m_useCustomReverbDistance ? m_customReverbDistance : 64f);
+			float num3 = Mathf.Clamp01(num / num2);
+			float b = Mathf.Clamp01(m_audioSource.maxDistance / num2) * Mathf.Clamp01(num / m_audioSource.maxDistance);
+			float num4 = Mathf.Max(num3, b);
+			if (flag)
+			{
+				num4 = Mathf.Lerp(num4, 0f, num3);
+				m_reverbPitchModifier = 0.5f * num3;
 			}
 			m_audioSource.bypassReverbZones = false;
-			m_audioSource.reverbZoneMix = num5;
+			m_audioSource.reverbZoneMix = num4;
 			if (m_baseSpread < 120f)
 			{
 				float a = Mathf.Max(m_baseSpread, 45f);
-				m_audioSource.spread = Mathf.Lerp(a, 120f, num5);
+				m_audioSource.spread = Mathf.Lerp(a, 120f, num4);
 			}
 		}
 		else
```

# `LightFlicker.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/LightFlicker.cs
+++ b/LightFlicker.cs
@@ -64,7 +64,7 @@
 	{
 		m_light = GetComponent<Light>();
 		m_baseIntensity = m_light.intensity;
-		m_basePosition = base.transform.localPosition;
+		m_basePosition = transform.localPosition;
 		m_flickerOffset = UnityEngine.Random.Range(0f, 10f);
 		if (Settings.ReduceFlashingLights)
 		{
@@ -77,7 +77,7 @@
 
 	private void ApplySettings()
 	{
-		if (!base.enabled)
+		if (!enabled)
 		{
 			return;
 		}
@@ -150,7 +150,7 @@
 			{
 				if (m_time > m_ttl)
 				{
-					UnityEngine.Object.Destroy(base.gameObject);
+					UnityEngine.Object.Destroy(gameObject);
 					return;
 				}
 				float l = m_ttl - m_fadeDuration;
@@ -170,7 +170,7 @@
 			m_offset.y = MathF.Sin(num * 0.56436f) * MathF.Sin(num * 0.688742f);
 			m_offset.z = MathF.Cos(num * 0.758348f) * MathF.Cos(num * 0.4563696f);
 			m_offset *= m_movement;
-			base.transform.localPosition = m_basePosition + m_offset;
+			transform.localPosition = m_basePosition + m_offset;
 		}
 	}
 }
```

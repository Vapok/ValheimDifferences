# `EffectFade.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/EffectFade.cs
+++ b/EffectFade.cs
@@ -20,9 +20,9 @@
 
 	private void Awake()
 	{
-		m_particles = base.gameObject.GetComponentsInChildren<ParticleSystem>();
-		m_light = base.gameObject.GetComponentInChildren<Light>();
-		m_audioSource = base.gameObject.GetComponentInChildren<AudioSource>();
+		m_particles = gameObject.GetComponentsInChildren<ParticleSystem>();
+		m_light = gameObject.GetComponentInChildren<Light>();
+		m_audioSource = gameObject.GetComponentInChildren<AudioSource>();
 		if ((bool)m_light)
 		{
 			m_lightBaseIntensity = m_light.intensity;
```

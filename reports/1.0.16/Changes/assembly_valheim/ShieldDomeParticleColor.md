# `ShieldDomeParticleColor.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ShieldDomeParticleColor.cs
+++ b/ShieldDomeParticleColor.cs
@@ -16,7 +16,7 @@
 
 	private void Start()
 	{
-		Color domeColor = ShieldDomeImageEffect.GetDomeColor(ShieldGenerator.GetClosestShieldGenerator(base.transform.position, m_colorMode == ColorMode.ClosestShieldGenerator).GetFuelRatio());
+		Color domeColor = ShieldDomeImageEffect.GetDomeColor(ShieldGenerator.GetClosestShieldGenerator(transform.position, m_colorMode == ColorMode.ClosestShieldGenerator).GetFuelRatio());
 		ParticleSystem[] particleSystems = m_particleSystems;
 		foreach (ParticleSystem obj in particleSystems)
 		{
```

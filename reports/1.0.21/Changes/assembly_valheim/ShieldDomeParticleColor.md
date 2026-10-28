# `ShieldDomeParticleColor.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+10/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Start() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/ShieldDomeParticleColor.cs
+++ b/ShieldDomeParticleColor.cs
@@ -16,13 +16,17 @@
 
 	private void Start()
 	{
-		Color domeColor = ShieldDomeImageEffect.GetDomeColor(ShieldGenerator.GetClosestShieldGenerator(transform.position, m_colorMode == ColorMode.ClosestShieldGenerator).GetFuelRatio());
-		ParticleSystem[] particleSystems = m_particleSystems;
-		foreach (ParticleSystem obj in particleSystems)
+		ShieldGenerator closestShieldGenerator = ShieldGenerator.GetClosestShieldGenerator(transform.position, m_colorMode == ColorMode.ClosestShieldGenerator);
+		if ((object)closestShieldGenerator != null)
 		{
-			ParticleSystem.MainModule main = obj.main;
-			domeColor.a = obj.main.startColor.color.a;
-			main.startColor = domeColor;
+			Color domeColor = ShieldDomeImageEffect.GetDomeColor(closestShieldGenerator.GetFuelRatio());
+			ParticleSystem[] particleSystems = m_particleSystems;
+			foreach (ParticleSystem obj in particleSystems)
+			{
+				ParticleSystem.MainModule main = obj.main;
+				domeColor.a = obj.main.startColor.color.a;
+				main.startColor = domeColor;
+			}
 		}
 	}
 }
```

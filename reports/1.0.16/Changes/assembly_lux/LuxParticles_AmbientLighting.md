# `LuxParticles/LuxParticles_AmbientLighting.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_lux.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/LuxParticles/LuxParticles_AmbientLighting.cs
+++ b/LuxParticles/LuxParticles_AmbientLighting.cs
@@ -118,7 +118,7 @@
 		}
 		else
 		{
-			LightProbes.GetInterpolatedProbe(base.transform.position, null, out probe);
+			LightProbes.GetInterpolatedProbe(transform.position, null, out probe);
 		}
 		PremultiplyCoefficients(probe);
 		GetShaderConstantsFromNormalizedSH(ref probe, IsSkyLighting: true);
```

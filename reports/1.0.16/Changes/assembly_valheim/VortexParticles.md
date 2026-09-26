# `VortexParticles.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/VortexParticles.cs
+++ b/VortexParticles.cs
@@ -90,7 +90,7 @@
 		ps = GetComponent<ParticleSystem>();
 		if (ps == null)
 		{
-			ZLog.LogWarning("VortexParticles object '" + base.gameObject.name + "' is missing a particle system and disabled!");
+			ZLog.LogWarning("VortexParticles object '" + gameObject.name + "' is missing a particle system and disabled!");
 			effectOn = false;
 		}
 	}
@@ -104,8 +104,8 @@
 		}
 		else
 		{
-			job.vortexCenter = base.transform.position + centerOffset;
-			job.upDir = base.transform.up;
+			job.vortexCenter = transform.position + centerOffset;
+			job.upDir = transform.up;
 		}
 		job.pullStrength = pullStrength;
 		job.vortexStrength = vortexStrength;
@@ -122,7 +122,7 @@
 			ps = GetComponent<ParticleSystem>();
 			if (ps == null)
 			{
-				ZLog.LogWarning("VortexParticles object '" + base.gameObject.name + "' is missing a particle system and disabled!");
+				ZLog.LogWarning("VortexParticles object '" + gameObject.name + "' is missing a particle system and disabled!");
 				effectOn = false;
 			}
 		}
```

# `WrapParticles.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/WrapParticles.cs
+++ b/WrapParticles.cs
@@ -117,7 +117,7 @@
 		m_ps = GetComponent<ParticleSystem>();
 		if (m_ps == null)
 		{
-			ZLog.LogWarning("WrapParticles object '" + base.gameObject.name + "' is missing a particle system and disabled!");
+			ZLog.LogWarning("WrapParticles object '" + gameObject.name + "' is missing a particle system and disabled!");
 			m_effectOn = false;
 		}
 	}
@@ -125,7 +125,7 @@
 	private void Update()
 	{
 		job.isGlobal = m_ps.main.simulationSpace == ParticleSystemSimulationSpace.World;
-		job.globalCenter = base.transform.position;
+		job.globalCenter = transform.position;
 		job.wrapMode = m_wrapMode;
 		job.sphereRadius = m_wrapSphereRadius;
 		job.sphereRadiusSqr = m_wrapSphereRadius * m_wrapSphereRadius;
@@ -140,10 +140,10 @@
 		switch (m_wrapMode)
 		{
 		case WrapMode.Box:
-			Gizmos.DrawWireCube(base.transform.position + m_wrapCenterOffset, m_wrapBoxSize);
+			Gizmos.DrawWireCube(transform.position + m_wrapCenterOffset, m_wrapBoxSize);
 			break;
 		case WrapMode.Sphere:
-			Gizmos.DrawWireSphere(base.transform.position + m_wrapCenterOffset, m_wrapSphereRadius);
+			Gizmos.DrawWireSphere(transform.position + m_wrapCenterOffset, m_wrapSphereRadius);
 			break;
 		}
 	}
@@ -155,7 +155,7 @@
 			m_ps = GetComponent<ParticleSystem>();
 			if (m_ps == null)
 			{
-				ZLog.LogWarning("WrapParticles object '" + base.gameObject.name + "' is missing a particle system and disabled!");
+				ZLog.LogWarning("WrapParticles object '" + gameObject.name + "' is missing a particle system and disabled!");
 				m_effectOn = false;
 			}
 		}
```

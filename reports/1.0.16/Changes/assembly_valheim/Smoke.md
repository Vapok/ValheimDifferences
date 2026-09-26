# `Smoke.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Smoke.cs
+++ b/Smoke.cs
@@ -47,7 +47,7 @@
 			angularVelocity = 0f,
 			angularVelocity3D = Vector3.zero,
 			axisOfRotation = new Vector3(0f, 0f, 1f),
-			position = base.transform.position,
+			position = transform.position,
 			randomSeed = (uint)Random.Range(int.MinValue, int.MaxValue),
 			remainingLifetime = m_ttl + m_fadetime,
 			startLifetime = m_ttl,
@@ -67,7 +67,7 @@
 		{
 			m_renderParticle.remainingLifetime = m_fadetime - m_fadeTimer;
 		}
-		m_renderParticle.position = base.transform.position;
+		m_renderParticle.position = transform.position;
 		return m_renderParticle;
 	}
 
@@ -175,7 +175,7 @@
 			Mathf.Clamp01(m_fadeTimer / m_fadetime);
 			if (m_fadeTimer >= m_fadetime)
 			{
-				Object.Destroy(base.gameObject);
+				Object.Destroy(gameObject);
 			}
 		}
 	}
```

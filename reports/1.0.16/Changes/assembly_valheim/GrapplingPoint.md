# `GrapplingPoint.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+11/-11` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/GrapplingPoint.cs
+++ b/GrapplingPoint.cs
@@ -155,7 +155,7 @@
 			}
 			if ((bool)m_pullSound)
 			{
-				m_instanceSound = Object.Instantiate(m_pullSound, base.transform);
+				m_instanceSound = Object.Instantiate(m_pullSound, transform);
 			}
 		}
 		Transform leftHand;
@@ -168,7 +168,7 @@
 				goto IL_009b;
 			}
 		}
-		leftHand = base.transform;
+		leftHand = transform;
 		goto IL_009b;
 		IL_009b:
 		m_attachPoint = leftHand;
@@ -185,9 +185,9 @@
 			}
 			if (Method == GrapplingMethod.OneBoost)
 			{
-				m_launchDir = base.transform.position - character.transform.position;
+				m_launchDir = transform.position - character.transform.position;
 				m_launchDir.Normalize();
-				float num = Vector3.Distance(base.transform.position, m_character.transform.position);
+				float num = Vector3.Distance(transform.position, m_character.transform.position);
 				float num2 = m_pullForce + m_distanceForceMultiplier * num;
 				character.ForceJump(m_launchDir * num2);
 			}
@@ -225,11 +225,11 @@
 			return;
 		}
 		m_time += Time.deltaTime;
-		Vector3 vector = m_character.transform.position - base.transform.position;
+		Vector3 vector = m_character.transform.position - transform.position;
 		float magnitude = vector.magnitude;
 		if (m_secondary)
 		{
-			if (base.transform.position.y > m_character.transform.position.y && magnitude > m_repellingMinDistance)
+			if (transform.position.y > m_character.transform.position.y && magnitude > m_repellingMinDistance)
 			{
 				Vector3 normalized = vector.normalized;
 				float num = Vector3.Dot(Vector3.down, normalized);
@@ -293,14 +293,14 @@
 						Break(early: true);
 					}
 				}
-				if (Vector3.Dot(base.transform.position - m_character.transform.position, m_launchDir) < m_dotBreakValue)
+				if (Vector3.Dot(transform.position - m_character.transform.position, m_launchDir) < m_dotBreakValue)
 				{
 					Break(early: false);
 				}
 			}
 			if (Method == GrapplingMethod.ConstantVelocity)
 			{
-				Vector3 vector4 = base.transform.position - m_character.transform.position;
+				Vector3 vector4 = transform.position - m_character.transform.position;
 				if (magnitude > m_closePullDist)
 				{
 					m_character.SetVelocity(vector4.normalized * m_pullForce);
@@ -376,7 +376,7 @@
 	{
 		if ((object)m_attachPoint != null)
 		{
-			m_lineRenderer.SetPosition(0, base.transform.position + base.transform.rotation * m_attachOffsetProjectile);
+			m_lineRenderer.SetPosition(0, transform.position + transform.rotation * m_attachOffsetProjectile);
 			m_lineRenderer.SetPosition(1, m_attachPoint.position + m_attachPoint.rotation * m_attachOffsetHand);
 		}
 	}
@@ -416,7 +416,7 @@
 			}
 			if ((bool)m_spawnOnDone)
 			{
-				Object.Instantiate(m_spawnOnDone, base.transform.position, base.transform.rotation).GetComponent<GrapplingPoint>()?.Activate(m_character);
+				Object.Instantiate(m_spawnOnDone, transform.position, transform.rotation).GetComponent<GrapplingPoint>()?.Activate(m_character);
 			}
 			if (m_jumpOnDone != 0f)
 			{
@@ -427,7 +427,7 @@
 		{
 			m_lineRenderer.enabled = false;
 		}
-		ZNetScene.instance.Destroy(base.gameObject);
+		ZNetScene.instance.Destroy(gameObject);
 		GameCamera.instance.ResetTempFOV();
 	}
 }
```

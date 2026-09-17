# `GrapplingPoint.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+17/-8` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/GrapplingPoint.cs
+++ b/GrapplingPoint.cs
@@ -153,7 +153,10 @@
 			{
 				m_localGrappler = this;
 			}
-			m_instanceSound = Object.Instantiate(m_pullSound, base.transform);
+			if ((bool)m_pullSound)
+			{
+				m_instanceSound = Object.Instantiate(m_pullSound, base.transform);
+			}
 		}
 		Transform leftHand;
 		if (character is Humanoid humanoid)
@@ -162,12 +165,12 @@
 			if ((object)visEquipment != null)
 			{
 				leftHand = visEquipment.m_leftHand;
-				goto IL_008e;
+				goto IL_009b;
 			}
 		}
 		leftHand = base.transform;
-		goto IL_008e;
-		IL_008e:
+		goto IL_009b;
+		IL_009b:
 		m_attachPoint = leftHand;
 		m_time = 0f;
 		UpdateLinePosition();
@@ -352,8 +355,11 @@
 		m_rotateCharacter = false;
 		GameCamera.instance.ResetTempFOV();
 		m_breakingTime = 0f;
-		m_instanceSound.GetComponent<ZSFX>().Stop();
-		Object.Destroy(m_instanceSound);
+		if ((bool)m_instanceSound)
+		{
+			m_instanceSound.GetComponent<ZSFX>().Stop();
+			Object.Destroy(m_instanceSound);
+		}
 	}
 
 	private void StandUp()
@@ -368,8 +374,11 @@
 
 	private void UpdateLinePosition()
 	{
-		m_lineRenderer.SetPosition(0, base.transform.position + base.transform.rotation * m_attachOffsetProjectile);
-		m_lineRenderer.SetPosition(1, m_attachPoint.position + m_attachPoint.rotation * m_attachOffsetHand);
+		if ((object)m_attachPoint != null)
+		{
+			m_lineRenderer.SetPosition(0, base.transform.position + base.transform.rotation * m_attachOffsetProjectile);
+			m_lineRenderer.SetPosition(1, m_attachPoint.position + m_attachPoint.rotation * m_attachOffsetHand);
+		}
 	}
 
 	public void Break(bool early)
```

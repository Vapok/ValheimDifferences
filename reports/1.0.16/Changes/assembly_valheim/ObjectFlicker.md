# `ObjectFlicker.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ObjectFlicker.cs
+++ b/ObjectFlicker.cs
@@ -56,9 +56,9 @@
 
 	public void Reset()
 	{
-		m_basePosition = base.transform.localPosition;
-		m_baseRotation = base.transform.localRotation.eulerAngles;
-		m_baseScale = base.transform.localScale;
+		m_basePosition = transform.localPosition;
+		m_baseRotation = transform.localRotation.eulerAngles;
+		m_baseScale = transform.localScale;
 		m_moveTime = new Vector3(UnityEngine.Random.Range(0f, 10f), UnityEngine.Random.Range(0f, 10f), UnityEngine.Random.Range(0f, 10f));
 		m_rotationTime = UnityEngine.Random.Range(0f, 10f);
 		m_scaleTime = UnityEngine.Random.Range(0f, 10f);
@@ -92,7 +92,7 @@
 			m_offset.y = MathF.Cos(m_moveTime.y * 0.564364f + 11f) * MathF.Sin(m_moveTime.y * 0.5887422f + 91f);
 			m_offset.z = MathF.Cos(m_moveTime.z * 0.518348f + 46f) * MathF.Cos(m_moveTime.z * 0.5963696f + 3f);
 			m_offset.Scale(m_movementRange);
-			base.transform.localPosition = m_basePosition + m_offset;
+			transform.localPosition = m_basePosition + m_offset;
 		}
 		if (m_rotationSpeed != Vector3.zero)
 		{
@@ -109,7 +109,7 @@
 			{
 				quaternion = Quaternion.Slerp(Quaternion.identity, quaternion, SpeedMultiplier);
 			}
-			base.transform.rotation *= quaternion;
+			transform.rotation *= quaternion;
 		}
 		if (m_scaleSpeed > 0f)
 		{
@@ -120,11 +120,11 @@
 			m_scale.Scale(m_scaleRange);
 			if (m_uniformX)
 			{
-				base.transform.localScale = m_baseScale * (1f + m_scale.x);
+				transform.localScale = m_baseScale * (1f + m_scale.x);
 			}
 			else
 			{
-				base.transform.localScale = Vector3.Scale(m_baseScale, Vector3.one + m_scale);
+				transform.localScale = Vector3.Scale(m_baseScale, Vector3.one + m_scale);
 			}
 		}
 	}
```

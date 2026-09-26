# `CharacterAnimEvent.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CharacterAnimEvent.cs
+++ b/CharacterAnimEvent.cs
@@ -367,7 +367,7 @@
 			return;
 		}
 		Camera mainCamera = Utils.GetMainCamera();
-		if (mainCamera == null || Vector3.Distance(base.transform.position, mainCamera.transform.position) > 64f)
+		if (mainCamera == null || Vector3.Distance(transform.position, mainCamera.transform.position) > 64f)
 		{
 			return;
 		}
@@ -396,7 +396,7 @@
 			{
 				num3 /= 4f;
 			}
-			float target = 1f - Mathf.Clamp01(base.transform.InverseTransformPoint(position - base.transform.up * num2).y / num);
+			float target = 1f - Mathf.Clamp01(transform.InverseTransformPoint(position - transform.up * num2).y / num);
 			foot2.m_ikWeight = Mathf.MoveTowards(foot2.m_ikWeight, target, deltaTime * 10f);
 			m_animator.SetIKPositionWeight(ikHandle, foot2.m_ikWeight);
 			m_animator.SetIKRotationWeight(ikHandle, foot2.m_ikWeight * 0.5f);
@@ -597,11 +597,11 @@
 			float num2 = (m_useFeetValues ? foot.m_footOffset : m_footOffset);
 			float num3 = (m_useFeetValues ? foot.m_footStepHeight : m_footStepHeight);
 			float num4 = (m_useFeetValues ? foot.m_stabalizeDistance : m_stabalizeDistance);
-			Vector3 vector = foot.m_transform.position - base.transform.up * num2;
-			Gizmos.color = ((vector.y > base.transform.position.y) ? Color.red : Color.white);
+			Vector3 vector = foot.m_transform.position - transform.up * num2;
+			Gizmos.color = ((vector.y > transform.position.y) ? Color.red : Color.white);
 			Gizmos.DrawWireSphere(vector, 0.1f);
 			Gizmos.color = Color.yellow;
-			Gizmos.DrawWireCube(new Vector3(vector.x, base.transform.position.y, vector.z) + Vector3.up * num, new Vector3(1f, 0.01f, 1f));
+			Gizmos.DrawWireCube(new Vector3(vector.x, transform.position.y, vector.z) + Vector3.up * num, new Vector3(1f, 0.01f, 1f));
 			Gizmos.color = Color.red;
 			Gizmos.DrawLine(vector, vector + Vector3.up * num3);
 			if (num4 > 0f)
```

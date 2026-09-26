# `TestSceneCharacter.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/TestSceneCharacter.cs
+++ b/TestSceneCharacter.cs
@@ -52,19 +52,19 @@
 		Vector3 zero2 = Vector3.zero;
 		if (ZInput.GetKey(KeyCode.A))
 		{
-			zero2 -= base.transform.right * m_speed;
+			zero2 -= transform.right * m_speed;
 		}
 		if (ZInput.GetKey(KeyCode.D))
 		{
-			zero2 += base.transform.right * m_speed;
+			zero2 += transform.right * m_speed;
 		}
 		if (ZInput.GetKey(KeyCode.W))
 		{
-			zero2 += base.transform.forward * m_speed;
+			zero2 += transform.forward * m_speed;
 		}
 		if (ZInput.GetKey(KeyCode.S))
 		{
-			zero2 -= base.transform.forward * m_speed;
+			zero2 -= transform.forward * m_speed;
 		}
 		if (ZInput.GetKeyDown(KeyCode.Space))
 		{
@@ -73,9 +73,9 @@
 		Vector3 force = zero2 - m_body.linearVelocity;
 		force.y = 0f;
 		m_body.AddForce(force, ForceMode.VelocityChange);
-		base.transform.rotation = m_lookYaw;
+		transform.rotation = m_lookYaw;
 		Quaternion quaternion = m_lookYaw * Quaternion.Euler(m_lookPitch, 0f, 0f);
-		mainCamera.transform.position = base.transform.position - quaternion * Vector3.forward * m_cameraDistance;
-		mainCamera.transform.LookAt(base.transform.position + Vector3.up);
+		mainCamera.transform.position = transform.position - quaternion * Vector3.forward * m_cameraDistance;
+		mainCamera.transform.LookAt(transform.position + Vector3.up);
 	}
 }
```

# `LuxParticles.Demo/LuxParticles_ExtendedFlycam.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `Assembly-CSharp.dll`
* **Status**: `🟡 MODIFIED` (`+10/-10` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/LuxParticles.Demo/LuxParticles_ExtendedFlycam.cs
+++ b/LuxParticles.Demo/LuxParticles_ExtendedFlycam.cs
@@ -24,7 +24,7 @@
 
 	private void Start()
 	{
-		rotationX = base.transform.eulerAngles.y;
+		rotationX = transform.eulerAngles.y;
 		cam = GetComponent<Camera>();
 		if (cam != null)
 		{
@@ -40,16 +40,16 @@
 		rotationY = Mathf.Clamp(rotationY, -90f, 90f);
 		Quaternion b = Quaternion.AngleAxis(rotationX, Vector3.up);
 		b *= Quaternion.AngleAxis(rotationY, Vector3.left);
-		base.transform.localRotation = Quaternion.Slerp(base.transform.localRotation, b, deltaTime * 6f);
+		transform.localRotation = Quaternion.Slerp(transform.localRotation, b, deltaTime * 6f);
 		if (Input.GetKey(KeyCode.LeftShift) || Input.GetKey(KeyCode.RightShift))
 		{
-			base.transform.position += base.transform.forward * (normalMoveSpeed * fastMoveFactor) * Input.GetAxis("Vertical") * deltaTime;
-			base.transform.position += base.transform.right * (normalMoveSpeed * fastMoveFactor) * Input.GetAxis("Horizontal") * deltaTime;
+			transform.position += transform.forward * (normalMoveSpeed * fastMoveFactor) * Input.GetAxis("Vertical") * deltaTime;
+			transform.position += transform.right * (normalMoveSpeed * fastMoveFactor) * Input.GetAxis("Horizontal") * deltaTime;
 		}
 		else if (Input.GetKey(KeyCode.LeftControl) || Input.GetKey(KeyCode.RightControl))
 		{
-			base.transform.position += base.transform.forward * (normalMoveSpeed * slowMoveFactor) * Input.GetAxis("Vertical") * deltaTime;
-			base.transform.position += base.transform.right * (normalMoveSpeed * slowMoveFactor) * Input.GetAxis("Horizontal") * deltaTime;
+			transform.position += transform.forward * (normalMoveSpeed * slowMoveFactor) * Input.GetAxis("Vertical") * deltaTime;
+			transform.position += transform.right * (normalMoveSpeed * slowMoveFactor) * Input.GetAxis("Horizontal") * deltaTime;
 		}
 		else
 		{
@@ -59,17 +59,17 @@
 			}
 			else
 			{
-				base.transform.position += base.transform.forward * normalMoveSpeed * Input.GetAxis("Vertical") * deltaTime;
+				transform.position += transform.forward * normalMoveSpeed * Input.GetAxis("Vertical") * deltaTime;
 			}
-			base.transform.position += base.transform.right * normalMoveSpeed * Input.GetAxis("Horizontal") * deltaTime;
+			transform.position += transform.right * normalMoveSpeed * Input.GetAxis("Horizontal") * deltaTime;
 		}
 		if (Input.GetKey(KeyCode.Q))
 		{
-			base.transform.position -= base.transform.up * climbSpeed * deltaTime;
+			transform.position -= transform.up * climbSpeed * deltaTime;
 		}
 		if (Input.GetKey(KeyCode.E))
 		{
-			base.transform.position += base.transform.up * climbSpeed * deltaTime;
+			transform.position += transform.up * climbSpeed * deltaTime;
 		}
 	}
 }
```

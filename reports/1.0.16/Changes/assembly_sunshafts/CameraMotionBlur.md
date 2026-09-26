# `UnityStandardAssets.ImageEffects/CameraMotionBlur.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+15/-15` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/CameraMotionBlur.cs
+++ b/UnityStandardAssets.ImageEffects/CameraMotionBlur.cs
@@ -104,7 +104,7 @@
 		{
 			_camera = GetComponent<Camera>();
 		}
-		wasActive = base.gameObject.activeInHierarchy;
+		wasActive = gameObject.activeInHierarchy;
 		currentStereoViewProjMat = new Matrix4x4[2];
 		prevStereoViewProjMat = new Matrix4x4[2];
 		CalculateViewProjection();
@@ -200,11 +200,11 @@
 		temporary3.wrapMode = TextureWrapMode.Clamp;
 		temporary2.wrapMode = TextureWrapMode.Clamp;
 		CalculateViewProjection();
-		if (base.gameObject.activeInHierarchy && !wasActive)
+		if (gameObject.activeInHierarchy && !wasActive)
 		{
 			Remember();
 		}
-		wasActive = base.gameObject.activeInHierarchy;
+		wasActive = gameObject.activeInHierarchy;
 		Matrix4x4 matrix4x = Matrix4x4.Inverse(currentViewProjMat);
 		motionBlurMaterial.SetMatrix("_InvViewProj", matrix4x);
 		motionBlurMaterial.SetMatrix("_PrevViewProj", prevViewProjMat);
@@ -242,21 +242,21 @@
 		if (filterType == MotionBlurFilter.CameraMotion)
 		{
 			Vector4 zero = Vector4.zero;
-			float num4 = Vector3.Dot(base.transform.up, Vector3.up);
-			Vector3 rhs = prevFramePos - base.transform.position;
+			float num4 = Vector3.Dot(transform.up, Vector3.up);
+			Vector3 rhs = prevFramePos - transform.position;
 			float magnitude = rhs.magnitude;
 			float num5 = 1f;
-			num5 = Vector3.Angle(base.transform.up, prevFrameUp) / _camera.fieldOfView * ((float)source.width * 0.75f);
+			num5 = Vector3.Angle(transform.up, prevFrameUp) / _camera.fieldOfView * ((float)source.width * 0.75f);
 			zero.x = rotationScale * num5;
-			num5 = Vector3.Angle(base.transform.forward, prevFrameForward) / _camera.fieldOfView * ((float)source.width * 0.75f);
+			num5 = Vector3.Angle(transform.forward, prevFrameForward) / _camera.fieldOfView * ((float)source.width * 0.75f);
 			zero.y = rotationScale * num4 * num5;
-			num5 = Vector3.Angle(base.transform.forward, prevFrameForward) / _camera.fieldOfView * ((float)source.width * 0.75f);
+			num5 = Vector3.Angle(transform.forward, prevFrameForward) / _camera.fieldOfView * ((float)source.width * 0.75f);
 			zero.z = rotationScale * (1f - num4) * num5;
 			if (magnitude > Mathf.Epsilon && movementScale > Mathf.Epsilon)
 			{
-				zero.w = movementScale * Vector3.Dot(base.transform.forward, rhs) * ((float)source.width * 0.5f);
-				zero.x += movementScale * Vector3.Dot(base.transform.up, rhs) * ((float)source.width * 0.5f);
-				zero.y += movementScale * Vector3.Dot(base.transform.right, rhs) * ((float)source.width * 0.5f);
+				zero.w = movementScale * Vector3.Dot(transform.forward, rhs) * ((float)source.width * 0.5f);
+				zero.x += movementScale * Vector3.Dot(transform.up, rhs) * ((float)source.width * 0.5f);
+				zero.y += movementScale * Vector3.Dot(transform.right, rhs) * ((float)source.width * 0.5f);
 			}
 			if (preview)
 			{
@@ -337,9 +337,9 @@
 	private void Remember()
 	{
 		prevViewProjMat = currentViewProjMat;
-		prevFrameForward = base.transform.forward;
-		prevFrameUp = base.transform.up;
-		prevFramePos = base.transform.position;
+		prevFrameForward = transform.forward;
+		prevFrameUp = transform.up;
+		prevFramePos = transform.position;
 		prevStereoViewProjMat[0] = currentStereoViewProjMat[0];
 		prevStereoViewProjMat[1] = currentStereoViewProjMat[1];
 	}
@@ -372,7 +372,7 @@
 
 	private void StartFrame()
 	{
-		prevFramePos = Vector3.Slerp(prevFramePos, base.transform.position, 0.75f);
+		prevFramePos = Vector3.Slerp(prevFramePos, transform.position, 0.75f);
 	}
 
 	private static int divRoundUp(int x, int d)
```

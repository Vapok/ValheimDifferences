# `UnityStandardAssets.ImageEffects/GlobalFog.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/GlobalFog.cs
+++ b/UnityStandardAssets.ImageEffects/GlobalFog.cs
@@ -52,19 +52,19 @@
 			return;
 		}
 		Camera component = GetComponent<Camera>();
-		Transform obj = component.transform;
+		Transform transform = component.transform;
 		Vector3[] array = new Vector3[4];
 		component.CalculateFrustumCorners(new Rect(0f, 0f, 1f, 1f), component.farClipPlane, component.stereoActiveEye, array);
-		Vector3 vector = obj.TransformVector(array[0]);
-		Vector3 vector2 = obj.TransformVector(array[1]);
-		Vector3 vector3 = obj.TransformVector(array[2]);
-		Vector3 vector4 = obj.TransformVector(array[3]);
+		Vector3 vector = transform.TransformVector(array[0]);
+		Vector3 vector2 = transform.TransformVector(array[1]);
+		Vector3 vector3 = transform.TransformVector(array[2]);
+		Vector3 vector4 = transform.TransformVector(array[3]);
 		Matrix4x4 identity = Matrix4x4.identity;
 		identity.SetRow(0, vector);
 		identity.SetRow(1, vector4);
 		identity.SetRow(2, vector2);
 		identity.SetRow(3, vector3);
-		Vector3 position = obj.position;
+		Vector3 position = transform.position;
 		float num = position.y - height;
 		float z = ((num <= 0f) ? 1f : 0f);
 		float y = (excludeFarPixels ? 1f : 2f);
@@ -79,7 +79,7 @@
 		bool flag = fogMode == FogMode.Linear;
 		float num2 = (flag ? (fogEndDistance - fogStartDistance) : 0f);
 		float num3 = ((Mathf.Abs(num2) > 0.0001f) ? (1f / num2) : 0f);
-		Vector4 value = default(Vector4);
+		Vector4 value = default;
 		value.x = fogDensity * 1.2011224f;
 		value.y = fogDensity * 1.442695f;
 		value.z = (flag ? (0f - num3) : 0f);
```

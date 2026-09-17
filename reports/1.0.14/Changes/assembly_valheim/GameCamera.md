# `GameCamera.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/GameCamera.cs
+++ b/GameCamera.cs
@@ -593,8 +593,10 @@
 		}
 		vector += Vector3.up * ZInput.GetJoyRTrigger();
 		vector -= Vector3.up * ZInput.GetJoyLTrigger();
-		vector += Vector3.right * ZInput.GetJoyLeftStickX();
-		vector += -Vector3.forward * ZInput.GetJoyLeftStickY();
+		Vector2 joyLeftStick = ZInput.GetJoyLeftStick();
+		joyLeftStick *= joyLeftStick.magnitude;
+		vector += Vector3.right * joyLeftStick.x;
+		vector += Vector3.forward * joyLeftStick.y;
 		if (ZInput.GetButtonDown("JoyButtonB") || ZInput.GetButtonDown("Block"))
 		{
 			m_freeFlySavedVel = vector;
```

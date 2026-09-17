# `PlayerController.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+16/-13` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/PlayerController.cs
+++ b/PlayerController.cs
@@ -103,8 +103,9 @@
 		{
 			zero.x++;
 		}
-		zero.x += ZInput.GetJoyLeftStickX();
-		zero.z += 0f - ZInput.GetJoyLeftStickY();
+		Vector2 joyLeftStick = ZInput.GetJoyLeftStick();
+		zero.x += joyLeftStick.x;
+		zero.z += joyLeftStick.y;
 		if (zero.magnitude > 1f)
 		{
 			zero.Normalize();
@@ -123,13 +124,15 @@
 		bool button = ZInput.GetButton("Jump");
 		bool jump = (button && !m_lastJump) || (ZInput.GetButtonDown("JoyJump") && !flag2 && !flag && !Hud.InRadial());
 		m_lastJump = button;
-		bool dodge = ZInput.IsNonClassicFunctionality() && ZInput.IsGamepadActive() && ZInput.GetButtonDown("JoyDodge") && !flag && !Hud.InRadial();
-		bool flag6 = InventoryGui.IsVisible();
-		bool flag7 = (ZInput.GetButton("Crouch") || ZInput.GetButton("JoyCrouch")) && !flag6 && !Hud.InRadial();
-		bool crouch = flag7 && !m_lastCrouch;
-		m_lastCrouch = flag7;
-		bool flag8 = ZInput.GetButton("Run") || ZInput.GetButton("JoyRun");
-		if ((!m_lastRunPressed & flag8) && m_character.GetStamina() > 0f)
+		bool num = ZInput.IsNonClassicFunctionality() && ZInput.IsGamepadActive() && ZInput.GetButtonDown("JoyDodge");
+		bool flag6 = !ZInput.IsGamepadActive() && ZInput.GetButtonDown("AltDodge");
+		bool dodge = (num | flag6) && !flag && !Hud.InRadial();
+		bool flag7 = InventoryGui.IsVisible();
+		bool flag8 = (ZInput.GetButton("Crouch") || ZInput.GetButton("JoyCrouch")) && !flag7 && !Hud.InRadial();
+		bool crouch = flag8 && !m_lastCrouch;
+		m_lastCrouch = flag8;
+		bool flag9 = ZInput.GetButton("Run") || ZInput.GetButton("JoyRun");
+		if ((!m_lastRunPressed & flag9) && m_character.GetStamina() > 0f)
 		{
 			m_runPressedWhileStamina = true;
 		}
@@ -139,7 +142,7 @@
 		}
 		if (ZInput.ToggleRun)
 		{
-			if (!m_lastRunPressed & flag8)
+			if (!m_lastRunPressed & flag9)
 			{
 				m_run = !m_run;
 			}
@@ -150,16 +153,16 @@
 		}
 		else
 		{
-			m_run = flag8 && m_runPressedWhileStamina;
+			m_run = flag9 && m_runPressedWhileStamina;
 		}
 		float magnitude = zero.magnitude;
 		if (magnitude < 0.05f && m_lastMagnitude < 0.05f && !m_character.m_autoRun)
 		{
 			m_run = false;
 		}
-		m_lastRunPressed = flag8;
+		m_lastRunPressed = flag9;
 		m_lastMagnitude = magnitude;
-		m_lastRunPressed = flag8;
+		m_lastRunPressed = flag9;
 		bool button2 = ZInput.GetButton("AutoRun");
 		if (takeInputDelay > 0f)
 		{
```

# `ZInput.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+97/-53` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `private Vector2 ApplyDeadzoneVector(Vector2 value)`
- `private Vector2 ApplyDeadzoneVector(Vector2 value, bool smooth)`
- `private float ApplyDeadzoneFloat(float value)`
- `private float ApplyDeadzoneFloat(float value, bool smooth)`
- `private void ApplyDeadzoneToMagnitude(ref float magnitude)`
- `private void ApplyRebind(InputActionRebindingExtensions.RebindingOperation rebinding, string path)`
- `private void CancelOnAbortInput(InputActionRebindingExtensions.RebindingOperation rebinding)`
- `private void OnRebindComplete(InputAction action)`
- `private void OnRebindComplete(InputActionRebindingExtensions.RebindingOperation op, InputAction action)`
- `private void UpdateGyro()`
- `public static Vector2 GetJoyLeftStick()`
- `public static Vector2 GetJoyRightStick()`
- `public static float GetJoyLeftStickX()`
- `public static float GetJoyLeftStickX(bool smooth = false)`
- `public static float GetJoyLeftStickY()`
- `public static float GetJoyLeftStickY(bool smooth = true)`
- `public static float GetJoyRightStickX()`
- `public static float GetJoyRightStickX(bool smooth = true)`
- `public static float GetJoyRightStickY()`
- `public static float GetJoyRightStickY(bool smooth = true)`

---

## 📝 Code Diff

```diff
--- a/ZInput.cs
+++ b/ZInput.cs
@@ -140,6 +140,10 @@
 		{
 			Name = name;
 			ButtonAction = new InputAction(name, InputActionType.PassThrough, path, "press(pressPoint=" + pressPoint + ")");
+			if (path == "")
+			{
+				ButtonAction.AddBinding("");
+			}
 			DisplayNameOverride = displayNameOverride;
 			Source = source;
 			AltKey = altKey;
@@ -1564,9 +1568,7 @@
 			value.Tick(dt);
 		}
 		UpdateRumble();
-		ReadRawControllerSensorValues();
-		UpdateGyroAngularVelocity();
-		UpdateGravityVector();
+		UpdateGyro();
 		m_systemUpdated = false;
 	}
 
@@ -1914,27 +1916,37 @@
 		return ReadValueDef<float>("TriggerR");
 	}
 
-	public static float GetJoyRightStickX(bool smooth = true)
-	{
-		return ReadValueDef<Vector2>("StickR", smooth).x;
-	}
-
-	public static float GetJoyRightStickY(bool smooth = true)
-	{
-		return 0f - ReadValueDef<Vector2>("StickR", smooth).y;
-	}
-
-	public static float GetJoyLeftStickX(bool smooth = false)
-	{
-		return ReadValueDef<Vector2>("StickL", smooth).x;
-	}
-
-	public static float GetJoyLeftStickY(bool smooth = true)
-	{
-		return 0f - ReadValueDef<Vector2>("StickL", smooth).y;
-	}
-
-	private static T ReadValueDef<T>(string name, bool smooth = false) where T : struct
+	public static Vector2 GetJoyRightStick()
+	{
+		return ReadValueDef<Vector2>("StickR");
+	}
+
+	public static float GetJoyRightStickX()
+	{
+		return GetJoyRightStick().x;
+	}
+
+	public static float GetJoyRightStickY()
+	{
+		return 0f - GetJoyRightStick().y;
+	}
+
+	public static Vector2 GetJoyLeftStick()
+	{
+		return ReadValueDef<Vector2>("StickL");
+	}
+
+	public static float GetJoyLeftStickX()
+	{
+		return GetJoyLeftStick().x;
+	}
+
+	public static float GetJoyLeftStickY()
+	{
+		return 0f - GetJoyLeftStick().y;
+	}
+
+	private static T ReadValueDef<T>(string name) where T : struct
 	{
 		if (m_instance == null)
 		{
@@ -1950,11 +1962,11 @@
 		{
 			if (valueRaw is Vector2 value3)
 			{
-				return (T)(object)m_instance.ApplyDeadzoneVector(value3, smooth);
+				return (T)(object)m_instance.ApplyDeadzoneVector(value3);
 			}
 			return valueRaw;
 		}
-		return (T)(object)m_instance.ApplyDeadzoneFloat(value2, smooth);
+		return (T)(object)m_instance.ApplyDeadzoneFloat(value2);
 	}
 
 	public static bool GetRadialTap()
@@ -2126,7 +2138,7 @@
 			return value.DisplayNameOverride;
 		}
 		InputBinding inputBinding = value.ButtonAction.bindings.FirstOrDefault();
-		if (inputBinding == default(InputBinding))
+		if (inputBinding == default(InputBinding) || string.IsNullOrEmpty(inputBinding.effectivePath))
 		{
 			if (!emptyStringOnMissing)
 			{
@@ -2226,7 +2238,11 @@
 		}
 		if (text == "motionsensor")
 		{
-			return str += Utils.GetPlatformSpecificLocalizationKey("$settings_controller_motion_sensor", localizeSwitch: true, localizePlayStation: true, localizeXbox: false);
+			if (!button.AltKey)
+			{
+				return str += Utils.GetPlatformSpecificLocalizationKey("$settings_controller_motion_sensor", localizeSwitch: true, localizePlayStation: true, localizeXbox: false);
+			}
+			return str = str + "<color=#AAAAAA>" + Utils.GetPlatformSpecificLocalizationKey("$settings_controller_motion_sensor", localizeSwitch: true, localizePlayStation: true, localizeXbox: false) + "</color>";
 		}
 		str = (button.AltKey ? (str + "<color=#AAAAAA>$settings_" + text + "</color>") : (((!IsNonClassicFunctionality() || !(text == "rotate")) && !(text == "rotateright")) ? (str + "$settings_" + text) : (str + "$rotate_build_mode")));
 		return str;
@@ -2320,25 +2336,39 @@
 			return;
 		}
 		action.Disable();
-		InputActionRebindingExtensions.RebindingOperation rebindingOperation = action.PerformInteractiveRebinding().WithCancelingThrough("<Keyboard>/escape").WithCancelingThrough("<Gamepad>/*");
+		InputActionRebindingExtensions.RebindingOperation rebindingOperation = action.PerformInteractiveRebinding().OnPotentialMatch(CancelOnAbortInput).OnApplyBinding(ApplyRebind);
 		if (value.Name.Contains("Tab"))
 		{
 			rebindingOperation.WithControlsExcluding("Mouse");
 		}
-		rebindingOperation.Start().OnComplete(delegate
-		{
-			OnRebindComplete(action);
-		}).OnCancel(delegate
-		{
-			OnRebindComplete(action);
+		rebindingOperation.Start().OnComplete(delegate(InputActionRebindingExtensions.RebindingOperation op)
+		{
+			OnRebindComplete(op, action);
+		}).OnCancel(delegate(InputActionRebindingExtensions.RebindingOperation op)
+		{
+			OnRebindComplete(op, action);
 		});
 		s_IsRebindActive = true;
 	}
 
-	private void OnRebindComplete(InputAction action)
+	private void CancelOnAbortInput(InputActionRebindingExtensions.RebindingOperation rebinding)
+	{
+		if (rebinding.selectedControl.path == "/Keyboard/escape" || rebinding.selectedControl.device is Gamepad)
+		{
+			rebinding.Cancel();
+		}
+	}
+
+	private void ApplyRebind(InputActionRebindingExtensions.RebindingOperation rebinding, string path)
+	{
+		rebinding.action.ApplyBindingOverride((path == "<Keyboard>/delete") ? string.Empty : path);
+	}
+
+	private void OnRebindComplete(InputActionRebindingExtensions.RebindingOperation op, InputAction action)
 	{
 		action.Enable();
 		s_IsRebindActive = false;
+		op.Dispose();
 	}
 
 	public void ResetToDefault(string name = "all")
@@ -2480,6 +2510,13 @@
 		}
 	}
 
+	private void UpdateGyro()
+	{
+		ReadRawControllerSensorValues();
+		UpdateGyroAngularVelocity();
+		UpdateGravityVector();
+	}
+
 	private void ReadRawControllerSensorValues()
 	{
 	}
@@ -2574,22 +2611,24 @@
 			select g).SelectMany((IGrouping<string, KeyValuePair<string, ButtonDef>> g) => g.Select((KeyValuePair<string, ButtonDef> b) => b.Key)).ToList();
 	}
 
-	private float ApplyDeadzoneFloat(float value, bool smooth)
+	private float ApplyDeadzoneFloat(float value)
 	{
 		float num = Mathf.Sign(value);
 		value = Mathf.Abs(value);
-		value = Mathf.Clamp01(value - 0.2f);
-		value *= 1.25f;
-		if (smooth)
-		{
-			value *= value;
-		}
+		ApplyDeadzoneToMagnitude(ref value);
 		return value * num;
 	}
 
-	private Vector2 ApplyDeadzoneVector(Vector2 value, bool smooth)
-	{
-		return new Vector2(ApplyDeadzoneFloat(value.x, smooth), ApplyDeadzoneFloat(value.y, smooth));
+	private Vector2 ApplyDeadzoneVector(Vector2 value)
+	{
+		float magnitude = value.magnitude;
+		ApplyDeadzoneToMagnitude(ref magnitude);
+		return value.normalized * magnitude;
+	}
+
+	private void ApplyDeadzoneToMagnitude(ref float magnitude)
+	{
+		magnitude = Mathf.Clamp01((magnitude - 0.2f) / 0.8f);
 	}
 
 	private static float GetScrollModifier()
@@ -2870,7 +2909,7 @@
 
 	private void AddButton(string name, string path, bool altKey = false, bool showHints = true, bool rebindable = false, float repeatDelay = 0f, float repeatInterval = 0f)
 	{
-		InputSource inputSource = (path.Contains("Gamepad") ? InputSource.Gamepad : InputSource.KeyboardMouse);
+		InputSource inputSource = ((path != null && path.Contains("Gamepad")) ? InputSource.Gamepad : InputSource.KeyboardMouse);
 		if (inputSource == InputSource.Gamepad)
 		{
 			m_presentationButtons.Add(new LayoutButton(name, LayoutContext.CurrentLayout), new ButtonPresentation(name, path, altKey, showHints));
@@ -2965,6 +3004,7 @@
 		AddButton("Hide", KeyToPath(Key.R), altKey: false, showHints: true, rebindable: true);
 		AddButton("Jump", KeyToPath(Key.Space), altKey: false, showHints: true, rebindable: true);
 		AddButton("Crouch", KeyToPath(Key.LeftCtrl), altKey: false, showHints: true, rebindable: true);
+		AddButton("AltDodge", "", altKey: false, showHints: true, rebindable: true);
 		AddButton("Run", KeyToPath(Key.LeftShift), altKey: false, showHints: true, rebindable: true);
 		AddButton("ToggleWalk", KeyToPath(Key.C), altKey: false, showHints: true, rebindable: true);
 		AddButton("AutoRun", KeyToPath(Key.Q), altKey: false, showHints: true, rebindable: true);
@@ -2995,6 +3035,10 @@
 		AddButton("OpenRadial", KeyToPath(Key.G), altKey: false, showHints: true, rebindable: true);
 		AddButton("OpenEmote", KeyToPath(Key.T), altKey: false, showHints: true, rebindable: true);
 		AddButton("RadialSecondaryInteract", MouseButtonToPath(MouseButton.Right));
+		for (int i = 1; i <= 8; i++)
+		{
+			AddButton($"Hotbar{i}Alt", "", altKey: false, showHints: true, rebindable: true);
+		}
 		AddButton("Chat", KeyToPath(Key.Enter));
 		AddButton("Hotbar1", KeyToPath(Key.Digit1));
 		AddButton("Hotbar2", KeyToPath(Key.Digit2));
@@ -3108,10 +3152,10 @@
 			AddButton("JoyInventory", s_gamepadInputPathMap[GamepadInput.FaceButtonY]);
 			AddButton("JoyBlock", s_gamepadInputPathMap[GamepadInput.BumperL]);
 			AddButton("JoyAttack", s_gamepadInputPathMap[GamepadInput.BumperR]);
-			AddButton("JoyHide", s_gamepadInputPathMap[GamepadInput.TriggerL], altKey: true);
+			AddButton("JoyHide", s_gamepadInputPathMap[GamepadInput.TriggerL]);
 			if (Application.platform == RuntimePlatform.Switch2 || Application.platform == RuntimePlatform.PS5)
 			{
-				AddButton("JoyMotionSensor", s_gamepadInputPathMap[GamepadInput.TriggerL]);
+				AddButton("JoyMotionSensor", s_gamepadInputPathMap[GamepadInput.TriggerL], altKey: true);
 			}
 			AddButton("JoySecondaryAttack", s_gamepadInputPathMap[GamepadInput.TriggerR]);
 			AddButton("JoyRun", s_gamepadInputPathMap[GamepadInput.StickLButton]);
@@ -3157,10 +3201,10 @@
 			AddButton("JoyDodge", s_gamepadInputPathMap[GamepadInput.FaceButtonB], altKey: true);
 			AddButton("JoyUse", s_gamepadInputPathMap[GamepadInput.FaceButtonX]);
 			AddButton("JoyInventory", s_gamepadInputPathMap[GamepadInput.FaceButtonY]);
-			AddButton("JoyHide", s_gamepadInputPathMap[GamepadInput.BumperL], altKey: true);
+			AddButton("JoyHide", s_gamepadInputPathMap[GamepadInput.BumperL]);
 			if (Application.platform == RuntimePlatform.Switch2 || Application.platform == RuntimePlatform.PS5)
 			{
-				AddButton("JoyMotionSensor", s_gamepadInputPathMap[GamepadInput.BumperL]);
+				AddButton("JoyMotionSensor", s_gamepadInputPathMap[GamepadInput.BumperL], altKey: true);
 			}
 			AddButton("JoySecondaryAttack", s_gamepadInputPathMap[GamepadInput.BumperR]);
 			AddButton("JoyBlock", s_gamepadInputPathMap[GamepadInput.TriggerL]);
@@ -3210,8 +3254,8 @@
 			bool flag = MouseLayout == SwitchMouseLayout.PC;
 			AddButton("JoyBlock", s_gamepadInputPathMap[flag ? GamepadInput.TriggerR : GamepadInput.BumperL]);
 			AddButton("JoyAttack", s_gamepadInputPathMap[GamepadInput.BumperR]);
-			AddButton("JoyHide", s_gamepadInputPathMap[GamepadInput.TriggerL], altKey: true);
-			AddButton("JoyMotionSensor", s_gamepadInputPathMap[GamepadInput.TriggerL]);
+			AddButton("JoyHide", s_gamepadInputPathMap[GamepadInput.TriggerL]);
+			AddButton("JoyMotionSensor", s_gamepadInputPathMap[GamepadInput.TriggerL], altKey: true);
 			AddButton("JoySecondaryAttack", s_gamepadInputPathMap[flag ? GamepadInput.StickRButton : GamepadInput.TriggerR]);
 			AddButton("JoyRun", s_gamepadInputPathMap[GamepadInput.StickLButton]);
 			AddButton("JoyCrouch", s_gamepadInputPathMap[flag ? GamepadInput.BumperL : GamepadInput.StickRButton]);
```

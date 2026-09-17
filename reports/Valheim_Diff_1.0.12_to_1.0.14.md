# Valheim API & Assembly Diff: `1.0.12` $\rightarrow$ `1.0.14`

> Automated decompilation comparison, mod impact report, and transpiler IL safety audit generated between Valheim version **1.0.12** and **1.0.14**.

## 📊 Executive Summary

| Metric | Count |
| :--- | :--- |
| **Assemblies Changed** | `2` / `9` |
| **Game Classes Modified** | `32` |
| **Game Classes Added** | `0` |
| **Game Classes Deleted** | `0` |
| **Total Lines Added** | `+412` |
| **Total Lines Removed** | `-287` |
| **High Risk Mod Patches** | `0` mod(s) |
| **Medium Risk Mod Patches** | `11` mod(s) |
| **Transpiler Hooks Audited** | `17` total (`1` modified / `16` verified safe) |

## 🔬 Transpiler Safety Audit

Audits every Harmony Transpiler across workspace mods to verify whether the underlying vanilla IL hook methods were modified in this game version.

| Status | Mod | Hook Target Class & Method | Audit Result | Source Location |
| :---: | :--- | :--- | :--- | :--- |
| 🟢 `SAFE` | **`AdventureBackpacks`** | `ItemData.GetWeight` | Class 'ItemData' and method 'GetWeight' are 100% UNCHANGED. | `ItemDrop.cs:14` |
| 🟢 `SAFE` | **`AdventureBackpacks`** | `Container.Awake` | Class 'Container' and method 'Awake' are 100% UNCHANGED. | `Container.cs:68` |
| 🛡️ `VERIFIED SAFE` | **`AdventureBackpacks`** | `Humanoid.UpdateEquipmentStatusEffects` | Class 'Humanoid' was modified elsewhere, but method 'UpdateEquipmentStatusEffects' is UNTOUCHED. | `Humanoid.cs:17` |
| 🛡️ `VERIFIED SAFE` | **`AdventureBackpacks`** | `InventoryGui.Update` | Class 'InventoryGui' was modified elsewhere, but method 'Update' is UNTOUCHED. | `InventoryGui.cs:272` |
| 🛡️ `VERIFIED SAFE` | **`AdventureBackpacks`** | `InventoryGui.SetupRequirement` | Class 'InventoryGui' was modified elsewhere, but method 'SetupRequirement' is UNTOUCHED. | `InventoryGui.cs:502` |
| 🛡️ `VERIFIED SAFE` | **`AdventureBackpacks`** | `Player.HaveRequirementItems` | Class 'Player' was modified elsewhere, but method 'HaveRequirementItems' is UNTOUCHED. | `Player.cs:93` |
| 🛡️ `VERIFIED SAFE` | **`AdventureBackpacks`** | `Player.ConsumeResources` | Class 'Player' was modified elsewhere, but method 'ConsumeResources' is UNTOUCHED. | `Player.cs:156` |
| 🟢 `SAFE` | **`NoFogBruh`** | `PostProcessingBehaviour.OnPreRender` | Class 'PostProcessingBehaviour' and method 'OnPreRender' are 100% UNCHANGED. | `DisableFogComponent.cs:297` |
| 🛡️ `VERIFIED SAFE` | **`Vapok.Common`** | `Inventory.FindFreeStackSpace` | Class 'Inventory' was modified elsewhere, but method 'FindFreeStackSpace' is UNTOUCHED. | `CustomDataManager.cs:680` |
| 🚨 `CRITICAL` | **`Vapok.Common`** | `Inventory.FindFreeStackItem` | Vanilla method 'Inventory.FindFreeStackItem' was MODIFIED! IL opcodes/offsets likely altered. | `CustomDataManager.cs:681` |
| 🟢 `SAFE` | **`Vapok.Common`** | `ItemDrop.AutoStackItems` | Class 'ItemDrop' and method 'AutoStackItems' are 100% UNCHANGED. | `CustomDataManager.cs:683` |
| 🛡️ `VERIFIED SAFE` | **`Vapok.Common`** | `InventoryGui.DoCrafting` | Class 'InventoryGui' was modified elsewhere, but method 'DoCrafting' is UNTOUCHED. | `CustomDataManager.cs:685` |
| 🟢 `SAFE` | **`Vapok.Common`** | `ItemDrop.Awake` | Class 'ItemDrop' and method 'Awake' are 100% UNCHANGED. | `CustomDataManager.cs:695` |
| 🛡️ `VERIFIED SAFE` | **`Vapok.Common`** | `InventoryGui.UpdateRecipe` | Class 'InventoryGui' was modified elsewhere, but method 'UpdateRecipe' is UNTOUCHED. | `ItemManager.cs:1848` |
| 🛡️ `VERIFIED SAFE` | **`Vapok.Common`** | `InventoryGui.SetupRequirementList` | Class 'InventoryGui' was modified elsewhere, but method 'SetupRequirementList' is UNTOUCHED. | `ItemManager.cs:1849` |
| 🟢 `SAFE` | **`Vapok.Common`** | `PieceTable.UpdateAvailable` | Class 'PieceTable' and method 'UpdateAvailable' are 100% UNCHANGED. | `PieceManager.cs:1096` |
| 🟢 `SAFE` | **`XPortalNetworks`** | `TeleportWorld.UpdatePortal` | Class 'TeleportWorld' and method 'UpdatePortal' are 100% UNCHANGED. | `TeleportWorld.cs:87` |

## 🎯 Mod Impact Assessment

Scans all workspace mod projects for Harmony patches, transpilers, and references against modified game classes.

| Mod Project | Risk Level | Direct Patches on Changed Methods | Patches on Modified Classes | Touched Game Classes |
| :--- | :---: | :--- | :--- | :--- |
| **`AdventureBackpacks`** | 🟡 MEDIUM | *None* | `InventoryGui.OnRightClickItem`<br>`Humanoid.UseItem`<br>`InventoryGrid.UpdateGui`<br>`SEMan.RemoveStatusEffect`<br>`FejdStartup.Start`<br>`Humanoid.UpdateEquipmentStatusEffects`<br>`Humanoid.UnequipItem`<br>`Humanoid.EquipItem`<br>`Inventory.Changed`<br>`InventoryGui.OnDropOutside`<br>`Humanoid.DropItem`<br>`Inventory.RemoveItem`<br>`Inventory.RemoveItem`<br>`Inventory.RemoveOneItem`<br>`Inventory.AddItem`<br>`Inventory.AddItem`<br>`InventoryGrid.DropItem`<br>`Inventory.MoveAll`<br>`Inventory.MoveItemToThis`<br>`Inventory.MoveItemToThis`<br>`Inventory.UpdateTotalWeight`<br>`Inventory.IsTeleportable`<br>`InventoryGui.DoCrafting`<br>`InventoryGui.OnSelectedItem`<br>`InventoryGui.Update`<br>`InventoryGui.SetupRequirement`<br>`Player.Awake`<br>`Player.HaveRequirementItems`<br>`Player.ConsumeResources` | `FejdStartup`, `Humanoid`, `Inventory`, `InventoryGrid`, `InventoryGui`, `Piece`, `Player`, `SEMan`, `Version`, `ZInput` |
| **`AutoFeedRedux`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake` | `FejdStartup`, `Humanoid`, `Player`, `Version` |
| **`BetterSleepBruh`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake`<br>`ZNet.UpdateNetTime` | `FejdStartup`, `Minimap`, `Player`, `Terminal`, `Version`, `ZNet` |
| **`ConsoleBuddy`** | 🟡 MEDIUM | *None* | `Terminal.AddString`<br>`FejdStartup.Awake` | `FejdStartup`, `Terminal`, `Version` |
| **`DoorOpenerBruh`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake`<br>`Player.SetLocalPlayer` | `FejdStartup`, `Piece`, `Player`, `Version` |
| **`FastItemTransfer`** | 🟡 MEDIUM | *None* | `InventoryGui.OnRightClickItem`<br>`Humanoid.UseItem`<br>`FejdStartup.Awake` | `FejdStartup`, `Humanoid`, `Inventory`, `InventoryGrid`, `InventoryGui`, `Player`, `Version` |
| **`NoFogBruh`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake` | `FejdStartup`, `Version` |
| **`RandomSpawnPointBruh`** | 🟢 LOW | *None* | *None* | `Player`, `Version` |
| **`ShieldMeBruh`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake`<br>`InventoryGui.Show`<br>`Player.SetLocalPlayer`<br>`Player.OnDeath`<br>`Humanoid.EquipItem`<br>`Humanoid.UnequipItem`<br>`InventoryGrid.UpdateGui`<br>`Inventory.MoveItemToThis`<br>`Inventory.MoveItemToThis`<br>`Inventory.RemoveItem`<br>`InventoryGrid.DropItem` | `FejdStartup`, `Humanoid`, `Inventory`, `InventoryGrid`, `InventoryGui`, `Player`, `Version` |
| **`TheQueensDeadBruh`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake` | `FejdStartup`, `Version` |
| **`Vapok.Common`** | 🟡 MEDIUM | *None* | `ZNet.OnNewConnection` | `Attack`, `Character`, `FejdStartup`, `Inventory`, `InventoryGui`, `Minimap`, `Piece`, `Player`, `Terminal`, `Version`, `ZNet` |
| **`XPortalNetworks`** | 🟡 MEDIUM | *None* | `Piece.SetCreator`<br>`Piece.CanBeRemoved`<br>`Player.PlacePiece`<br>`ZNet.RPC_PeerInfo` | `Minimap`, `Piece`, `Player`, `Version`, `ZInput`, `ZNet` |

## 📦 Assemblies Overview

| Assembly | Modified | Added | Deleted | Line Changes |
| :--- | :--- | :--- | :--- | :--- |
| `Assembly-CSharp.dll` | `0` | `0` | `0` | *No Changes* |
| `assembly_googleanalytics.dll` | `0` | `0` | `0` | *No Changes* |
| `assembly_guiutils.dll` | `0` | `0` | `0` | *No Changes* |
| `assembly_lux.dll` | `0` | `0` | `0` | *No Changes* |
| `assembly_postprocessing.dll` | `0` | `0` | `0` | *No Changes* |
| `assembly_simplemeshcombine.dll` | `0` | `0` | `0` | *No Changes* |
| `assembly_sunshafts.dll` | `0` | `0` | `0` | *No Changes* |
| [`assembly_utils.dll`](#assembly_utils) | `1` | `0` | `0` | `+97` / `-53` |
| [`assembly_valheim.dll`](#assembly_valheim) | `31` | `0` | `0` | `+315` / `-234` |

---

## 🔧 Assembly: `assembly_utils.dll` <a id="assembly_utils"></a>

**Changes Summary:** `1` modified, `0` added, `0` deleted (`+97` / `-53` lines)

| Status | Class / File | Changed Scope / Signatures | Diff |
| :---: | :--- | :--- | :---: |
| 🟡 `MOD` | `ZInput.cs` | `private Vector2 ApplyDeadzoneVector(Vector2 value)`<br>`private Vector2 ApplyDeadzoneVector(Vector2 value, bool smooth)`<br>`private float ApplyDeadzoneFloat(float value)`<br>`private float ApplyDeadzoneFloat(float value, bool smooth)`<br>`private void ApplyDeadzoneToMagnitude(ref float magnitude)`<br>*...and 15 more* | [View Diff](#assembly_utils_zinput_cs) |

### Detailed Diffs: `assembly_utils.dll`

#### 📄 `ZInput.cs` (🟡 MODIFIED `+97/-53`) <a id="assembly_utils_zinput_cs"></a>
*([⬆ Back to `assembly_utils.dll` summary](#assembly_utils))*

**Identified Changes / Methods:**
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

---

## 🔧 Assembly: `assembly_valheim.dll` <a id="assembly_valheim"></a>

**Changes Summary:** `31` modified, `0` added, `0` deleted (`+315` / `-234` lines)

| Status | Class / File | Changed Scope / Signatures | Diff |
| :---: | :--- | :--- | :---: |
| 🟡 `MOD` | `Achievements.cs` | *Class level change* | [View Diff](#assembly_valheim_achievements_cs) |
| 🟡 `MOD` | `AltBiomeWorldData.cs` | *Class level change* | [View Diff](#assembly_valheim_altbiomeworlddata_cs) |
| 🟡 `MOD` | `Attack.cs` | *Class level change* | [View Diff](#assembly_valheim_attack_cs) |
| 🟡 `MOD` | `Character.cs` | *Class level change* | [View Diff](#assembly_valheim_character_cs) |
| 🟡 `MOD` | `CinematicsManager.cs` | *Class level change* | [View Diff](#assembly_valheim_cinematicsmanager_cs) |
| 🟡 `MOD` | `FejdStartup.cs` | `private IEnumerator PlayIntroCinematic()`<br>`private IEnumerator TryPlayIntroCinematic()` | [View Diff](#assembly_valheim_fejdstartup_cs) |
| 🟡 `MOD` | `GameCamera.cs` | *Class level change* | [View Diff](#assembly_valheim_gamecamera_cs) |
| 🟡 `MOD` | `GraphicsSettingsManager.cs` | `private static void ApplyShaderKeywords(in GraphicsSettingsState settings)`<br>`private void ApplyTesselation(in GraphicsSettingsState settings)` | [View Diff](#assembly_valheim_graphicssettingsmanager_cs) |
| 🟡 `MOD` | `GrapplingPoint.cs` | *Class level change* | [View Diff](#assembly_valheim_grapplingpoint_cs) |
| 🟡 `MOD` | `Humanoid.cs` | *Class level change* | [View Diff](#assembly_valheim_humanoid_cs) |
| 🟡 `MOD` | `Inventory.cs` | *Class level change* | [View Diff](#assembly_valheim_inventory_cs) |
| 🟡 `MOD` | `InventoryGrid.cs` | *Class level change* | [View Diff](#assembly_valheim_inventorygrid_cs) |
| 🟡 `MOD` | `InventoryGui.cs` | *Class level change* | [View Diff](#assembly_valheim_inventorygui_cs) |
| 🟡 `MOD` | `Leviathan.cs` | *Class level change* | [View Diff](#assembly_valheim_leviathan_cs) |
| 🟡 `MOD` | `Minimap.cs` | *Class level change* | [View Diff](#assembly_valheim_minimap_cs) |
| 🟡 `MOD` | `Piece.cs` | `public static void CheckLenientBuildAchUnlocked(Achievement buildAchievement, bool afterLocalPlayerExists, bool useTagStats)`<br>`public static void CheckLenientBuildAchUnlocked(Achievement buildAchievement, bool showPopup, bool useTagStats)` | [View Diff](#assembly_valheim_piece_cs) |
| 🟡 `MOD` | `Player.cs` | *Class level change* | [View Diff](#assembly_valheim_player_cs) |
| 🟡 `MOD` | `PlayerController.cs` | *Class level change* | [View Diff](#assembly_valheim_playercontroller_cs) |
| 🟡 `MOD` | `PresentManager.cs` | `public void RequestTargetFrameRate(int targetFrameRate, int targetRefreshRate)`<br>`public void RequestTargetFrameRate(int value)` | [View Diff](#assembly_valheim_presentmanager_cs) |
| 🟡 `MOD` | `Projectile.cs` | *Class level change* | [View Diff](#assembly_valheim_projectile_cs) |
| 🟡 `MOD` | `ReportUser.cs` | *Class level change* | [View Diff](#assembly_valheim_reportuser_cs) |
| 🟡 `MOD` | `SEMan.cs` | *Class level change* | [View Diff](#assembly_valheim_seman_cs) |
| 🟡 `MOD` | `StaticRotation.cs` | *Class level change* | [View Diff](#assembly_valheim_staticrotation_cs) |
| 🟡 `MOD` | `Terminal.cs` | *Class level change* | [View Diff](#assembly_valheim_terminal_cs) |
| 🟡 `MOD` | `TerrainComp.cs` | `private TerrainComp GetNeighbor(Vector3 worldPos, int x, int y, float radius)`<br>`private TerrainComp TryGetNeighbor(Vector3 worldPos, int x, int y, float radius)` | [View Diff](#assembly_valheim_terraincomp_cs) |
| 🟡 `MOD` | `Valheim.SettingsGui/AccessibilitySettings.cs` | *Class level change* | [View Diff](#assembly_valheim_valheim_settingsgui_accessibilitysettings_cs) |
| 🟡 `MOD` | `Valheim.SettingsGui/GamepadSettings.cs` | *Class level change* | [View Diff](#assembly_valheim_valheim_settingsgui_gamepadsettings_cs) |
| 🟡 `MOD` | `Valheim.SettingsGui/GameplaySettings.cs` | *Class level change* | [View Diff](#assembly_valheim_valheim_settingsgui_gameplaysettings_cs) |
| 🟡 `MOD` | `Valheim.SettingsGui/KeyboardMouseSettings.cs` | `public void SetConsoleEnabled(bool enabled)` | [View Diff](#assembly_valheim_valheim_settingsgui_keyboardmousesettings_cs) |
| 🟡 `MOD` | `Version.cs` | *Class level change* | [View Diff](#assembly_valheim_version_cs) |
| 🟡 `MOD` | `ZNet.cs` | *Class level change* | [View Diff](#assembly_valheim_znet_cs) |

### Detailed Diffs: `assembly_valheim.dll`

#### 📄 `Achievements.cs` (🟡 MODIFIED `+1/-1`) <a id="assembly_valheim_achievements_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/Achievements.cs
+++ b/Achievements.cs
@@ -484,7 +484,7 @@
 				}
 				if (achievement.m_lenientBuildAchievement)
 				{
-					Piece.CheckLenientBuildAchUnlocked(achievement, showPopup: false, useTagStats: false);
+					Piece.CheckLenientBuildAchUnlocked(achievement, afterLocalPlayerExists: false, useTagStats: false);
 				}
 				if (achievement.CheckUnlocked())
 				{
```

#### 📄 `AltBiomeWorldData.cs` (🟡 MODIFIED `+2/-6`) <a id="assembly_valheim_altbiomeworlddata_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/AltBiomeWorldData.cs
+++ b/AltBiomeWorldData.cs
@@ -71,12 +71,8 @@
 
 	public static void VerifyBiomeData(World world)
 	{
-		TryLoadCache(world);
-		if (world.m_biomeData == null || Version.World.DeepNorth != world.m_worldVersion)
-		{
-			GenerateBiomePoints(world);
-			world.m_biomeData.SaveCache();
-		}
+		RemoveCache(world.m_name);
+		GenerateBiomePoints(world);
 		world.m_biomeData.GenerateSectors();
 	}
 
```

#### 📄 `Attack.cs` (🟡 MODIFIED `+18/-4`) <a id="assembly_valheim_attack_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/Attack.cs
+++ b/Attack.cs
@@ -429,10 +429,24 @@
 		{
 			m_zanim.SetTrigger(text = m_attackAnimation);
 		}
-		if (character.IsPlayer() && m_attackType != AttackType.None && m_currentAttackCainLevel == 0 && (Player.m_localPlayer == null || !Player.m_localPlayer.AttackTowardsPlayerLookDir || m_attackType == AttackType.Projectile))
-		{
-			character.transform.rotation = character.GetLookYaw();
-			m_body.rotation = character.transform.rotation;
+		if (character.IsPlayer() && m_attackType != AttackType.None && m_currentAttackCainLevel == 0)
+		{
+			bool num2 = Player.m_localPlayer == null || !Player.m_localPlayer.AttackTowardsPlayerLookDir;
+			bool flag = Player.m_localPlayer == null || Player.m_localPlayer.AttackTowardsPlayerLookDir;
+			if (num2 || m_attackType == AttackType.Projectile)
+			{
+				character.transform.rotation = character.GetLookYaw();
+				m_body.rotation = character.transform.rotation;
+			}
+			else if (flag)
+			{
+				Vector3 moveDir = character.GetMoveDir();
+				if (moveDir.sqrMagnitude > 0f)
+				{
+					character.transform.rotation = Quaternion.LookRotation(moveDir);
+					m_body.rotation = character.transform.rotation;
+				}
+			}
 		}
 		weapon.m_lastAttackTime = Time.time;
 		m_animEvent.ResetChain();
```

#### 📄 `Character.cs` (🟡 MODIFIED `+34/-30`) <a id="assembly_valheim_character_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/Character.cs
+++ b/Character.cs
@@ -1022,17 +1022,18 @@
 	private void UpdateHeatEffects(float dt)
 	{
 		bool flag = false;
+		float num = Mathf.Max(m_ashlandsOceanHeatLevel, m_lavaHeatLevel);
 		if (!(Player.m_localPlayer == this))
 		{
 			return;
 		}
-		GameCamera.instance.m_heatDistortImageEffect.enabled = m_lavaHeatLevel > 0f;
-		GameCamera.instance.m_heatDistortImageEffect.m_intensity = (flag ? 0f : m_lavaHeatLevel);
+		GameCamera.instance.m_heatDistortImageEffect.enabled = num > 0f;
+		GameCamera.instance.m_heatDistortImageEffect.m_intensity = (flag ? 0f : num);
 		if (!m_lavaHeatEffects.HasEffects())
 		{
 			return;
 		}
-		if (m_lavaHeatLevel > 0f && m_lavaHeatParticles.Count == 0 && !IsDead())
+		if (num > 0f && m_lavaHeatParticles.Count == 0 && !IsDead())
 		{
 			GameObject[] array = m_lavaHeatEffects.Create(base.transform.position, Quaternion.identity, base.transform);
 			foreach (KeyValuePair<ParticleSystem, float> lavaHeatParticle in m_lavaHeatParticles)
@@ -1064,7 +1065,7 @@
 		{
 			if (lavaHeatParticle2.Key != null)
 			{
-				lavaHeatParticle2.Key.emissionRate = m_lavaHeatLevel * lavaHeatParticle2.Value;
+				lavaHeatParticle2.Key.emissionRate = num * lavaHeatParticle2.Value;
 			}
 		}
 		if (Player.m_localPlayer == this)
@@ -1073,7 +1074,7 @@
 			{
 				if (item3 != null)
 				{
-					item3.SetVolumeModifier(IsDead() ? 0f : m_lavaHeatLevel);
+					item3.SetVolumeModifier(IsDead() ? 0f : num);
 				}
 			}
 		}
@@ -1156,23 +1157,31 @@
 
 	private void UpdateAshlandsWater(float dt)
 	{
-		if (m_tolerateFire || !InWater())
-		{
-			return;
-		}
-		float num = WorldGenerator.GetAshlandsOceanGradient(base.transform.position);
-		if (!IsSwimming())
-		{
-			num *= m_heatWaterTouchMultiplier;
-		}
-		if (!(num < 0f))
-		{
-			num = Mathf.Clamp01(num);
-			float num2 = 1f - GetEquipmentHeatResistanceModifier();
-			m_ashlandsOceanHeatLevel += num * dt * m_heatBuildupWater * num2;
-			if (m_ashlandsOceanHeatLevel > m_heatLevelFirstDamageThreshold)
-			{
-				m_ashlandsOceanHeatLevel = m_heatLevelFirstDamageThreshold;
+		if (!InWater())
+		{
+			m_ashlandsOceanHeatLevel -= dt * m_heatCooldownBase;
+			m_ashlandsOceanHeatLevel = Mathf.Clamp01(m_ashlandsOceanHeatLevel);
+		}
+		else
+		{
+			if (m_tolerateFire)
+			{
+				return;
+			}
+			float num = WorldGenerator.GetAshlandsOceanGradient(base.transform.position);
+			if (!IsSwimming())
+			{
+				num *= m_heatWaterTouchMultiplier;
+			}
+			if (!(num < 0f))
+			{
+				num = Mathf.Clamp01(num);
+				float num2 = 1f - GetEquipmentHeatResistanceModifier();
+				m_ashlandsOceanHeatLevel += num * dt * m_heatBuildupWater * num2;
+				if (m_ashlandsOceanHeatLevel > m_heatLevelFirstDamageThreshold)
+				{
+					m_ashlandsOceanHeatLevel = m_heatLevelFirstDamageThreshold;
+				}
 			}
 		}
 	}
@@ -2437,14 +2446,9 @@
 			DamageText.instance.ShowText(mod, hit.m_point, totalDamage, IsPlayer() || IsTamed());
 		}
 		Character attacker = hit.GetAttacker();
-		if (attacker != null)
-		{
-			bool num = attacker is Player player && (player.GetInventory().CheatedDamagingItemEquipped() || player.IsDebugFlying() || player.InGodMode() || player.InGhostMode());
-			bool flag = attacker.m_nview.GetZDO().GetBool(ZDOVars.s_cheated);
-			if (((num | flag) || (hit != null && hit.m_damage.GetTotalDamage() > 99999f)) && !PlayerProfile.s_bypassCheatChecks)
-			{
-				m_nview.GetZDO().Set(ZDOVars.s_cheated, value: true);
-			}
+		if (attacker != null && attacker.IsPlayer() && !IsPlayer() && attacker is Player player && (player.GetInventory().CheatedDamagingItemEquipped() || player.IsDebugFlying() || player.InGodMode() || player.InGhostMode()) && !PlayerProfile.s_bypassCheatChecks)
+		{
+			m_nview.GetZDO().Set(ZDOVars.s_cheated, value: true);
 		}
 		float health = GetHealth();
 		if (health > 0f)
```

#### 📄 `CinematicsManager.cs` (🟡 MODIFIED `+2/-0`) <a id="assembly_valheim_cinematicsmanager_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/CinematicsManager.cs
+++ b/CinematicsManager.cs
@@ -63,6 +63,8 @@
 
 	public static List<GameObject> m_hiders = new List<GameObject>();
 
+	public static bool m_allUnlocked = false;
+
 	private static List<GameObject> m_hidden = new List<GameObject>();
 
 	private static bool m_playing;
```

#### 📄 `FejdStartup.cs` (🟡 MODIFIED `+12/-7`) <a id="assembly_valheim_fejdstartup_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

**Identified Changes / Methods:**
- `private IEnumerator PlayIntroCinematic()`
- `private IEnumerator TryPlayIntroCinematic()`

```diff
--- a/FejdStartup.cs
+++ b/FejdStartup.cs
@@ -16,7 +16,7 @@
 {
 	private delegate void ContinueAction();
 
-	private bool m_cinematicsInitialized;
+	public bool m_cinematicsInitialized;
 
 	private Vector3 camSpeed = Vector3.zero;
 
@@ -464,11 +464,16 @@
 		}
 		CheckShowChangelogNotice();
 		Player.m_debugMode = false;
-		StartCoroutine(PlayIntroCinematic());
-	}
-
-	private IEnumerator PlayIntroCinematic()
-	{
+		StartCoroutine(TryPlayIntroCinematic());
+	}
+
+	private IEnumerator TryPlayIntroCinematic()
+	{
+		if (PlatformPrefs.GetBool("SkipIntroCinematic"))
+		{
+			m_menuAnimator.SetTrigger("FadeIn");
+			yield break;
+		}
 		m_mainMenu.SetActive(value: false);
 		if (m_queuedJoinServer != ServerJoinData.None || MatchmakingManager.HasPendingInvite())
 		{
@@ -1967,7 +1972,7 @@
 				{
 					continue;
 				}
-				if (Terminal.m_cheat)
+				if (CinematicsManager.m_allUnlocked)
 				{
 					video.m_unlocked = true;
 				}
```

#### 📄 `GameCamera.cs` (🟡 MODIFIED `+4/-2`) <a id="assembly_valheim_gamecamera_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

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

#### 📄 `GraphicsSettingsManager.cs` (🟡 MODIFIED `+12/-4`) <a id="assembly_valheim_graphicssettingsmanager_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

**Identified Changes / Methods:**
- `private static void ApplyShaderKeywords(in GraphicsSettingsState settings)`
- `private void ApplyTesselation(in GraphicsSettingsState settings)`

```diff
--- a/GraphicsSettingsManager.cs
+++ b/GraphicsSettingsManager.cs
@@ -56,6 +56,9 @@
 	[SerializeField]
 	private GlobalGraphicsConfiguration m_globalConfig;
 
+	[SerializeField]
+	private Shader[] m_tesselationShaders = new Shader[0];
+
 	private PresentManager m_presentManager = new PresentManager();
 
 	private SoftReference<GraphicsConfiguration> m_config;
@@ -199,7 +202,7 @@
 		UnityEngine.Object.DontDestroyOnLoad(base.gameObject);
 		s_instance = this;
 		m_presentManager.Initialize();
-		m_presentManager.RequestTargetFrameRate(60);
+		m_presentManager.RequestTargetFrameRate(60, 60);
 		m_presentManager.TargetFrameRateChanged += ApplyGraphicsSettingsToCurrentSession;
 		m_presentManager.ResolutionChanged += ApplyGraphicsSettingsToCurrentSession;
 		if (PlatformManager.DistributionPlatform != null)
@@ -375,7 +378,7 @@
 			RequestTargetFrameRateFromPreset();
 			m_activeSettings = GetCurrentSettingsWithCurrentPresetApplied(includeBackground: true, out var _);
 			ApplyTargetResolutionSetting(ScaleTarget3DResolutionByCurrentRenderingArea(m_activeSettings.m_target3DResolutionVertical), m_activeSettings.m_upscalingAlgorithm);
-			ApplyShaderKeywords(in m_activeSettings);
+			ApplyTesselation(in m_activeSettings);
 			ApplyQualitySettings(in m_activeSettings);
 			ApplyLightLod(in m_activeSettings);
 			GraphicsSettingsChanged?.Invoke();
@@ -385,8 +388,9 @@
 	private void RequestTargetFrameRateFromPreset()
 	{
 		GraphicsSettingsState currentSettingsWithCurrentPresetApplied = GetCurrentSettingsWithCurrentPresetApplied(includeBackground: true, forceSelected: true);
+		GraphicsSettingsState currentSettingsWithCurrentPresetApplied2 = GetCurrentSettingsWithCurrentPresetApplied(includeBackground: false, forceSelected: true);
 		int fpsLimit = currentSettingsWithCurrentPresetApplied.m_presentSettings.m_fpsLimit;
-		m_presentManager.RequestTargetFrameRate(fpsLimit);
+		m_presentManager.RequestTargetFrameRate(fpsLimit, currentSettingsWithCurrentPresetApplied2.m_presentSettings.m_fpsLimit);
 		m_presentManager.SetVSyncEnabled(currentSettingsWithCurrentPresetApplied.m_presentSettings.m_vsync);
 	}
 
@@ -661,7 +665,7 @@
 		LightLod.m_shadowLimit = GetPointLightShadowLimit(settings.m_pointLightShadows);
 	}
 
-	private static void ApplyShaderKeywords(in GraphicsSettingsState settings)
+	private void ApplyTesselation(in GraphicsSettingsState settings)
 	{
 		if (settings.m_tesselation)
 		{
@@ -671,5 +675,9 @@
 		{
 			Shader.DisableKeyword("TESSELATION_ON");
 		}
+		for (int i = 0; i < m_tesselationShaders.Length; i++)
+		{
+			m_tesselationShaders[i].maximumLOD = (settings.m_tesselation ? 250 : 200);
+		}
 	}
 }
```

#### 📄 `GrapplingPoint.cs` (🟡 MODIFIED `+17/-8`) <a id="assembly_valheim_grapplingpoint_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

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

#### 📄 `Humanoid.cs` (🟡 MODIFIED `+1/-1`) <a id="assembly_valheim_humanoid_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/Humanoid.cs
+++ b/Humanoid.cs
@@ -712,7 +712,7 @@
 					outofRangeWeapons.Add(item);
 					continue;
 				}
-				if (item.m_shared.m_aiPrioritizedIfAngleCheckValid && m_baseAI.IsLookingAt(targetCreature.transform.position, item.m_shared.m_aiAttackMaxAngle, item.m_shared.m_aiInvertAngleCheck))
+				if ((bool)targetCreature && item.m_shared.m_aiPrioritizedIfAngleCheckValid && m_baseAI.IsLookingAt(targetCreature.transform.position, item.m_shared.m_aiAttackMaxAngle, item.m_shared.m_aiInvertAngleCheck))
 				{
 					EquipItem(item);
 					return;
```

#### 📄 `Inventory.cs` (🟡 MODIFIED `+11/-15`) <a id="assembly_valheim_inventory_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/Inventory.cs
+++ b/Inventory.cs
@@ -117,14 +117,10 @@
 		{
 			for (int i = 0; i < item.m_stack; i++)
 			{
-				ItemDrop.ItemData itemData = FindFreeStackItem(item.m_shared.m_name, item.m_quality, item.m_worldLevel);
+				ItemDrop.ItemData itemData = FindFreeStackItem(item.m_shared.m_name, item.m_quality, item.m_worldLevel, item.m_cheated);
 				if (itemData != null)
 				{
 					itemData.m_stack++;
-					if (item.m_cheated && !PlayerProfile.s_bypassCheatChecks)
-					{
-						itemData.m_cheated = true;
-					}
 					continue;
 				}
 				int stack = item.m_stack - i;
@@ -138,7 +134,7 @@
 				else
 				{
 					flag = false;
-					ZLog.LogError($"Trying to add item to occupied slot {gridPos.x}, {gridPos.y}");
+					ZLog.LogWarning($"Trying to add item to occupied slot {gridPos.x}, {gridPos.y}");
 				}
 				break;
 			}
@@ -154,7 +150,7 @@
 			else
 			{
 				flag = false;
-				ZLog.LogError($"Trying to add item to occupied slot {gridPos2.x}, {gridPos2.y}");
+				ZLog.LogWarning($"Trying to add item to occupied slot {gridPos2.x}, {gridPos2.y}");
 			}
 		}
 		Changed(flag, cheatedStateChanged);
@@ -169,7 +165,7 @@
 		{
 			for (int i = 0; i < item.m_stack; i++)
 			{
-				ItemDrop.ItemData itemData = FindFreeStackItem(item.m_shared.m_name, item.m_quality, item.m_worldLevel);
+				ItemDrop.ItemData itemData = FindFreeStackItem(item.m_shared.m_name, item.m_quality, item.m_worldLevel, item.m_cheated);
 				if (itemData != null)
 				{
 					itemData.m_stack++;
@@ -185,7 +181,7 @@
 				else
 				{
 					flag = false;
-					ZLog.LogError($"Trying to add item to occupied slot {pos.x}, {pos.y}");
+					ZLog.LogWarning($"Trying to add item to occupied slot {pos.x}, {pos.y}");
 				}
 				break;
 			}
@@ -198,7 +194,7 @@
 		else
 		{
 			flag = false;
-			ZLog.LogError($"Trying to add item to occupied slot {pos.x}, {pos.y}");
+			ZLog.LogWarning($"Trying to add item to occupied slot {pos.x}, {pos.y}");
 		}
 		Changed(flag, cheatedStateChanged);
 		return flag;
@@ -544,11 +540,11 @@
 		return num;
 	}
 
-	private ItemDrop.ItemData FindFreeStackItem(string name, int quality, float worldLevel)
-	{
-		foreach (ItemDrop.ItemData item in m_inventory)
-		{
-			if (item.m_shared.m_name == name && item.m_quality == quality && item.m_stack < item.m_shared.m_maxStackSize && (float)item.m_worldLevel == worldLevel)
+	private ItemDrop.ItemData FindFreeStackItem(string name, int quality, float worldLevel, bool cheated)
+	{
+		foreach (ItemDrop.ItemData item in m_inventory)
+		{
+			if (item.m_shared.m_name == name && item.m_quality == quality && item.m_stack < item.m_shared.m_maxStackSize && (float)item.m_worldLevel == worldLevel && item.m_cheated == cheated)
 			{
 				return item;
 			}
```

#### 📄 `InventoryGrid.cs` (🟡 MODIFIED `+1/-1`) <a id="assembly_valheim_inventorygrid_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/InventoryGrid.cs
+++ b/InventoryGrid.cs
@@ -576,7 +576,7 @@
 		{
 			return true;
 		}
-		if (itemAt != null && (itemAt.m_shared.m_name != item.m_shared.m_name || (item.m_shared.m_maxQuality > 1 && itemAt.m_quality != item.m_quality) || itemAt.m_shared.m_maxStackSize == 1) && item.m_stack == amount)
+		if (itemAt != null && (itemAt.m_shared.m_name != item.m_shared.m_name || (item.m_shared.m_maxQuality > 1 && itemAt.m_quality != item.m_quality) || itemAt.m_shared.m_maxStackSize == 1 || itemAt.m_cheated != item.m_cheated) && item.m_stack == amount)
 		{
 			fromInventory.RemoveItem(item);
 			fromInventory.MoveItemToThis(m_inventory, itemAt, itemAt.m_stack, item.m_gridPos.x, item.m_gridPos.y);
```

#### 📄 `InventoryGui.cs` (🟡 MODIFIED `+3/-3`) <a id="assembly_valheim_inventorygui_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/InventoryGui.cs
+++ b/InventoryGui.cs
@@ -479,9 +479,9 @@
 
 	private bool CanDropDragOntoItem(ItemDrop.ItemData item)
 	{
-		if (item.IsSameType(m_dragItem))
-		{
-			return item.GetSpaceLeftInStack() > 0;
+		if (item.IsSameType(m_dragItem) && item.GetSpaceLeftInStack() > 0)
+		{
+			return item.m_cheated == m_dragItem.m_cheated;
 		}
 		return false;
 	}
```

#### 📄 `Leviathan.cs` (🟡 MODIFIED `+2/-2`) <a id="assembly_valheim_leviathan_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/Leviathan.cs
+++ b/Leviathan.cs
@@ -48,10 +48,10 @@
 			MineRock mineRock = m_mineRock;
 			mineRock.m_onHit = (Action)Delegate.Combine(mineRock.m_onHit, new Action(OnHit));
 		}
-		if (m_nview.IsValid() && m_nview.IsOwner())
+		if (m_nview.IsValid())
 		{
 			m_nview.Register("RPC_Left", RPC_Left);
-			if (m_nview.GetZDO().GetBool(ZDOVars.s_dead))
+			if (m_nview.GetZDO().GetBool(ZDOVars.s_dead) && m_nview.IsOwner())
 			{
 				m_nview.Destroy();
 			}
```

#### 📄 `Minimap.cs` (🟡 MODIFIED `+1/-1`) <a id="assembly_valheim_minimap_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/Minimap.cs
+++ b/Minimap.cs
@@ -1149,7 +1149,7 @@
 			}
 			if (!m_nameInput.gameObject.activeSelf)
 			{
-				m_mapOffset.x += ZInput.GetJoyLeftStickX(smooth: true) * dt * 50000f * LargeZoom * m_gamepadMoveSpeed;
+				m_mapOffset.x += ZInput.GetJoyLeftStickX() * dt * 50000f * LargeZoom * m_gamepadMoveSpeed;
 				m_mapOffset.z -= ZInput.GetJoyLeftStickY() * dt * 50000f * LargeZoom * m_gamepadMoveSpeed;
 			}
 			if (m_dragView)
```

#### 📄 `Piece.cs` (🟡 MODIFIED `+12/-15`) <a id="assembly_valheim_piece_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

**Identified Changes / Methods:**
- `public static void CheckLenientBuildAchUnlocked(Achievement buildAchievement, bool afterLocalPlayerExists, bool useTagStats)`
- `public static void CheckLenientBuildAchUnlocked(Achievement buildAchievement, bool showPopup, bool useTagStats)`

```diff
--- a/Piece.cs
+++ b/Piece.cs
@@ -558,27 +558,19 @@
 
 	private static void CheckBuildLeniencyUnlocks()
 	{
-		List<Achievement> list = new List<Achievement>();
 		foreach (AchievementList achievementList in Achievements.m_instance.m_achievementLists)
 		{
 			foreach (Achievement achievement in achievementList.m_achievements)
 			{
-				if (achievement.m_lenientBuildAchievement)
+				if (achievement.m_lenientBuildAchievement && !achievement.m_unlocked)
 				{
-					list.Add(achievement);
+					CheckLenientBuildAchUnlocked(achievement, afterLocalPlayerExists: true, useTagStats: true);
 				}
 			}
 		}
-		foreach (Achievement item in list)
-		{
-			if (!item.m_unlocked)
-			{
-				CheckLenientBuildAchUnlocked(item, showPopup: true, useTagStats: true);
-			}
-		}
-	}
-
-	public static void CheckLenientBuildAchUnlocked(Achievement buildAchievement, bool showPopup, bool useTagStats)
+	}
+
+	public static void CheckLenientBuildAchUnlocked(Achievement buildAchievement, bool afterLocalPlayerExists, bool useTagStats)
 	{
 		float num = 0f;
 		float[] array = new float[20];
@@ -611,10 +603,15 @@
 				num2 += num7;
 			}
 		}
-		if (num2 > num && Achievements.CanGetAchievements(Player.m_localPlayer != null && Player.m_localPlayer.NoCostCheat()))
+		bool flag = true;
+		if (afterLocalPlayerExists)
+		{
+			flag = Achievements.CanGetAchievements();
+		}
+		if ((num2 > num) & flag)
 		{
 			buildAchievement.m_unlocked = true;
-			Achievements.AchievementEvent(buildAchievement, synchronize: true, showPopup);
+			Achievements.AchievementEvent(buildAchievement, synchronize: true, afterLocalPlayerExists);
 		}
 	}
 
```

#### 📄 `Player.cs` (🟡 MODIFIED `+58/-54`) <a id="assembly_valheim_player_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/Player.cs
+++ b/Player.cs
@@ -455,6 +455,8 @@
 
 	private Dictionary<Material, float> m_ghostRippleDistance = new Dictionary<Material, float>();
 
+	private bool m_toggleBlock;
+
 	private bool m_attackTowardsPlayerLookDir;
 
 	public float m_blockReload;
@@ -621,6 +623,18 @@
 		set
 		{
 			m_attackTowardsPlayerLookDir = value;
+		}
+	}
+
+	public bool ToggleBlock
+	{
+		get
+		{
+			return m_toggleBlock;
+		}
+		set
+		{
+			m_toggleBlock = value;
 		}
 	}
 
@@ -687,6 +701,7 @@
 		AddQueuedKeys();
 		UpdateCurrentSeason();
 		m_attackTowardsPlayerLookDir = PlatformPrefs.GetInt("AttackTowardsPlayerLookDir", 1) == 1;
+		m_toggleBlock = PlayerPrefs.GetInt("ToggleBlock", 0) == 1;
 	}
 
 	protected override void OnEnable()
@@ -903,29 +918,29 @@
 			{
 				if (ZInput.GetButtonDown("Hide"))
 				{
-					goto IL_031d;
+					goto IL_0320;
 				}
 				if (flag3 && !ZInput.GetButton("JoyAltKeys"))
 				{
 					num = !InPlaceMode();
-					goto IL_031b;
+					goto IL_031e;
 				}
 			}
 			else if (!InPlaceMode() & flag3)
 			{
-				num = ZInput.GetButton("JoyAltKeys");
-				goto IL_031b;
-			}
-			goto IL_0368;
-		}
-		goto IL_052b;
-		IL_031b:
+				num = !ZInput.GetButton("JoyAltKeys");
+				goto IL_031e;
+			}
+			goto IL_036b;
+		}
+		goto IL_04de;
+		IL_031e:
 		if (num)
 		{
-			goto IL_031d;
-		}
-		goto IL_0368;
-		IL_052b:
+			goto IL_0320;
+		}
+		goto IL_036b;
+		IL_04de:
 		UpdateControllerTriggerFeedback(flag2);
 		UpdateGyro(flag2);
 		if (m_blockReload > 0f)
@@ -943,7 +958,7 @@
 		UpdatePlacement(flag2, Time.deltaTime);
 		UpdateStats();
 		return;
-		IL_031d:
+		IL_0320:
 		if (GetRightItem() != null || GetLeftItem() != null)
 		{
 			if (!InAttack() && !InDodge())
@@ -955,8 +970,8 @@
 		{
 			ShowHandItems();
 		}
-		goto IL_0368;
-		IL_0368:
+		goto IL_036b;
+		IL_036b:
 		if (ZInput.GetButtonDown("ToggleWalk") && !Hud.InRadial())
 		{
 			SetWalk(!GetWalk());
@@ -983,39 +998,14 @@
 			m_enableAutoPickup = !m_enableAutoPickup;
 			Message(MessageHud.MessageType.TopLeft, "$hud_autopickup:" + (m_enableAutoPickup ? "$hud_on" : "$hud_off"));
 		}
-		if (ZInput.GetButtonDown("Hotbar1"))
-		{
-			UseHotbarItem(1);
-		}
-		if (ZInput.GetButtonDown("Hotbar2"))
-		{
-			UseHotbarItem(2);
-		}
-		if (ZInput.GetButtonDown("Hotbar3"))
-		{
-			UseHotbarItem(3);
-		}
-		if (ZInput.GetButtonDown("Hotbar4"))
-		{
-			UseHotbarItem(4);
-		}
-		if (ZInput.GetButtonDown("Hotbar5"))
-		{
-			UseHotbarItem(5);
-		}
-		if (ZInput.GetButtonDown("Hotbar6"))
-		{
-			UseHotbarItem(6);
-		}
-		if (ZInput.GetButtonDown("Hotbar7"))
-		{
-			UseHotbarItem(7);
-		}
-		if (ZInput.GetButtonDown("Hotbar8"))
-		{
-			UseHotbarItem(8);
-		}
-		goto IL_052b;
+		for (int i = 1; i <= 8; i++)
+		{
+			if (ZInput.GetButtonDown($"Hotbar{i}") || ZInput.GetButtonDown($"Hotbar{i}Alt"))
+			{
+				UseHotbarItem(i);
+			}
+		}
+		goto IL_04de;
 	}
 
 	private void UpdateControllerTriggerFeedback(bool takeInput)
@@ -6646,6 +6636,7 @@
 			lookDir.Normalize();
 			m_moveDir = movedir.z * lookDir + movedir.x * Vector3.Cross(Vector3.up, lookDir);
 		}
+		bool flag = false;
 		if ((!m_autoRun & autoRun) && !InPlaceMode())
 		{
 			m_autoRun = true;
@@ -6665,23 +6656,36 @@
 				m_moveDir = m_lookDir;
 				m_moveDir.y = 0f;
 				m_moveDir.Normalize();
-				blockHold = false;
-				block = false;
+				flag = true;
 			}
 		}
 		m_attack = attack;
 		m_attackHold = attackHold;
 		m_secondaryAttack = secondaryAttack;
 		m_secondaryAttackHold = secondaryAttackHold;
-		m_blocking = blockHold;
 		m_run = run;
+		if (m_toggleBlock)
+		{
+			if (block)
+			{
+				m_blocking = !m_blocking;
+			}
+		}
+		else
+		{
+			m_blocking = blockHold;
+		}
+		if (flag)
+		{
+			m_blocking = false;
+		}
 		if (crouch)
 		{
 			SetCrouch(!m_crouchToggled);
 		}
 		if (ZInput.InputLayout == InputLayout.Default || !ZInput.IsGamepadActive())
 		{
-			if (!jump)
+			if (!(jump | dodge))
 			{
 				return;
 			}
@@ -6696,7 +6700,7 @@
 				}
 				Dodge(dodgeDir);
 			}
-			else if (IsCrouching() || m_crouchToggled)
+			else if ((IsCrouching() || m_crouchToggled) | dodge)
 			{
 				Vector3 dodgeDir2 = m_moveDir;
 				if (dodgeDir2.magnitude < 0.1f)
```

#### 📄 `PlayerController.cs` (🟡 MODIFIED `+16/-13`) <a id="assembly_valheim_playercontroller_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

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

#### 📄 `PresentManager.cs` (🟡 MODIFIED `+7/-4`) <a id="assembly_valheim_presentmanager_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

**Identified Changes / Methods:**
- `public void RequestTargetFrameRate(int targetFrameRate, int targetRefreshRate)`
- `public void RequestTargetFrameRate(int value)`

```diff
--- a/PresentManager.cs
+++ b/PresentManager.cs
@@ -25,6 +25,8 @@
 
 	private int m_requestedTargetFrameRate = -1;
 
+	private int m_requestedRefreshRate = -1;
+
 	private int m_targetFrameRate = -1;
 
 	private bool m_setVSyncEnabled;
@@ -67,9 +69,10 @@
 
 	public event Action ResolutionChanged;
 
-	public void RequestTargetFrameRate(int value)
-	{
-		m_requestedTargetFrameRate = ((value < 30 || value > 360) ? (-1) : value);
+	public void RequestTargetFrameRate(int targetFrameRate, int targetRefreshRate)
+	{
+		m_requestedTargetFrameRate = ((targetFrameRate < 30 || targetFrameRate > 360) ? (-1) : targetFrameRate);
+		m_requestedRefreshRate = ((targetRefreshRate < 30 || targetRefreshRate > 360) ? (-1) : targetRefreshRate);
 		UpdatePresentSettings();
 	}
 
@@ -273,7 +276,7 @@
 	{
 		if (!m_isComputer && !m_isXbox)
 		{
-			PresentRefreshRate presentRefreshRate = (((m_requestedTargetFrameRate <= 0 || !FrameRateIsSubmultipleOfRefreshRate((uint)m_requestedTargetFrameRate, s_hz59_94, 0.002f)) && IsSupportedRefreshRate(s_hz119_88)) ? s_hz119_88 : s_hz59_94);
+			PresentRefreshRate presentRefreshRate = (((m_requestedRefreshRate <= 0 || !FrameRateIsSubmultipleOfRefreshRate((uint)m_requestedRefreshRate, s_hz59_94, 0.002f)) && IsSupportedRefreshRate(s_hz119_88)) ? s_hz119_88 : s_hz59_94);
 			if (!m_currentDisplayRefreshRate.Equals(presentRefreshRate))
 			{
 				m_currentDisplayRefreshRate = presentRefreshRate;
```

#### 📄 `Projectile.cs` (🟡 MODIFIED `+5/-2`) <a id="assembly_valheim_projectile_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/Projectile.cs
+++ b/Projectile.cs
@@ -702,13 +702,16 @@
 		{
 			m_didHit = true;
 			base.transform.position = hitPoint;
-			m_nview.InvokeRPC("RPC_OnHit");
+			if (m_nview.IsValid())
+			{
+				m_nview.InvokeRPC("RPC_OnHit");
+			}
 			m_ttl = m_stayTTL;
 		}
 		if ((bool)collider && collider.attachedRigidbody != null)
 		{
 			ZNetView componentInParent = collider.gameObject.GetComponentInParent<ZNetView>();
-			if ((bool)componentInParent && (m_attachToClosestBone || m_attachToRigidBody))
+			if ((bool)componentInParent && componentInParent.IsValid() && (m_attachToClosestBone || m_attachToRigidBody))
 			{
 				m_nview.InvokeRPC("RPC_Attach", componentInParent.GetZDO().m_uid);
 			}
```

#### 📄 `ReportUser.cs` (🟡 MODIFIED `+19/-4`) <a id="assembly_valheim_reportuser_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/ReportUser.cs
+++ b/ReportUser.cs
@@ -173,16 +173,31 @@
 			MondayReportFailed(result.Error.Message);
 			return;
 		}
-		JObject jObject = JObject.Parse(JsonConvert.SerializeObject(result.FunctionResult));
+		string text = result.FunctionResult?.ToString();
+		if (string.IsNullOrEmpty(text))
+		{
+			MondayReportFailed("Invalid json returned!");
+			return;
+		}
+		JObject jObject;
+		try
+		{
+			jObject = JObject.Parse(text);
+		}
+		catch
+		{
+			MondayReportFailed("Invalid json returned!");
+			return;
+		}
 		if (!jObject.Value<bool>("success"))
 		{
-			string text = jObject.Value<string>("message");
-			ZLog.LogError("Monday request failed: " + text);
+			string text2 = jObject.Value<string>("message");
+			ZLog.LogError("Monday request failed: " + text2);
 			if (jObject["errors"] != null)
 			{
 				ZLog.Log(jObject["errors"].ToString());
 			}
-			MondayReportFailed(text);
+			MondayReportFailed(text2);
 		}
 		else
 		{
```

#### 📄 `SEMan.cs` (🟡 MODIFIED `+4/-0`) <a id="assembly_valheim_seman_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/SEMan.cs
+++ b/SEMan.cs
@@ -137,6 +137,10 @@
 	public StatusEffect AddStatusEffect(int nameHash, bool resetTime = false, int itemLevel = 0, float skillLevel = 0f, short variant = -1)
 	{
 		if (nameHash == 0)
+		{
+			return null;
+		}
+		if (!m_nview.IsValid())
 		{
 			return null;
 		}
```

#### 📄 `StaticRotation.cs` (🟡 MODIFIED `+8/-4`) <a id="assembly_valheim_staticrotation_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/StaticRotation.cs
+++ b/StaticRotation.cs
@@ -32,12 +32,16 @@
 			return;
 		}
 		ZDO zDO = m_nview.GetZDO();
-		if (zDO != null && zDO.IsValid())
+		if (zDO == null || !zDO.IsValid())
 		{
-			m_rotation = zDO.GetFloat(ZDOVars.s_tiltrot);
-			if (m_rotation == 0f)
+			return;
+		}
+		m_rotation = zDO.GetFloat(ZDOVars.s_tiltrot);
+		if (m_rotation == 0f)
+		{
+			m_rotation = base.transform.rotation.eulerAngles.y;
+			if (zDO.IsOwner())
 			{
-				m_rotation = base.transform.rotation.eulerAngles.y;
 				zDO.Set(ZDOVars.s_tiltrot, m_rotation);
 			}
 		}
```

#### 📄 `Terminal.cs` (🟡 MODIFIED `+13/-1`) <a id="assembly_valheim_terminal_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/Terminal.cs
+++ b/Terminal.cs
@@ -1926,6 +1926,18 @@
 			}
 			return list;
 		});
+		new ConsoleCommand("unlockcinematics", "toggles unlocking all cinematics in the main menu", delegate(ConsoleEventArgs args)
+		{
+			if (FejdStartup.instance != null && FejdStartup.instance.m_cinematicsInitialized)
+			{
+				args.Context.AddString("Can't reload unlocked cinematics while in main menu when they've already been loaded once, either enter world, retry command, and log out - or restart game and enter this command before entering the cinematics menu.");
+			}
+			else
+			{
+				CinematicsManager.m_allUnlocked = !CinematicsManager.m_allUnlocked;
+				args.Context.AddString($"All cinematics unlocked : {CinematicsManager.m_allUnlocked}");
+			}
+		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true);
 		new ConsoleCommand("inventorysize", "sets inventory size", delegate(ConsoleEventArgs args)
 		{
 			if (Player.m_localPlayer == null)
@@ -2153,7 +2165,7 @@
 					args.Context.AddString($"{item21.eventId}: {item21.internalName} | Position: {item21.position}");
 				}
 			}
-		});
+		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
 		new ConsoleCommand("tombstone", "[name] creates a tombstone with given name", delegate(ConsoleEventArgs args)
 		{
 			GameObject obj = UnityEngine.Object.Instantiate(Player.m_localPlayer.m_tombstone, Player.m_localPlayer.GetCenterPoint(), Player.m_localPlayer.transform.rotation);
```

#### 📄 `TerrainComp.cs` (🟡 MODIFIED `+20/-13`) <a id="assembly_valheim_terraincomp_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

**Identified Changes / Methods:**
- `private TerrainComp GetNeighbor(Vector3 worldPos, int x, int y, float radius)`
- `private TerrainComp TryGetNeighbor(Vector3 worldPos, int x, int y, float radius)`

```diff
--- a/TerrainComp.cs
+++ b/TerrainComp.cs
@@ -58,7 +58,14 @@
 		if ((bool)terrainComp)
 		{
 			ZLog.LogWarning("Found another terrain compiler in this area, removing it");
-			ZNetScene.instance.Destroy(terrainComp.gameObject);
+			if (m_nview.IsValid() && !m_nview.HasOwner())
+			{
+				m_nview.ClaimOwnership();
+			}
+			if (m_nview.IsOwner())
+			{
+				ZNetScene.instance.Destroy(terrainComp.gameObject);
+			}
 		}
 		s_instances.Add(this);
 		m_nview.Register<ZPackage>("RPC_ApplyOperation", RPC_ApplyOperation);
@@ -516,7 +523,7 @@
 				if ((bool)heightmap)
 				{
 					heightmap.WorldToVertexMask(worldPos, out var x2, out var y2);
-					color = getMask(heightmap, heightmap.GetAndCreateTerrainCompiler(), x2, y2, getIndex(x2, y2));
+					color = getMask(heightmap, FindTerrainCompiler(heightmap.transform.position), x2, y2, getIndex(x2, y2));
 				}
 			}
 			else
@@ -665,16 +672,16 @@
 					{
 						return false;
 					}
-					TerrainComp neighbor = GetNeighbor(worldPos, ox, oy, settings.m_paintRadius);
-					if (neighbor != null)
-					{
-						GetNearestVertex(neighbor, x3, y3, out var ox2, out var oy2);
+					TerrainComp terrainComp = TryGetNeighbor(worldPos, ox, oy, settings.m_paintRadius);
+					if (terrainComp != null)
+					{
+						GetNearestVertex(terrainComp, x3, y3, out var ox2, out var oy2);
 						int num13 = getIndex(ox2, oy2);
-						neighbor.m_modifiedPaint[num13] = true;
-						neighbor.m_paintMask[num13] = color2;
+						terrainComp.m_modifiedPaint[num13] = true;
+						terrainComp.m_paintMask[num13] = color2;
 						bool paintOnly = settings.m_paintCleared && !settings.m_level && !settings.m_raise && !settings.m_smooth;
-						neighbor.Save(paintOnly);
-						neighbor.m_hmap.Poke(1, paintOnly);
+						terrainComp.Save(paintOnly);
+						terrainComp.m_hmap.Poke(1, paintOnly);
 					}
 					return true;
 				}
@@ -696,7 +703,7 @@
 		}
 		static Color getMask(Heightmap hmap, TerrainComp tc, int x4, int y4, int index)
 		{
-			if (hmap.m_doLateUpdate != 1)
+			if (hmap.m_doLateUpdate != 1 || !(tc != null))
 			{
 				return hmap.GetPaintMask(x4, y4);
 			}
@@ -704,7 +711,7 @@
 		}
 	}
 
-	private TerrainComp GetNeighbor(Vector3 worldPos, int x, int y, float radius)
+	private TerrainComp TryGetNeighbor(Vector3 worldPos, int x, int y, float radius)
 	{
 		if (m_neighborGrid == null)
 		{
@@ -720,7 +727,7 @@
 				Vector3 position2 = neighbor.transform.position;
 				int num = ((!(position2.x < position.x)) ? ((!(position2.x > position.x)) ? 1 : 2) : 0);
 				int num2 = ((!(position2.z < position.z)) ? ((!(position2.z > position.z)) ? 1 : 2) : 0);
-				m_neighborGrid[num, num2] = neighbor.GetAndCreateTerrainCompiler();
+				m_neighborGrid[num, num2] = FindTerrainCompiler(neighbor.transform.position);
 			}
 		}
 		return m_neighborGrid[x, y];
```

#### 📄 `Valheim.SettingsGui/AccessibilitySettings.cs` (🟡 MODIFIED `+13/-4`) <a id="assembly_valheim_valheim_settingsgui_accessibilitysettings_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/Valheim.SettingsGui/AccessibilitySettings.cs
+++ b/Valheim.SettingsGui/AccessibilitySettings.cs
@@ -40,14 +40,17 @@
 	[SerializeField]
 	private Toggle m_soundIndicatorsToggle;
 
+	[SerializeField]
+	private Toggle m_toggleBlockToggle;
+
 	public event Action<string, int> SharedSettingChanged;
 
 	public void OnTabOpen(Button backButton, Button okButton)
 	{
-		GuiUtils.SetNavigationDown(m_motionblurToggle, backButton);
-		GuiUtils.SetNavigationUp(backButton, m_motionblurToggle);
-		GuiUtils.SetNavigationUp(okButton, m_depthOfFieldToggle);
-		GuiUtils.SetNavigationDown(m_depthOfFieldToggle, okButton);
+		GuiUtils.SetNavigationDown(m_depthOfFieldToggle, backButton);
+		GuiUtils.SetNavigationUp(backButton, m_depthOfFieldToggle);
+		GuiUtils.SetNavigationUp(okButton, m_toggleBlockToggle);
+		GuiUtils.SetNavigationDown(m_toggleBlockToggle, okButton);
 	}
 
 	public void Initialize()
@@ -62,6 +65,7 @@
 		m_depthOfFieldToggle.isOn = PlatformPrefs.GetInt("DOF", 1) == 1;
 		m_closedCaptionsToggle.isOn = PlatformPrefs.GetInt("ClosedCaptions") == 1;
 		m_soundIndicatorsToggle.isOn = PlatformPrefs.GetInt("DirectionalSoundIndicators") == 1;
+		m_toggleBlockToggle.isOn = PlatformPrefs.GetInt("ToggleBlock") == 1;
 		Settings.ReduceFlashingLights = m_reduceFlashingLights.isOn;
 		Settings.DirectionalSoundIndicators = m_soundIndicatorsToggle.isOn;
 		Settings.ClosedCaptions = m_closedCaptionsToggle.isOn;
@@ -76,9 +80,14 @@
 		PlatformPrefs.SetInt("ReduceFlashingLights", m_reduceFlashingLights.isOn ? 1 : 0);
 		PlatformPrefs.SetInt("ClosedCaptions", m_closedCaptionsToggle.isOn ? 1 : 0);
 		PlatformPrefs.SetInt("DirectionalSoundIndicators", m_soundIndicatorsToggle.isOn ? 1 : 0);
+		PlatformPrefs.SetInt("ToggleBlock", m_toggleBlockToggle.isOn ? 1 : 0);
 		Settings.ReduceFlashingLights = m_reduceFlashingLights.isOn;
 		Settings.ClosedCaptions = m_closedCaptionsToggle.isOn;
 		Settings.DirectionalSoundIndicators = m_soundIndicatorsToggle.isOn;
+		if (Player.m_localPlayer != null)
+		{
+			Player.m_localPlayer.ToggleBlock = m_toggleBlockToggle.isOn;
+		}
 		okActionCompletedCallback?.Invoke();
 	}
 
```

#### 📄 `Valheim.SettingsGui/GamepadSettings.cs` (🟡 MODIFIED `+3/-3`) <a id="assembly_valheim_valheim_settingsgui_gamepadsettings_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/Valheim.SettingsGui/GamepadSettings.cs
+++ b/Valheim.SettingsGui/GamepadSettings.cs
@@ -154,9 +154,9 @@
 
 	private const string GlyphsPlaystation = "Playstation";
 
-	public static float m_motionSensorYAxisSensitivity = 1f;
-
-	public static float m_motionSensorXAxisSensitivity = 1f;
+	public static float m_motionSensorYAxisSensitivity;
+
+	public static float m_motionSensorXAxisSensitivity;
 
 	private List<string> m_glyphOptions = new List<string> { "Xbox", "Playstation" };
 
```

#### 📄 `Valheim.SettingsGui/GameplaySettings.cs` (🟡 MODIFIED `+5/-1`) <a id="assembly_valheim_valheim_settingsgui_gameplaysettings_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/Valheim.SettingsGui/GameplaySettings.cs
+++ b/Valheim.SettingsGui/GameplaySettings.cs
@@ -43,6 +43,9 @@
 
 	[SerializeField]
 	private Toggle m_showBuildPieceAuthor;
+
+	[SerializeField]
+	private Toggle m_skipIntroCinematic;
 
 	[SerializeField]
 	private Slider m_autoBackups;
@@ -101,6 +104,7 @@
 		m_reduceBGUsage.isOn = PlatformPrefs.GetInt("ReduceBackgroundUsage") == 1;
 		m_enableConsole.isOn = PlatformPrefs.GetInt("EnableConsole", Console.instance.IsConsoleEnabled() ? 1 : 0) == 1;
 		m_showBuildPieceAuthor.isOn = PlatformPrefs.GetInt("ShowBuildPieceAuthor", (Application.platform == RuntimePlatform.PS5) ? 1 : 0) == 1;
+		m_skipIntroCinematic.isOn = PlatformPrefs.GetBool("SkipIntroCinematic");
 		Hud.s_showBuildPieceAuthor = m_showBuildPieceAuthor.isOn;
 		m_autoBackups.value = PlatformPrefs.GetInt("AutoBackups", 4);
 		UpdateLanguageText();
@@ -119,6 +123,7 @@
 		PlatformPrefs.SetInt("ReduceBackgroundUsage", m_reduceBGUsage.isOn ? 1 : 0);
 		PlatformPrefs.SetInt("AutoBackups", (int)m_autoBackups.value);
 		PlatformPrefs.SetInt("ShowBuildPieceAuthor", m_showBuildPieceAuthor.isOn ? 1 : 0);
+		PlatformPrefs.SetBool("SkipIntroCinematic", m_skipIntroCinematic.isOn);
 		Hud.s_showBuildPieceAuthor = m_showBuildPieceAuthor.isOn;
 		ZInput.ToggleRun = m_toggleRun.isOn;
 		Raven.m_tutorialsEnabled = m_tutorialsEnabled.isOn;
@@ -154,7 +159,6 @@
 	public void OnConsoleToggle()
 	{
 		PlatformPrefs.SetInt("EnableConsole", m_enableConsole.isOn ? 1 : 0);
-		UnityEngine.Object.FindAnyObjectByType<KeyboardMouseSettings>(FindObjectsInactive.Include).SetConsoleEnabled(m_enableConsole.isOn);
 		Console.SetConsoleEnabled(m_enableConsole.isOn);
 	}
 
```

#### 📄 `Valheim.SettingsGui/KeyboardMouseSettings.cs` (🟡 MODIFIED `+6/-25`) <a id="assembly_valheim_valheim_settingsgui_keyboardmousesettings_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

**Identified Changes / Methods:**
- `public void SetConsoleEnabled(bool enabled)`

```diff
--- a/Valheim.SettingsGui/KeyboardMouseSettings.cs
+++ b/Valheim.SettingsGui/KeyboardMouseSettings.cs
@@ -34,9 +34,6 @@
 	private List<KeySetting> m_keys = new List<KeySetting>();
 
 	[SerializeField]
-	private Button m_consoleKeyButton;
-
-	[SerializeField]
 	private Button m_bottomLeftKeyButton;
 
 	[SerializeField]
@@ -62,12 +59,12 @@
 
 	public void OnTabOpen(Button backButton, Button okButton)
 	{
-		Button button = ((m_consoleKeyButton.transform.parent.localScale.x > 0f) ? m_consoleKeyButton.GetComponentInChildren<Button>() : m_bottomLeftKeyButton.GetComponentInChildren<Button>());
-		GuiUtils.SetNavigationDown(button, backButton);
-		GuiUtils.SetNavigationUp(backButton, button);
-		button = m_bottomRightKeyButton.GetComponentInChildren<Button>();
-		GuiUtils.SetNavigationDown(button, okButton);
-		GuiUtils.SetNavigationUp(okButton, button);
+		Button componentInChildren = m_bottomLeftKeyButton.GetComponentInChildren<Button>();
+		GuiUtils.SetNavigationDown(componentInChildren, backButton);
+		GuiUtils.SetNavigationUp(backButton, componentInChildren);
+		componentInChildren = m_bottomRightKeyButton.GetComponentInChildren<Button>();
+		GuiUtils.SetNavigationDown(componentInChildren, okButton);
+		GuiUtils.SetNavigationUp(okButton, componentInChildren);
 	}
 
 	public void Initialize()
@@ -83,10 +80,6 @@
 		SetupKeys();
 		m_scrollRectVisibilityManager = GetComponentInChildren<ScrollRectEnsureVisible>();
 		m_selectedGameObject = EventSystem.current.currentSelectedGameObject;
-		if (m_consoleKeyButton.transform.parent.localScale.x > 0f)
-		{
-			SetConsoleEnabled(enabled: true);
-		}
 	}
 
 	public void OnBack()
@@ -191,18 +184,6 @@
 		if (setting == "InvertMouse")
 		{
 			m_invertMouse.isOn = value == 1;
-		}
-	}
-
-	public void SetConsoleEnabled(bool enabled)
-	{
-		int num = (enabled ? 1 : 0);
-		m_consoleKeyButton.transform.parent.transform.localScale = new Vector3(num, num, 1f);
-		if (enabled)
-		{
-			GuiUtils.SetNavigationUp(m_consoleKeyButton, m_bottomLeftKeyButton);
-			GuiUtils.SetNavigationLeft(m_consoleKeyButton, null);
-			GuiUtils.SetNavigationDown(m_bottomLeftKeyButton, m_consoleKeyButton);
 		}
 	}
 
```

#### 📄 `Version.cs` (🟡 MODIFIED `+1/-1`) <a id="assembly_valheim_version_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/Version.cs
+++ b/Version.cs
@@ -165,7 +165,7 @@
 
 	public static readonly GameVersion FirstVersionWithModifiers = new GameVersion(0, 217, 8);
 
-	public static GameVersion CurrentVersion { get; } = new GameVersion(1, 0, 12);
+	public static GameVersion CurrentVersion { get; } = new GameVersion(1, 0, 14);
 
 	public static string GetVersionString(bool includeMercurialHash = false)
 	{
```

#### 📄 `ZNet.cs` (🟡 MODIFIED `+4/-5`) <a id="assembly_valheim_znet_cs"></a>
*([⬆ Back to `assembly_valheim.dll` summary](#assembly_valheim))*

```diff
--- a/ZNet.cs
+++ b/ZNet.cs
@@ -1340,11 +1340,10 @@
 		if (IsServer())
 		{
 			RPC_Save(null);
-		}
-		else
-		{
-			GetServerRPC()?.Invoke("Save");
-		}
+			return;
+		}
+		Game.instance.SavePlayerProfile(setLogoutPoint: true);
+		GetServerRPC()?.Invoke("Save");
 	}
 
 	private void RPC_Save(ZRpc rpc)
```

---

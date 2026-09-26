# `Valheim.UI/RadialConfigHelper.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/RadialConfigHelper.cs
+++ b/Valheim.UI/RadialConfigHelper.cs
@@ -20,7 +20,7 @@
 	public static void SetItemInteractionControls(this RadialBase radial)
 	{
 		radial.GetConfirm = () => (ZInput.GetButtonLastPressedTimer("JoyRadialInteract") < 0.33f && ZInput.GetButtonUp("JoyRadialInteract")) || ZInput.GetMouseButtonUp(0);
-		radial.GetReleaseToUse = delegate
+		radial.GetReleaseToUse = () =>
 		{
 			if (!RadialData.SO.EnableReleaseToUseMode)
 			{
@@ -31,7 +31,7 @@
 		radial.GetBack = () => ZInput.GetButtonUp("JoyRadialBack") || (ZInput.GetButtonUp("JoyRadialClose") && !radial.IsTopLevel) || (!ZInput.GetKey(KeyCode.LeftShift) && !ZInput.IsGamepadMouseActive() && ZInput.GetMouseButtonUp(1));
 		radial.GetThrow = () => (ZInput.GetButtonLastPressedTimer("JoyRadialSecondaryInteract") < 0.33f && ZInput.GetButtonUp("JoyRadialSecondaryInteract")) || (ZInput.GetKey(KeyCode.LeftShift) && ZInput.GetButtonLastPressedTimer("RadialSecondaryInteract") < 0.33f && ZInput.GetButtonUp("RadialSecondaryInteract"));
 		radial.GetOpenThrowMenu = () => (ZInput.GetButtonPressedTimer("JoyRadialSecondaryInteract") > 0.33f && ZInput.GetButton("JoyRadialSecondaryInteract")) || (ZInput.GetKey(KeyCode.LeftShift) && ZInput.GetButtonPressedTimer("RadialSecondaryInteract") > 0.33f && ZInput.GetButton("RadialSecondaryInteract"));
-		radial.GetClose = delegate
+		radial.GetClose = () =>
 		{
 			if ((ZInput.GetButtonUp("JoyRadialClose") && radial.IsTopLevel) || ZInput.GetButtonDown("JoyRadial") || ZInput.GetKeyDown(KeyCode.Escape) || ZInput.GetKeyDown(KeyCode.BackQuote) || ZInput.GetButtonDown("JoyMenu") || ZInput.GetButtonDown("JoyMap") || ZInput.GetButtonDown("Map") || ZInput.GetButtonDown("JoyChat") || ZInput.GetButtonDown("Chat") || ZInput.GetButtonDown("Console") || ZInput.GetButtonDown("OpenEmote"))
 			{
```

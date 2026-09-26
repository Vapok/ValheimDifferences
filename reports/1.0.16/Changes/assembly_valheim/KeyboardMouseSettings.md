# `Valheim.SettingsGui/KeyboardMouseSettings.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.SettingsGui/KeyboardMouseSettings.cs
+++ b/Valheim.SettingsGui/KeyboardMouseSettings.cs
@@ -142,7 +142,7 @@
 	private void InvalidKeybindPopup()
 	{
 		string text = "$invalid_keybind_text";
-		UnifiedPopup.Push(new WarningPopup("$invalid_keybind_header", text, delegate
+		UnifiedPopup.Push(new WarningPopup("$invalid_keybind_header", text, () =>
 		{
 			UnifiedPopup.Pop();
 			StartCoroutine(DelayedKeyEnable());
@@ -151,7 +151,7 @@
 
 	private IEnumerator DelayedKeyEnable()
 	{
-		if (!(base.gameObject == null))
+		if (!(gameObject == null))
 		{
 			yield return null;
 			EnableKeys(enable: true);
@@ -195,7 +195,7 @@
 		foreach (KeySetting key in m_keys)
 		{
 			GuiButton componentInChildren = key.m_keyTransform.GetComponentInChildren<GuiButton>();
-			componentInChildren.onClick.AddListener(delegate
+			componentInChildren.onClick.AddListener(() =>
 			{
 				OpenBindDialog(key);
 			});
```

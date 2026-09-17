# `Valheim.SettingsGui/KeyboardMouseSettings.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-25` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `public void SetConsoleEnabled(bool enabled)`

---

## 📝 Code Diff

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

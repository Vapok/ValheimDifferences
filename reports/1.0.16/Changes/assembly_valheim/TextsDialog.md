# `TextsDialog.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/TextsDialog.cs
+++ b/TextsDialog.cs
@@ -62,7 +62,7 @@
 
 	public void Setup(Player player)
 	{
-		base.gameObject.SetActive(value: true);
+		gameObject.SetActive(value: true);
 		FillTextList();
 		if (m_texts.Count > 0)
 		{
@@ -116,7 +116,7 @@
 			text.m_listElement = gameObject;
 			text.m_selected = Utils.FindChild(gameObject.transform, "selected").gameObject;
 			text.m_selected.SetActive(value: false);
-			gameObject.GetComponent<Button>().onClick.AddListener(delegate
+			gameObject.GetComponent<Button>().onClick.AddListener(() =>
 			{
 				OnSelectText(text);
 			});
@@ -140,16 +140,16 @@
 			float joyRightStickY = ZInput.GetJoyRightStickY();
 			float joyLeftStickY = ZInput.GetJoyLeftStickY();
 			bool buttonDown = ZInput.GetButtonDown("JoyDPadUp");
-			bool num = joyLeftStickY < -0.1f;
+			bool flag = joyLeftStickY < -0.1f;
 			bool buttonDown2 = ZInput.GetButtonDown("JoyDPadDown");
-			bool flag = joyLeftStickY > 0.1f;
-			if ((buttonDown2 | flag) && m_selectionIndex < m_texts.Count - 1)
+			bool flag2 = joyLeftStickY > 0.1f;
+			if ((buttonDown2 | flag2) && m_selectionIndex < m_texts.Count - 1)
 			{
 				GamepadRumble.instance.PlayGlobalSelectVibration();
 				ShowText(Mathf.Min(m_texts.Count - 1, GetSelectedText() + 1));
 				m_inputDelayTimer = 0.1f;
 			}
-			if ((num | buttonDown) && m_selectionIndex > 0)
+			if ((flag | buttonDown) && m_selectionIndex > 0)
 			{
 				GamepadRumble.instance.PlayGlobalSelectVibration();
 				ShowText(Mathf.Max(0, GetSelectedText() - 1));
@@ -201,7 +201,7 @@
 
 	public void OnClose()
 	{
-		base.gameObject.SetActive(value: false);
+		gameObject.SetActive(value: false);
 	}
 
 	private void UpdateTextsList()
```

# `UnifiedPopup.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnifiedPopup.cs
+++ b/UnifiedPopup.cs
@@ -289,13 +289,13 @@
 		bodyText.text = popup.text;
 		buttonRightText.text = Localization.instance.Localize(yesText);
 		buttonRight.gameObject.SetActive(value: true);
-		buttonRight.onClick.AddListener(delegate
+		buttonRight.onClick.AddListener(() =>
 		{
 			popup.yesCallback?.Invoke();
 		});
 		buttonLeftText.text = Localization.instance.Localize(noText);
 		buttonLeft.gameObject.SetActive(value: true);
-		buttonLeft.onClick.AddListener(delegate
+		buttonLeft.onClick.AddListener(() =>
 		{
 			popup.noCallback?.Invoke();
 		});
@@ -311,7 +311,7 @@
 		bodyText.text = popup.text;
 		buttonCenterText.text = Localization.instance.Localize(okText);
 		buttonCenter.gameObject.SetActive(value: true);
-		buttonCenter.onClick.AddListener(delegate
+		buttonCenter.onClick.AddListener(() =>
 		{
 			popup.okCallback?.Invoke();
 		});
@@ -329,7 +329,7 @@
 		popup.SetUpdateCoroutineReference(StartCoroutine(popup.updateRoutine));
 		buttonCenterText.text = Localization.instance.Localize(cancelText);
 		buttonCenter.gameObject.SetActive(value: true);
-		buttonCenter.onClick.AddListener(delegate
+		buttonCenter.onClick.AddListener(() =>
 		{
 			popup.cancelCallback?.Invoke();
 			StopCoroutine(popup.updateCoroutine);
@@ -345,17 +345,17 @@
 		textEntryField.gameObject.SetActive(value: true);
 		buttonLeftText.text = Localization.instance.Localize(cancelText);
 		buttonLeft.gameObject.SetActive(value: true);
-		buttonLeft.onClick.AddListener(delegate
+		buttonLeft.onClick.AddListener(() =>
 		{
 			popup.cancelCallback?.Invoke();
 		});
 		buttonConfirmText.text = Localization.instance.Localize(okText);
 		buttonConfirm.gameObject.SetActive(value: true);
-		buttonConfirm.onClick.AddListener(delegate
+		buttonConfirm.onClick.AddListener(() =>
 		{
 			popup?.sendResultCallback(textEntryField.text);
 		});
-		textEntryField.onValueChanged.AddListener(delegate(string s)
+		textEntryField.onValueChanged.AddListener((string s) =>
 		{
 			buttonConfirm.interactable = popup.validationCallback?.Invoke(s) ?? true;
 		});
```

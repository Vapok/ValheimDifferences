# `ManageSavesMenuElement.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ManageSavesMenuElement.cs
+++ b/ManageSavesMenuElement.cs
@@ -30,7 +30,7 @@
 		{
 			File = backup;
 			Button.onClick.RemoveAllListeners();
-			Button.onClick.AddListener(delegate
+			Button.onClick.AddListener(() =>
 			{
 				clickedCallback?.Invoke();
 			});
@@ -110,7 +110,7 @@
 
 	private Coroutine listAnimationCoroutine;
 
-	public RectTransform rectTransform => base.transform as RectTransform;
+	public RectTransform rectTransform => transform as RectTransform;
 
 	private RectTransform arrowRectTransform => arrow.transform as RectTransform;
 
@@ -175,7 +175,7 @@
 			if (dictionary.ContainsKey(saveFile.Name) && dictionary[saveFile.Name].ContainsKey(saveFile.m_source))
 			{
 				int currentIndex = j;
-				dictionary[saveFile.Name][saveFile.m_source].UpdateElement(saveFile, delegate
+				dictionary[saveFile.Name][saveFile.m_source].UpdateElement(saveFile, () =>
 				{
 					OnBackupElementClicked(currentIndex);
 				});
@@ -225,7 +225,7 @@
 			if (backupNameToElementMap.ContainsKey(saveFile.Name) && backupNameToElementMap[saveFile.Name].ContainsKey(saveFile.m_source))
 			{
 				int currentIndex = i;
-				backupNameToElementMap[saveFile.Name][saveFile.m_source].UpdateElement(saveFile, delegate
+				backupNameToElementMap[saveFile.Name][saveFile.m_source].UpdateElement(saveFile, () =>
 				{
 					OnBackupElementClicked(currentIndex);
 				});
@@ -258,7 +258,7 @@
 
 	private BackupElement CreateBackupElement(SaveFile backup, int index)
 	{
-		return new BackupElement(Object.Instantiate(backupElement.gameObject, rectTransform), backup, delegate
+		return new BackupElement(Object.Instantiate(backupElement.gameObject, rectTransform), backup, () =>
 		{
 			OnBackupElementClicked(index);
 		});
```

# `ManageSavesMenu.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+33/-33` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ManageSavesMenu.cs
+++ b/ManageSavesMenu.cs
@@ -254,7 +254,7 @@
 			ulong capacityBytes = 0uL;
 			int usedFiles = 0;
 			int capacityFiles = 0;
-			backgroundWorker.DoWork += delegate
+			backgroundWorker.DoWork += (object sender, DoWorkEventArgs args) =>
 			{
 				bool flag = false;
 				if (FileHelpers.CloudStorageSupported)
@@ -274,7 +274,7 @@
 					FileHelpers.Unmount();
 				}
 			};
-			backgroundWorker.RunWorkerCompleted += delegate
+			backgroundWorker.RunWorkerCompleted += (object sender, RunWorkerCompletedEventArgs args) =>
 			{
 				storageUsed.gameObject.SetActive(value: true);
 				storageBar.parent.gameObject.SetActive(value: true);
@@ -313,11 +313,11 @@
 				_ => "Remove?", 
 			}));
 			SaveFile toDelete = (isBackup ? currentList[selectedSaveIndex].BackupFiles[selectedBackupIndex] : currentList[selectedSaveIndex].PrimaryFile);
-			UnifiedPopup.Push(new YesNoPopup(Localization.instance.Localize(text), isBackup ? toDelete.Name : currentList[selectedSaveIndex].Name, delegate
+			UnifiedPopup.Push(new YesNoPopup(Localization.instance.Localize(text), isBackup ? toDelete.Name : currentList[selectedSaveIndex].Name, () =>
 			{
 				UnifiedPopup.Pop();
 				DeleteSaveFile(toDelete, isBackup);
-			}, delegate
+			}, () =>
 			{
 				UnifiedPopup.Pop();
 			}, localizeText: false));
@@ -348,14 +348,14 @@
 		}
 		if (saveFile2 != null)
 		{
-			UnifiedPopup.Push(new WarningPopup(Localization.instance.Localize("$menu_cantmovesave"), Localization.instance.Localize("$menu_duplicatefileprompttext", saveFile.Name), delegate
+			UnifiedPopup.Push(new WarningPopup(Localization.instance.Localize("$menu_cantmovesave"), Localization.instance.Localize("$menu_duplicatefileprompttext", saveFile.Name), () =>
 			{
 				UnifiedPopup.Pop();
 			}, localizeText: false));
 		}
 		else if (SaveSystem.IsCorrupt(saveFile))
 		{
-			UnifiedPopup.Push(new WarningPopup("$menu_cantmovesave", "$menu_savefilecorrupt", delegate
+			UnifiedPopup.Push(new WarningPopup("$menu_cantmovesave", "$menu_savefilecorrupt", () =>
 			{
 				UnifiedPopup.Pop();
 			}));
@@ -386,11 +386,11 @@
 	{
 		SaveWithBackups saveWithBackups = currentList[selectedSaveIndex];
 		SaveFile backup = currentList[selectedSaveIndex].BackupFiles[selectedBackupIndex];
-		UnifiedPopup.Push(new YesNoPopup(Localization.instance.Localize("$menu_backuprestorepromptheader"), saveWithBackups.IsDeleted ? Localization.instance.Localize("$menu_backuprestorepromptrecover", saveWithBackups.Name, backup.Name) : Localization.instance.Localize("$menu_backuprestorepromptreplace", saveWithBackups.Name, backup.Name), delegate
+		UnifiedPopup.Push(new YesNoPopup(Localization.instance.Localize("$menu_backuprestorepromptheader"), saveWithBackups.IsDeleted ? Localization.instance.Localize("$menu_backuprestorepromptrecover", saveWithBackups.Name, backup.Name) : Localization.instance.Localize("$menu_backuprestorepromptreplace", saveWithBackups.Name, backup.Name), () =>
 		{
 			UnifiedPopup.Pop();
 			RestoreBackupAsync();
-		}, delegate
+		}, () =>
 		{
 			UnifiedPopup.Pop();
 		}, localizeText: false));
@@ -399,11 +399,11 @@
 			PushPleaseWait();
 			SaveSystem.RestoreBackupResult result = SaveSystem.RestoreBackupResult.UnknownError;
 			BackgroundWorker backgroundWorker = new BackgroundWorker();
-			backgroundWorker.DoWork += delegate
+			backgroundWorker.DoWork += (object sender, DoWorkEventArgs args) =>
 			{
 				result = SaveSystem.RestoreBackup(backup);
 			};
-			backgroundWorker.RunWorkerCompleted += delegate
+			backgroundWorker.RunWorkerCompleted += (object sender, RunWorkerCompletedEventArgs args) =>
 			{
 				PopPleaseWait();
 				if (result != SaveSystem.RestoreBackupResult.Success)
@@ -419,7 +419,7 @@
 		}
 		static void RestoreBackupFailed()
 		{
-			UnifiedPopup.Push(new WarningPopup("$menu_backuprestorefailedheader", "$menu_tryagainorrestart", delegate
+			UnifiedPopup.Push(new WarningPopup("$menu_backuprestorefailedheader", "$menu_tryagainorrestart", () =>
 			{
 				UnifiedPopup.Pop();
 			}));
@@ -433,7 +433,7 @@
 		int saveIndex = selectedSaveIndex;
 		int backupIndex = selectedBackupIndex;
 		DeselectCurrent();
-		UpdateCloudUsageAndReloadSavesAsync(delegate(bool success)
+		UpdateCloudUsageAndReloadSavesAsync((bool success) =>
 		{
 			if (success)
 			{
@@ -446,7 +446,7 @@
 		});
 		void UpdateGuiAsync()
 		{
-			UpdateSavesListGuiAsync(delegate
+			UpdateSavesListGuiAsync(() =>
 			{
 				int num = listElements.FindIndex((ManageSavesMenuElement save) => save.Save.Name == saveName);
 				if (num >= 0)
@@ -500,7 +500,7 @@
 		DeselectCurrent();
 		currentList = SaveSystem.GetSavesByType(dataType);
 		currentListType = dataType;
-		UpdateSavesListGuiAsync(delegate
+		UpdateSavesListGuiAsync(() =>
 		{
 			bool flag = false;
 			if (!string.IsNullOrEmpty(m_queuedNameToSelect))
@@ -533,11 +533,11 @@
 		PushPleaseWait();
 		bool success = false;
 		BackgroundWorker backgroundWorker = new BackgroundWorker();
-		backgroundWorker.DoWork += delegate
+		backgroundWorker.DoWork += (object sender, DoWorkEventArgs args) =>
 		{
 			success = SaveSystem.Delete(file);
 		};
-		backgroundWorker.RunWorkerCompleted += delegate
+		backgroundWorker.RunWorkerCompleted += (object sender, RunWorkerCompletedEventArgs args) =>
 		{
 			PopPleaseWait();
 			if (!success)
@@ -553,7 +553,7 @@
 		backgroundWorker.RunWorkerAsync();
 		static void DeleteSaveFailed()
 		{
-			UnifiedPopup.Push(new WarningPopup("$menu_deletefailedheader", "$menu_tryagainorrestart", delegate
+			UnifiedPopup.Push(new WarningPopup("$menu_deletefailedheader", "$menu_tryagainorrestart", () =>
 			{
 				UnifiedPopup.Pop();
 			}));
@@ -566,11 +566,11 @@
 		bool cloudQuotaExceeded = false;
 		bool success = false;
 		BackgroundWorker backgroundWorker = new BackgroundWorker();
-		backgroundWorker.DoWork += delegate
+		backgroundWorker.DoWork += (object sender, DoWorkEventArgs args) =>
 		{
 			success = SaveSystem.MoveSource(file, isBackup, destinationSource, out cloudQuotaExceeded);
 		};
-		backgroundWorker.RunWorkerCompleted += delegate
+		backgroundWorker.RunWorkerCompleted += (object sender, RunWorkerCompletedEventArgs args) =>
 		{
 			PopPleaseWait();
 			if (cloudQuotaExceeded)
@@ -588,7 +588,7 @@
 		backgroundWorker.RunWorkerAsync();
 		static void MoveSourceFailed()
 		{
-			UnifiedPopup.Push(new WarningPopup("$menu_movefailedheader", "$menu_tryagainorrestart", delegate
+			UnifiedPopup.Push(new WarningPopup("$menu_movefailedheader", "$menu_tryagainorrestart", () =>
 			{
 				UnifiedPopup.Pop();
 			}));
@@ -605,7 +605,7 @@
 		PushPleaseWait();
 		Exception reloadException = null;
 		BackgroundWorker backgroundWorker = new BackgroundWorker();
-		backgroundWorker.DoWork += delegate
+		backgroundWorker.DoWork += (object sender, DoWorkEventArgs args) =>
 		{
 			try
 			{
@@ -616,7 +616,7 @@
 				reloadException = ex;
 			}
 		};
-		backgroundWorker.RunWorkerCompleted += delegate
+		backgroundWorker.RunWorkerCompleted += (object sender, RunWorkerCompletedEventArgs args) =>
 		{
 			currentList = SaveSystem.GetSavesByType(currentListType);
 			PopPleaseWait();
@@ -654,9 +654,9 @@
 
 	private ManageSavesMenuElement CreateElement()
 	{
-		GameObject obj = UnityEngine.Object.Instantiate(saveElement, listRoot);
-		ManageSavesMenuElement component = obj.GetComponent<ManageSavesMenuElement>();
-		obj.SetActive(value: true);
+		GameObject gameObject = UnityEngine.Object.Instantiate(saveElement, listRoot);
+		ManageSavesMenuElement component = gameObject.GetComponent<ManageSavesMenuElement>();
+		gameObject.SetActive(value: true);
 		component.HeightChanged += OnSaveElementHeighChanged;
 		component.ElementClicked += OnElementClicked;
 		component.ElementExpandedChanged += OnElementExpandedChanged;
@@ -827,7 +827,7 @@
 	{
 		this.closedCallback = closedCallback;
 		this.savesModifiedCallback = savesModifiedCallback;
-		if (base.gameObject.activeSelf && tabHandler.GetActiveTab() == GetTabIndexFromSaveDataType(dataType))
+		if (gameObject.activeSelf && tabHandler.GetActiveTab() == GetTabIndexFromSaveDataType(dataType))
 		{
 			return;
 		}
@@ -837,8 +837,8 @@
 		actionButton.onClick.AddListener(OnPrimaryActionButton);
 		storageUsed.gameObject.SetActive(value: false);
 		storageBar.parent.gameObject.SetActive(value: false);
-		base.gameObject.SetActive(value: true);
-		UpdateCloudUsageAndReloadSavesAsync(delegate(bool success)
+		gameObject.SetActive(value: true);
+		UpdateCloudUsageAndReloadSavesAsync((bool success) =>
 		{
 			if (!success)
 			{
@@ -858,7 +858,7 @@
 		}
 		else
 		{
-			UpdateCloudUsageAsync(delegate
+			UpdateCloudUsageAsync(() =>
 			{
 				ReloadSavesAsync(callback);
 			});
@@ -887,13 +887,13 @@
 		removeButton.onClick.RemoveListener(OnRemoveButton);
 		moveButton.onClick.RemoveListener(OnMoveButton);
 		actionButton.onClick.RemoveListener(OnPrimaryActionButton);
-		base.gameObject.SetActive(value: false);
+		gameObject.SetActive(value: false);
 		closedCallback?.Invoke();
 	}
 
 	public bool IsVisible()
 	{
-		return base.gameObject.activeInHierarchy;
+		return gameObject.activeInHierarchy;
 	}
 
 	private void SelectByIndex(int saveIndex, int backupIndex = -1)
@@ -1075,7 +1075,7 @@
 			header = "$menu_cloudstoragefull";
 			text = "$menu_cloudstoragefulloperationfailed";
 		}
-		UnifiedPopup.Push(new WarningPopup(header, text, delegate
+		UnifiedPopup.Push(new WarningPopup(header, text, () =>
 		{
 			UnifiedPopup.Pop();
 		}));
@@ -1083,7 +1083,7 @@
 
 	public void ShowReloadError()
 	{
-		UnifiedPopup.Push(new WarningPopup("$menu_reloadfailed", "$menu_checklogfile", delegate
+		UnifiedPopup.Push(new WarningPopup("$menu_reloadfailed", "$menu_checklogfile", () =>
 		{
 			UnifiedPopup.Pop();
 		}));
```

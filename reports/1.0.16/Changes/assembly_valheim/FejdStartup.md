# `FejdStartup.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+63/-63` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/FejdStartup.cs
+++ b/FejdStartup.cs
@@ -330,9 +330,9 @@
 		m_menuButtons = m_menuList.GetComponentsInChildren<Button>();
 		if (PlatformManager.DistributionPlatform != null && PlatformManager.DistributionPlatform.HardwareInfoProvider != null && PlatformManager.DistributionPlatform.HardwareInfoProvider.HardwareInfo.m_category == HardwareCategory.Console)
 		{
-			GameObject obj = GameObject.Find("Exit");
-			obj.SetActive(value: false);
-			Button component = obj.GetComponent<Button>();
+			GameObject gameObject = GameObject.Find("Exit");
+			gameObject.SetActive(value: false);
+			Button component = gameObject.GetComponent<Button>();
 			List<Button> list = new List<Button>();
 			Button[] menuButtons = m_menuButtons;
 			foreach (Button button in menuButtons)
@@ -524,7 +524,7 @@
 		m_moddedText.SetActive(Game.isModded);
 		m_worldListBaseSize = m_worldListRoot.rect.height;
 		m_versionLabel.text = $"Version {Version.GetVersionString()} (n-{40u})";
-		Localization.instance.Localize(base.transform);
+		Localization.instance.Localize(transform);
 		Localization.OnLanguageChange = (Action)Delegate.Combine(Localization.OnLanguageChange, new Action(OnLanguageChange));
 	}
 
@@ -616,7 +616,7 @@
 			{
 				string joinCode = commandLineArgs[i + 1];
 				Action autoJoin = null;
-				autoJoin = delegate
+				autoJoin = () =>
 				{
 					m_cliUpdateAction -= autoJoin;
 					AutoJoinServer(joinCode);
@@ -629,7 +629,7 @@
 	private static void QueueSettingSimulationDistance(SimulationDistance simulationDistance)
 	{
 		Action setSimDist = null;
-		setSimDist = delegate
+		setSimDist = () =>
 		{
 			ZNet.s_onZNetStart = (Action)Delegate.Remove(ZNet.s_onZNetStart, setSimDist);
 			ZNet.instance.ApplySimulationDistance(simulationDistance);
@@ -649,7 +649,7 @@
 		{
 			return;
 		}
-		PlayFabManager.instance.LoginFinished += delegate(LoginType loginType)
+		PlayFabManager.instance.LoginFinished += (LoginType loginType) =>
 		{
 			if (!m_autoConnectionInProgress)
 			{
@@ -659,11 +659,11 @@
 					ZLog.LogError("Failed to login to PlayFab");
 					Application.Quit();
 				}
-				ZPlayFabMatchmaking.ResolveJoinCode(joinCode, delegate(PlayFabMatchmakingServerData serverData)
+				ZPlayFabMatchmaking.ResolveJoinCode(joinCode, (PlayFabMatchmakingServerData serverData) =>
 				{
 					m_joinServer = new ServerJoinData(new ServerJoinDataPlayFabUser(serverData.remotePlayerId));
 					JoinServer();
-				}, delegate(ZPLayFabMatchmakingFailReason failReason)
+				}, (ZPLayFabMatchmakingFailReason failReason) =>
 				{
 					ZLog.LogError("Failed to resolve joincode: " + failReason);
 					Application.Quit();
@@ -854,7 +854,7 @@
 
 	private void SetupObjectDB()
 	{
-		ObjectDB objectDB = base.gameObject.AddComponent<ObjectDB>();
+		ObjectDB objectDB = gameObject.AddComponent<ObjectDB>();
 		ObjectDB component = m_objectDBPrefab.GetComponent<ObjectDB>();
 		objectDB.CopyOtherDB(component);
 	}
@@ -986,7 +986,7 @@
 
 	public void ResetOnlineRelatedButtons()
 	{
-		TabHandler[] componentsInChildren = base.transform.GetComponentsInChildren<TabHandler>(includeInactive: true);
+		TabHandler[] componentsInChildren = transform.GetComponentsInChildren<TabHandler>(includeInactive: true);
 		int num = 0;
 		if (num < componentsInChildren.Length)
 		{
@@ -1003,7 +1003,7 @@
 	{
 		if (!PlatformPrefs.GetBool("EulaAccepted"))
 		{
-			m_eulaWindow.Open(delegate(bool accepted)
+			m_eulaWindow.Open((bool accepted) =>
 			{
 				if (accepted)
 				{
@@ -1077,7 +1077,7 @@
 			{
 				string text = "";
 				text = ((!(PlatformManager.DistributionPlatform.Platform.ToString() == "GameCenter")) ? "$menu_logging_in_played_failed_not_signed_in_to_platform" : "$menu_logging_in_played_failed_not_signed_in_to_platform_gamecenter");
-				UnifiedPopup.Push(new WarningPopup("$menu_logging_in_playfab_failed_header", text, delegate
+				UnifiedPopup.Push(new WarningPopup("$menu_logging_in_playfab_failed_header", text, () =>
 				{
 					UnifiedPopup.Pop();
 				}));
@@ -1091,7 +1091,7 @@
 
 	private void ValidatePrivileges(Action onCompleted)
 	{
-		if (VerifyHasMultiplayerPrivilege(delegate(PrivilegeResult pr, Privilege p)
+		if (VerifyHasMultiplayerPrivilege((PrivilegeResult pr, Privilege p) =>
 		{
 			TryResolvePrivileges(pr, p, onCompleted);
 		}))
@@ -1139,10 +1139,10 @@
 	{
 		if (!PlayFabManager.IsLoggedIn)
 		{
-			UnifiedPopup.Push(new YesNoPopup("$menu_loginwithplayfab_header", "$menu_loginwithplayfab_text", delegate
+			UnifiedPopup.Push(new YesNoPopup("$menu_loginwithplayfab_header", "$menu_loginwithplayfab_text", () =>
 			{
 				LoginWithPlayFab(onPlayFabLogin);
-			}, delegate
+			}, () =>
 			{
 				PlayFabManager.instance.SetShouldTryAutoLogin(value: false);
 				UnifiedPopup.Pop();
@@ -1192,7 +1192,7 @@
 	{
 		if (PlatformManager.DistributionPlatform.UIProvider.ResolvePrivilege == null && !UnifiedPopup.IsVisible())
 		{
-			UnifiedPopup.Push(new WarningPopup("$menu_privilegerequiredheader", "$menu_onlineprivilegetext", delegate
+			UnifiedPopup.Push(new WarningPopup("$menu_privilegerequiredheader", "$menu_onlineprivilegetext", () =>
 			{
 				RefreshWorldSelection();
 				UnifiedPopup.Pop();
@@ -1206,7 +1206,7 @@
 		{
 			string text = "";
 			text = " Steam";
-			UnifiedPopup.Push(new WarningPopup("$menu_logintext", "$menu_loginfailedtext" + text, delegate
+			UnifiedPopup.Push(new WarningPopup("$menu_logintext", "$menu_loginfailedtext" + text, () =>
 			{
 				RefreshWorldSelection();
 				UnifiedPopup.Pop();
@@ -1251,7 +1251,7 @@
 	{
 		if (toggleIsOn && !PlatformPrefs.GetBool("EulaAccepted"))
 		{
-			m_eulaWindow.Open(delegate(bool accepted)
+			m_eulaWindow.Open((bool accepted) =>
 			{
 				if (accepted)
 				{
@@ -1329,7 +1329,7 @@
 			Button component = gameObject.GetComponent<Button>();
 			component.onClick.RemoveAllListeners();
 			int index = i;
-			component.onClick.AddListener(delegate
+			component.onClick.AddListener(() =>
 			{
 				OnSelectWorld(index);
 			});
@@ -1492,7 +1492,7 @@
 		string text2 = m_newWorldSeed.text;
 		if (World.HaveWorld(text))
 		{
-			UnifiedPopup.Push(new WarningPopup(Localization.instance.Localize("$menu_newworldalreadyexists"), Localization.instance.Localize("$menu_newworldalreadyexistsmessage", text), delegate
+			UnifiedPopup.Push(new WarningPopup(Localization.instance.Localize("$menu_newworldalreadyexists"), Localization.instance.Localize("$menu_newworldalreadyexistsmessage", text), () =>
 			{
 				UnifiedPopup.Pop();
 			}, localizeText: false));
@@ -1548,7 +1548,7 @@
 		EventSystem.current.SetSelectedGameObject(m_serverOptions.m_doneButton);
 		if (PlatformPrefs.GetInt("ServerOptionsDisclaimer") == 0)
 		{
-			UnifiedPopup.Push(new WarningPopup("$menu_modifier_popup_title", "$menu_modifier_popup_text", delegate
+			UnifiedPopup.Push(new WarningPopup("$menu_modifier_popup_title", "$menu_modifier_popup_text", () =>
 			{
 				UnifiedPopup.Pop();
 			}));
@@ -1725,7 +1725,7 @@
 		}
 		void RestoreBackupPrompt(SaveWithBackups saveToRestore)
 		{
-			UnifiedPopup.Push(new YesNoPopup("$menu_restorebackup", "$menu_corruptsaverestore", delegate
+			UnifiedPopup.Push(new YesNoPopup("$menu_restorebackup", "$menu_corruptsaverestore", () =>
 			{
 				UnifiedPopup.Pop();
 				SaveSystem.RestoreBackupResult restoreBackupResult = SaveSystem.RestoreMostRecentBackup(saveToRestore);
@@ -1747,7 +1747,7 @@
 		}
 		void RestoreMetaFromBackupPrompt(SaveWithBackups saveToRestore)
 		{
-			UnifiedPopup.Push(new YesNoPopup("$menu_restorebackup", "$menu_missingmetarestore", delegate
+			UnifiedPopup.Push(new YesNoPopup("$menu_restorebackup", "$menu_missingmetarestore", () =>
 			{
 				UnifiedPopup.Pop();
 				SaveSystem.RestoreBackupResult restoreBackupResult = SaveSystem.RestoreMetaFromMostRecentBackup(saveToRestore.PrimaryFile);
@@ -1775,7 +1775,7 @@
 		string retryText = "";
 		int previousRetryCountdown = -1;
 		PlayFabManager.instance.SetShouldTryAutoLogin(value: true);
-		UnifiedPopup.Push(new CancelableTaskPopup(() => headerText, delegate
+		UnifiedPopup.Push(new CancelableTaskPopup(() => headerText, () =>
 		{
 			if (PlayFabManager.CurrentLoginState == LoginState.WaitingForRetry)
 			{
@@ -1788,14 +1788,14 @@
 				return retryText;
 			}
 			return loggingInText;
-		}, delegate
+		}, () =>
 		{
 			if (PlayFabManager.IsLoggedIn)
 			{
 				continueAction?.Invoke();
 			}
 			return PlayFabManager.IsLoggedIn;
-		}, delegate
+		}, () =>
 		{
 			UnifiedPopup.Pop();
 		}));
@@ -1846,7 +1846,7 @@
 		}
 		else
 		{
-			if (!VerifyHasMultiplayerPrivilege(delegate
+			if (!VerifyHasMultiplayerPrivilege((PrivilegeResult _, Privilege _) =>
 			{
 				VerifyPlayFabLoggedIn();
 				ZLog.LogWarning("You should always prevent JoinServer() from being called when user does not have online multiplayer privilege!");
@@ -1859,7 +1859,7 @@
 			ServerMatchmakingData serverMatchmakingData = MultiBackendMatchmaking.GetServerMatchmakingData(m_joinServer);
 			if (serverMatchmakingData.m_onlineStatus.IsOnline() && serverMatchmakingData.m_networkVersion != 40)
 			{
-				UnifiedPopup.Push(new WarningPopup("$error_incompatibleversion", (40 < serverMatchmakingData.m_networkVersion) ? "$error_needslocalupdatetojoin" : "$error_needsserverupdatetojoin", delegate
+				UnifiedPopup.Push(new WarningPopup("$error_incompatibleversion", (40 < serverMatchmakingData.m_networkVersion) ? "$error_needslocalupdatetojoin" : "$error_needsserverupdatetojoin", () =>
 				{
 					UnifiedPopup.Pop();
 				}));
@@ -1874,14 +1874,14 @@
 						PlatformManager.DistributionPlatform.UIProvider.ResolvePrivilege.Open(Privilege.CrossPlatformMultiplayer);
 						return;
 					}
-					UnifiedPopup.Push(new WarningPopup(Localization.instance.Localize("$error_failedconnect"), Localization.instance.Localize("$xbox_error_crossplayprivilege"), delegate
+					UnifiedPopup.Push(new WarningPopup(Localization.instance.Localize("$error_failedconnect"), Localization.instance.Localize("$xbox_error_crossplayprivilege"), () =>
 					{
 						UnifiedPopup.Pop();
 					}, localizeText: false));
 				}
 				else
 				{
-					UnifiedPopup.Push(new WarningPopup(Localization.instance.Localize("$error_failedconnect"), Localization.instance.Localize("$xbox_error_crossplayprivilege"), delegate
+					UnifiedPopup.Push(new WarningPopup(Localization.instance.Localize("$error_failedconnect"), Localization.instance.Localize("$xbox_error_crossplayprivilege"), () =>
 					{
 						UnifiedPopup.Pop();
 					}, localizeText: false));
@@ -1905,7 +1905,7 @@
 			{
 				ServerJoinDataDedicated serverJoin = m_joinServer.Dedicated;
 				ZNet.ResetServerHost();
-				MultiBackendMatchmaking.GetServerIPAsync(serverJoin, delegate(bool succeeded, IPv6Address? address)
+				MultiBackendMatchmaking.GetServerIPAsync(serverJoin, (bool succeeded, IPv6Address? address) =>
 				{
 					if (!succeeded || !address.HasValue)
 					{
@@ -1914,7 +1914,7 @@
 					IPEndPoint endPoint = new IPEndPoint(address.Value, serverJoin.m_port);
 					if (PlayFabManager.IsLoggedIn)
 					{
-						ZPlayFabMatchmaking.FindHostByIp(endPoint, delegate(PlayFabMatchmakingServerData result)
+						ZPlayFabMatchmaking.FindHostByIp(endPoint, (PlayFabMatchmakingServerData result) =>
 						{
 							if (result != null)
 							{
@@ -1925,7 +1925,7 @@
 							{
 								retries = 50;
 							}
-						}, delegate
+						}, (ZPLayFabMatchmakingFailReason failReason) =>
 						{
 							ZNet.SetServerHost(endPoint.m_address.ToString(), endPoint.m_port, OnlineBackendType.Steamworks);
 							ZLog.Log("Determined backend of dedicated server to be Steamworks");
@@ -2002,23 +2002,23 @@
 				{
 					video.m_unlocked = true;
 				}
-				GameObject obj = UnityEngine.Object.Instantiate(video.m_unlocked ? m_cinematicsEntry : m_cinematicsEntryLocked);
-				obj.transform.parent = parent;
-				obj.transform.localScale = Vector3.one;
-				obj.SetActive(value: true);
-				TextMeshProUGUI componentInChildren = obj.GetComponentInChildren<TextMeshProUGUI>();
+				GameObject gameObject = UnityEngine.Object.Instantiate(video.m_unlocked ? m_cinematicsEntry : m_cinematicsEntryLocked);
+				gameObject.transform.parent = parent;
+				gameObject.transform.localScale = Vector3.one;
+				gameObject.SetActive(value: true);
+				TextMeshProUGUI componentInChildren = gameObject.GetComponentInChildren<TextMeshProUGUI>();
 				if ((object)componentInChildren != null)
 				{
 					componentInChildren.text = (video.m_unlocked ? video.m_name : m_cinematicsLockedText);
 				}
-				Button component = obj.GetComponent<Button>();
+				Button component = gameObject.GetComponent<Button>();
 				if ((object)component == null)
 				{
 					continue;
 				}
 				if (video.m_unlocked)
 				{
-					component.onClick.AddListener(delegate
+					component.onClick.AddListener(() =>
 					{
 						OnCinematicsPlay(video.m_name);
 					});
@@ -2035,15 +2035,15 @@
 			Button button = null;
 			for (int num = 0; num < parent.childCount; num++)
 			{
-				Button obj2 = ((button != null) ? button : parent.GetChild(num).GetComponent<Button>());
+				Button button2 = ((button != null) ? button : parent.GetChild(num).GetComponent<Button>());
 				button = ((num + 1 >= parent.childCount) ? null : parent.GetChild(num + 1).GetComponent<Button>());
-				Navigation navigation = obj2.navigation;
+				Navigation navigation = button2.navigation;
 				navigation.selectOnUp = selectOnUp;
 				navigation.selectOnDown = button;
 				navigation.selectOnLeft = null;
 				navigation.selectOnRight = null;
-				obj2.navigation = navigation;
-				selectOnUp = obj2;
+				button2.navigation = navigation;
+				selectOnUp = button2;
 			}
 			m_cinematicsEntry.SetActive(value: false);
 			m_cinematicsEntryLocked.SetActive(value: false);
@@ -2055,10 +2055,10 @@
 			Button[] componentsInChildren = m_cinematicsMenuList.GetComponentsInChildren<Button>();
 			for (int num2 = 0; num2 < componentsInChildren.Length; num2++)
 			{
-				Button button2 = componentsInChildren[num2];
-				if (button2.interactable && m_selectedCinematicIndex == num2)
-				{
-					button2.Select();
+				Button button3 = componentsInChildren[num2];
+				if (button3.interactable && m_selectedCinematicIndex == num2)
+				{
+					button3.Select();
 					break;
 				}
 			}
@@ -2075,7 +2075,7 @@
 
 	public void OnCinematicsPlay(string name)
 	{
-		CinematicsManager.Play(name, delegate
+		CinematicsManager.Play(name, (CinematicsManager.VideoEntry v, bool s) =>
 		{
 			OnCinematicsStop();
 		});
@@ -2156,7 +2156,7 @@
 	private void Update()
 	{
 		ZInput.Update(Time.deltaTime);
-		Localization.instance.ReLocalizeVisible(base.transform);
+		Localization.instance.ReLocalizeVisible(transform);
 		UpdateGamepad();
 		UpdateKeyboard();
 		CheckPendingJoinRequest();
@@ -2468,7 +2468,7 @@
 		}
 		if (!PlatformPrefs.GetBool("EulaAccepted"))
 		{
-			m_eulaWindow.Open(delegate(bool accepted)
+			m_eulaWindow.Open((bool accepted) =>
 			{
 				if (accepted)
 				{
@@ -2488,7 +2488,7 @@
 
 	private void ProceedJoinRequest(ServerJoinData joinData)
 	{
-		if (VerifyHasMultiplayerPrivilege(delegate
+		if (VerifyHasMultiplayerPrivilege((PrivilegeResult _, Privilege _) =>
 		{
 			VerifyPlayFabLoggedIn();
 		}))
@@ -2627,11 +2627,11 @@
 		string header = (isConsole ? Utils.GetPlatformSpecificLocalizationKey("$menu_storagefull", localizeSwitch: false, localizePlayStation: true, localizeXbox: false) : "$menu_cloudstoragefull");
 		if (FileHelpers.LocalStorageSupportedAndAllowed)
 		{
-			UnifiedPopup.Push(new YesNoPopup(header, "$menu_cloudstoragefullworldprompt", delegate
+			UnifiedPopup.Push(new YesNoPopup(header, "$menu_cloudstoragefullworldprompt", () =>
 			{
 				UnifiedPopup.Pop();
 				OnNewWorldDone(forceLocal: true);
-			}, delegate
+			}, () =>
 			{
 				UnifiedPopup.Pop();
 			}));
@@ -2639,7 +2639,7 @@
 		else
 		{
 			string text = (isConsole ? Utils.GetPlatformSpecificLocalizationKey("$menu_storagefulloperationfailed", localizeSwitch: false, localizePlayStation: true, localizeXbox: false) : "$menu_cloudstoragefulloperationfailed");
-			UnifiedPopup.Push(new WarningPopup(header, text, delegate
+			UnifiedPopup.Push(new WarningPopup(header, text, () =>
 			{
 				UnifiedPopup.Pop();
 			}));
@@ -2652,11 +2652,11 @@
 		string header = (isConsole ? Utils.GetPlatformSpecificLocalizationKey("$menu_storagefull", localizeSwitch: false, localizePlayStation: true, localizeXbox: false) : "$menu_cloudstoragefull");
 		if (FileHelpers.LocalStorageSupportedAndAllowed)
 		{
-			UnifiedPopup.Push(new YesNoPopup(header, "$menu_cloudstoragefullcharacterprompt", delegate
+			UnifiedPopup.Push(new YesNoPopup(header, "$menu_cloudstoragefullcharacterprompt", () =>
 			{
 				UnifiedPopup.Pop();
 				OnNewCharacterDone(forceLocal: true);
-			}, delegate
+			}, () =>
 			{
 				UnifiedPopup.Pop();
 			}));
@@ -2664,7 +2664,7 @@
 		else
 		{
 			string text = (isConsole ? Utils.GetPlatformSpecificLocalizationKey("$menu_storagefulloperationfailed", localizeSwitch: false, localizePlayStation: true, localizeXbox: false) : "$menu_cloudstoragefulloperationfailed");
-			UnifiedPopup.Push(new WarningPopup(header, text, delegate
+			UnifiedPopup.Push(new WarningPopup(header, text, () =>
 			{
 				UnifiedPopup.Pop();
 			}));
@@ -2965,17 +2965,17 @@
 	public void OnButtonSettings()
 	{
 		m_mainMenu.SetActive(value: false);
-		m_settingsPopup = UnityEngine.Object.Instantiate(m_settingsPrefab, base.transform);
+		m_settingsPopup = UnityEngine.Object.Instantiate(m_settingsPrefab, transform);
 		Settings component = m_settingsPopup.GetComponent<Settings>();
-		component.SettingsClosed = (Action)Delegate.Combine(component.SettingsClosed, (Action)delegate
+		component.SettingsClosed = (Action)Delegate.Combine(component.SettingsClosed, (Action)(() =>
 		{
 			m_mainMenu?.SetActive(value: true);
-		});
+		}));
 	}
 
 	public void OnButtonFeedback()
 	{
-		UnityEngine.Object.Instantiate(m_feedbackPrefab, base.transform);
+		UnityEngine.Object.Instantiate(m_feedbackPrefab, transform);
 	}
 
 	public void OnButtonTwitter()
```

# `ServerListGui.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+21/-21` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ServerListGui.cs
+++ b/ServerListGui.cs
@@ -270,23 +270,23 @@
 			return;
 		}
 		m_initialized = true;
-		m_favoriteButton.onClick.AddListener(delegate
+		m_favoriteButton.onClick.AddListener(() =>
 		{
 			OnFavoriteServerButton();
 		});
-		m_removeButton.onClick.AddListener(delegate
+		m_removeButton.onClick.AddListener(() =>
 		{
 			OnRemoveServerButton();
 		});
-		m_upButton.onClick.AddListener(delegate
+		m_upButton.onClick.AddListener(() =>
 		{
 			OnMoveServerUpButton();
 		});
-		m_downButton.onClick.AddListener(delegate
+		m_downButton.onClick.AddListener(() =>
 		{
 			OnMoveServerDownButton();
 		});
-		m_filterInputField.onValueChanged.AddListener(delegate
+		m_filterInputField.onValueChanged.AddListener((string _) =>
 		{
 			OnServerFilterChanged(isTyping: true);
 		});
@@ -322,7 +322,7 @@
 		float x = (515f - 5f * (float)(m_serverLists.Count - 1)) / (float)m_serverLists.Count;
 		for (int j = 0; j < m_serverLists.Count; j++)
 		{
-			GameObject gameObject = UnityEngine.Object.Instantiate(m_serverListTab, base.transform);
+			GameObject gameObject = UnityEngine.Object.Instantiate(m_serverListTab, transform);
 			m_serverListTabs.Add(gameObject);
 			gameObject.transform.SetSiblingIndex(j);
 			gameObject.SetActive(value: true);
@@ -491,10 +491,10 @@
 	public void OnRemoveServerButton()
 	{
 		int selectedServer = GetSelectedServer();
-		UnifiedPopup.Push(new YesNoPopup("$menu_removeserver", CensorShittyWords.FilterUGC(CurrentServerListFiltered[selectedServer].m_serverName, UGCType.ServerName, default(PlatformUserID), 0L), delegate
+		UnifiedPopup.Push(new YesNoPopup("$menu_removeserver", CensorShittyWords.FilterUGC(CurrentServerListFiltered[selectedServer].m_serverName, UGCType.ServerName, default, 0L), () =>
 		{
 			OnRemoveServerConfirm();
-		}, delegate
+		}, () =>
 		{
 			UnifiedPopup.Pop();
 		}));
@@ -598,17 +598,17 @@
 				serverListElement = m_serverListElementPool.Pop();
 				serverListElement.m_element.SetActive(value: true);
 				m_serverListElements.Add(serverListElement);
-				serverListElement.m_button.onClick.AddListener(delegate
+				serverListElement.m_button.onClick.AddListener(() =>
 				{
 					OnSelectedServer(serverEntry.m_joinData);
 				});
 			}
 			else
 			{
-				GameObject obj = UnityEngine.Object.Instantiate(m_serverListElement, m_serverListRoot);
-				obj.SetActive(value: true);
-				serverListElement = new ServerListElement(obj);
-				serverListElement.m_button.onClick.AddListener(delegate
+				GameObject gameObject = UnityEngine.Object.Instantiate(m_serverListElement, m_serverListRoot);
+				gameObject.SetActive(value: true);
+				serverListElement = new ServerListElement(gameObject);
+				serverListElement.m_button.onClick.AddListener(() =>
 				{
 					OnSelectedServer(serverEntry.m_joinData);
 				});
@@ -908,7 +908,7 @@
 		{
 			ServerJoinDataDedicated newServerListEntryDedicated = new ServerJoinDataDedicated(text);
 			OnManualAddToFavoritesStart();
-			MultiBackendMatchmaking.GetServerIPAsync(newServerListEntryDedicated, delegate(bool success, IPv6Address? address)
+			MultiBackendMatchmaking.GetServerIPAsync(newServerListEntryDedicated, (bool success, IPv6Address? address) =>
 			{
 				if (success && address.HasValue)
 				{
@@ -918,14 +918,14 @@
 				{
 					if (newServerListEntryDedicated.IsURL)
 					{
-						UnifiedPopup.Push(new WarningPopup("$menu_addserverfailed", "$menu_addserverfaileddnslookup", delegate
+						UnifiedPopup.Push(new WarningPopup("$menu_addserverfailed", "$menu_addserverfaileddnslookup", () =>
 						{
 							UnifiedPopup.Pop();
 						}));
 					}
 					else
 					{
-						UnifiedPopup.Push(new WarningPopup("$menu_addserverfailed", "$menu_addserverfailedincorrectformatting", delegate
+						UnifiedPopup.Push(new WarningPopup("$menu_addserverfailed", "$menu_addserverfailedincorrectformatting", () =>
 						{
 							UnifiedPopup.Pop();
 						}));
@@ -936,7 +936,7 @@
 		}
 		else
 		{
-			UnifiedPopup.Push(new WarningPopup("$menu_addserverfailed", "$menu_addserverfailedincorrectformatting", delegate
+			UnifiedPopup.Push(new WarningPopup("$menu_addserverfailed", "$menu_addserverfailedincorrectformatting", () =>
 			{
 				UnifiedPopup.Pop();
 			}));
@@ -967,7 +967,7 @@
 	{
 		if (!serverData.m_joinData.IsValid || serverData.m_matchmakingData.m_networkVersion != 40)
 		{
-			UnifiedPopup.Push(new WarningPopup("$menu_addserverfailed", "$error_incompatibleversion", delegate
+			UnifiedPopup.Push(new WarningPopup("$menu_addserverfailed", "$error_incompatibleversion", () =>
 			{
 				UnifiedPopup.Pop();
 			}));
@@ -975,7 +975,7 @@
 		}
 		else if (!serverData.m_matchmakingData.IsCrossplay && !serverData.m_matchmakingData.IsRestrictedToOwnPlatform)
 		{
-			UnifiedPopup.Push(new WarningPopup("$menu_addserverfailed", "$error_platformexcluded", delegate
+			UnifiedPopup.Push(new WarningPopup("$menu_addserverfailed", "$error_platformexcluded", () =>
 			{
 				UnifiedPopup.Pop();
 			}));
@@ -989,7 +989,7 @@
 			}
 			else
 			{
-				UnifiedPopup.Push(new WarningPopup("$menu_addserverfailed", "$xbox_error_crossplayprivilege", delegate
+				UnifiedPopup.Push(new WarningPopup("$menu_addserverfailed", "$xbox_error_crossplayprivilege", () =>
 				{
 					UnifiedPopup.Pop();
 				}));
@@ -1007,7 +1007,7 @@
 	{
 		ZLog.Log("Failed to resolve join code for the following reason: " + failReason);
 		m_isAwaitingServerAdd = false;
-		UnifiedPopup.Push(new WarningPopup("$menu_addserverfailed", "$menu_addserverfailedresolvejoincode", delegate
+		UnifiedPopup.Push(new WarningPopup("$menu_addserverfailed", "$menu_addserverfailedresolvejoincode", () =>
 		{
 			UnifiedPopup.Pop();
 		}));
```

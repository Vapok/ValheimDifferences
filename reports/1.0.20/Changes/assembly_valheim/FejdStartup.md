# `FejdStartup.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Awake() [Method Body Modified]`
- `JoinServer() [Method Body Modified]`
- `SetupGui() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/FejdStartup.cs
+++ b/FejdStartup.cs
@@ -313,7 +313,7 @@
 		{
 			return;
 		}
-		ZLog.Log("Valheim version: " + Version.GetVersionString() + " (network version " + 40u + ")");
+		ZLog.Log("Valheim version: " + Version.GetVersionString() + " (network version " + 41u + ")");
 		Settings.ApplyStartupSettings();
 		WorldGenerator.Initialize(World.GetMenuWorld());
 		if (!Console.instance)
@@ -523,7 +523,7 @@
 		}
 		m_moddedText.SetActive(Game.isModded);
 		m_worldListBaseSize = m_worldListRoot.rect.height;
-		m_versionLabel.text = $"Version {Version.GetVersionString()} (n-{40u})";
+		m_versionLabel.text = $"Version {Version.GetVersionString()} (n-{41u})";
 		Localization.instance.Localize(transform);
 		Localization.OnLanguageChange = (Action)Delegate.Combine(Localization.OnLanguageChange, new Action(OnLanguageChange));
 	}
@@ -1857,9 +1857,9 @@
 				return;
 			}
 			ServerMatchmakingData serverMatchmakingData = MultiBackendMatchmaking.GetServerMatchmakingData(m_joinServer);
-			if (serverMatchmakingData.m_onlineStatus.IsOnline() && serverMatchmakingData.m_networkVersion != 40)
-			{
-				UnifiedPopup.Push(new WarningPopup("$error_incompatibleversion", (40 < serverMatchmakingData.m_networkVersion) ? "$error_needslocalupdatetojoin" : "$error_needsserverupdatetojoin", () =>
+			if (serverMatchmakingData.m_onlineStatus.IsOnline() && serverMatchmakingData.m_networkVersion != 41)
+			{
+				UnifiedPopup.Push(new WarningPopup("$error_incompatibleversion", (41 < serverMatchmakingData.m_networkVersion) ? "$error_needslocalupdatetojoin" : "$error_needsserverupdatetojoin", () =>
 				{
 					UnifiedPopup.Pop();
 				}));
```

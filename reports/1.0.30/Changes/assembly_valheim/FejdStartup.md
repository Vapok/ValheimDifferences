# `FejdStartup.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+49/-34` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `AutoJoinPlayFabServer() [Method Body Modified]`
- `AutoJoinServer() [Method Body Modified]`
- `AutoJoinServer() [Method Removed]`
- `Awake() [Method Body Modified]`
- `CliAutoJoinServer() [Method Body Modified]`
- `JoinServer() [Method Body Modified]`
- `ParseArguments() [Method Body Modified]`
- `QueueSettingSimulationDistance() [Method Body Modified]`
- `SetDemoMode() [Method Body Modified]`
- `SetupGui() [Method Body Modified]`
- `UpdateCursor() [Method Body Modified]`
- `private void AutoJoinPlayFabServer(string joinCode)`
- `private void AutoJoinServer(string joinCode)`
- `private void CliAutoJoinServer(string joinInfo)`

---

## 📝 Code Diff

```diff
--- a/FejdStartup.cs
+++ b/FejdStartup.cs
@@ -288,6 +288,8 @@
 
 	private bool m_autoConnectionInProgress;
 
+	private static bool m_hasJoinedThroughArguments = false;
+
 	public static Action HandlePendingInvite;
 
 	public static Action ResetPendingInvite;
@@ -313,7 +315,7 @@
 		{
 			return;
 		}
-		ZLog.Log("Valheim version: " + Version.GetVersionString() + " (network version " + 41u + ")");
+		ZLog.Log("Valheim version: " + Version.GetVersionString() + " (network version " + 42u + ")");
 		Settings.ApplyStartupSettings();
 		WorldGenerator.Initialize(World.GetMenuWorld());
 		if (!Console.instance)
@@ -524,7 +526,7 @@
 		}
 		m_moddedText.SetActive(Game.isModded);
 		m_worldListBaseSize = m_worldListRoot.rect.height;
-		m_versionLabel.text = $"Version {Version.GetVersionString()} (n-{41u})";
+		m_versionLabel.text = $"Version {Version.GetVersionString()} (n-{42u})";
 		Localization.instance.Localize(transform);
 		Localization.OnLanguageChange = (Action)Delegate.Combine(Localization.OnLanguageChange, new Action(OnLanguageChange));
 	}
@@ -595,36 +597,49 @@
 			{
 				SetDemoMode();
 			}
-			if (text == "-joinserverwithcharacter" && commandLineArgs.Length > i + 3)
-			{
-				m_joinServer = new ServerJoinData(new ServerJoinDataDedicated(commandLineArgs[i + 1]));
+			if (text == "-joinserverwithcharacter" && commandLineArgs.Length > i + 3 && !m_hasJoinedThroughArguments)
+			{
 				SelectCharacter(commandLineArgs[i + 2], FileHelpers.FileSource.Local);
 				m_instantStart = true;
+				m_hasJoinedThroughArguments = true;
+				CliAutoJoinServer(commandLineArgs[i + 1]);
+			}
+			if (text == "-password" && commandLineArgs.Length > i + 1)
+			{
+				ServerPassword = commandLineArgs[i + 1];
+			}
+			if (text == "-simulationdistance" && commandLineArgs.Length > i + 1)
+			{
+				if (int.TryParse(commandLineArgs[i + 1], out var result))
+				{
+					QueueSettingSimulationDistance(SimulationDistance.GetSimulationDistance(result));
+				}
+			}
+			else if (text == "-joincode" && commandLineArgs.Length > i + 1)
+			{
+				CliAutoJoinServer(commandLineArgs[i + 1]);
+			}
+		}
+	}
+
+	private void CliAutoJoinServer(string joinInfo)
+	{
+		Action autoJoin = null;
+		autoJoin = () =>
+		{
+			m_cliUpdateAction -= autoJoin;
+			ServerJoinDataUtils.GetAddressAndPortFromString(joinInfo, out var ipAddress, out var _);
+			if (!string.IsNullOrEmpty(ipAddress))
+			{
+				m_joinServer = new ServerJoinData(new ServerJoinDataDedicated(joinInfo));
 				JoinServer();
 			}
-			if (text == "-password" && commandLineArgs.Length > i + 1)
-			{
-				ServerPassword = commandLineArgs[i + 1];
-			}
-			if (text == "-simulationdistance" && commandLineArgs.Length > i + 1)
-			{
-				if (int.TryParse(commandLineArgs[i + 1], out var result))
-				{
-					QueueSettingSimulationDistance(SimulationDistance.GetSimulationDistance(result));
-				}
-			}
-			else if (text == "-joincode" && commandLineArgs.Length > i + 1)
-			{
-				string joinCode = commandLineArgs[i + 1];
-				Action autoJoin = null;
-				autoJoin = () =>
-				{
-					m_cliUpdateAction -= autoJoin;
-					AutoJoinServer(joinCode);
-				};
-				m_cliUpdateAction += autoJoin;
-			}
-		}
+			else
+			{
+				AutoJoinPlayFabServer(joinInfo);
+			}
+		};
+		m_cliUpdateAction += autoJoin;
 	}
 
 	private static void QueueSettingSimulationDistance(SimulationDistance simulationDistance)
@@ -644,7 +659,7 @@
 		DemoMode.Enable();
 	}
 
-	private void AutoJoinServer(string joinCode)
+	private void AutoJoinPlayFabServer(string joinCode)
 	{
 		if (PlayFabManager.instance == null)
 		{
@@ -1864,9 +1879,9 @@
 				return;
 			}
 			ServerMatchmakingData serverMatchmakingData = MultiBackendMatchmaking.GetServerMatchmakingData(m_joinServer);
-			if (serverMatchmakingData.m_onlineStatus.IsOnline() && serverMatchmakingData.m_networkVersion != 41)
-			{
-				UnifiedPopup.Push(new WarningPopup("$error_incompatibleversion", (41 < serverMatchmakingData.m_networkVersion) ? "$error_needslocalupdatetojoin" : "$error_needsserverupdatetojoin", () =>
+			if (serverMatchmakingData.m_onlineStatus.IsOnline() && serverMatchmakingData.m_networkVersion != 42)
+			{
+				UnifiedPopup.Push(new WarningPopup("$error_incompatibleversion", (42 < serverMatchmakingData.m_networkVersion) ? "$error_needslocalupdatetojoin" : "$error_needsserverupdatetojoin", () =>
 				{
 					UnifiedPopup.Pop();
 				}));
@@ -1918,7 +1933,7 @@
 					{
 						retries = 50;
 					}
-					IPEndPoint endPoint = new IPEndPoint(address.Value, serverJoin.m_port);
+					IPEndPoint endPoint = new IPEndPoint(address.GetValueOrDefault(), serverJoin.m_port);
 					if (PlayFabManager.IsLoggedIn)
 					{
 						ZPlayFabMatchmaking.FindHostByIp(endPoint, (PlayFabMatchmakingServerData result) =>
@@ -2151,7 +2166,7 @@
 
 	private void UpdateCursor()
 	{
-		ZCursor.LockState = ((!ZInput.IsMouseActive()) ? CursorLockMode.Locked : CursorLockMode.None);
+		ZCursor.LockState = ((!ZInput.IsMouseActive() || ZInput.IsExclusiveGamepadActive()) ? CursorLockMode.Locked : CursorLockMode.None);
 		ZCursor.Show();
 	}
 
```

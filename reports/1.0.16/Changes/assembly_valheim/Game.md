# `Game.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+11/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Game.cs
+++ b/Game.cs
@@ -357,7 +357,7 @@
 		if (!m_shuttingDown)
 		{
 			bool shouldExit = false;
-			save = ZNet.instance.EnoughDiskSpaceAvailable(out var exitGamePopupShown, exitGamePrompt: true, delegate(bool exit)
+			save = ZNet.instance.EnoughDiskSpaceAvailable(out var exitGamePopupShown, exitGamePrompt: true, (bool exit) =>
 			{
 				shouldExit = exit;
 				ContinueLogout(save, shouldExit, changeToStartScene);
@@ -1181,7 +1181,16 @@
 		{
 			m_pauseRotateFade = 0f;
 		}
-		Time.timeScale = (IsPaused() ? 0f : ((ZNet.instance.GetPeerConnections() > 0) ? 1f : m_timeScale));
+		float timeScale;
+		if (IsPaused())
+		{
+			timeScale = 0f;
+		}
+		else
+		{
+			timeScale = ((ZNet.instance.GetPeerConnections() > 0) ? 1f : m_timeScale);
+		}
+		Time.timeScale = timeScale;
 		if (IsPaused())
 		{
 			m_pauseTimer += Time.fixedUnscaledDeltaTime;
```

# `FejdStartup.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+12/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `private IEnumerator PlayIntroCinematic()`
- `private IEnumerator TryPlayIntroCinematic()`

---

## 📝 Code Diff

```diff
--- a/FejdStartup.cs
+++ b/FejdStartup.cs
@@ -16,7 +16,7 @@
 {
 	private delegate void ContinueAction();
 
-	private bool m_cinematicsInitialized;
+	public bool m_cinematicsInitialized;
 
 	private Vector3 camSpeed = Vector3.zero;
 
@@ -464,11 +464,16 @@
 		}
 		CheckShowChangelogNotice();
 		Player.m_debugMode = false;
-		StartCoroutine(PlayIntroCinematic());
-	}
-
-	private IEnumerator PlayIntroCinematic()
-	{
+		StartCoroutine(TryPlayIntroCinematic());
+	}
+
+	private IEnumerator TryPlayIntroCinematic()
+	{
+		if (PlatformPrefs.GetBool("SkipIntroCinematic"))
+		{
+			m_menuAnimator.SetTrigger("FadeIn");
+			yield break;
+		}
 		m_mainMenu.SetActive(value: false);
 		if (m_queuedJoinServer != ServerJoinData.None || MatchmakingManager.HasPendingInvite())
 		{
@@ -1967,7 +1972,7 @@
 				{
 					continue;
 				}
-				if (Terminal.m_cheat)
+				if (CinematicsManager.m_allUnlocked)
 				{
 					video.m_unlocked = true;
 				}
```

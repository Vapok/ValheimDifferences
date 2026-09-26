# `SteamManager.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SteamManager.cs
+++ b/SteamManager.cs
@@ -80,7 +80,7 @@
 	{
 		if (s_instance != null)
 		{
-			UnityEngine.Object.Destroy(base.gameObject);
+			UnityEngine.Object.Destroy(gameObject);
 			return;
 		}
 		s_instance = this;
@@ -96,7 +96,7 @@
 		{
 			throw new Exception("Tried to Initialize the SteamAPI twice in one session!");
 		}
-		UnityEngine.Object.DontDestroyOnLoad(base.gameObject);
+		UnityEngine.Object.DontDestroyOnLoad(gameObject);
 		if (!Packsize.Test())
 		{
 			Debug.LogError("[Steamworks.NET] Packsize Test returned false, the wrong version of Steamworks.NET is being run in this platform.", this);
```

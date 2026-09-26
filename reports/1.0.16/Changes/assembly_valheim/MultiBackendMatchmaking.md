# `MultiBackendMatchmaking.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MultiBackendMatchmaking.cs
+++ b/MultiBackendMatchmaking.cs
@@ -36,9 +36,9 @@
 	{
 		if ((object)s_instance == null)
 		{
-			GameObject obj = new GameObject("MultiBackendMatchmaking", typeof(MultiBackendMatchmaking));
-			s_instance = obj.GetComponent<MultiBackendMatchmaking>();
-			UnityEngine.Object.DontDestroyOnLoad(obj);
+			GameObject gameObject = new GameObject("MultiBackendMatchmaking", typeof(MultiBackendMatchmaking));
+			s_instance = gameObject.GetComponent<MultiBackendMatchmaking>();
+			UnityEngine.Object.DontDestroyOnLoad(gameObject);
 		}
 		s_instance.m_referenceCounter++;
 	}
@@ -147,7 +147,7 @@
 			throw new ArgumentException("Server has to be valid!");
 		}
 		source = ServerNameSource.ManuallySet;
-		serverNameAtTimePoint = default(ServerNameAtTimePoint);
+		serverNameAtTimePoint = default;
 		if ((object)s_instance == null)
 		{
 			ZLog.LogError(string.Format("{0} was null! Couldn't get server name for server {1}.", "s_instance", server));
```

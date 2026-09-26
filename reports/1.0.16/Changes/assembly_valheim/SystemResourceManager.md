# `SystemResourceManager.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SystemResourceManager.cs
+++ b/SystemResourceManager.cs
@@ -54,7 +54,7 @@
 		EnsureInitialized();
 		PushIsInLoadingScreen();
 		ILoadSceneAsyncOperation loadSceneAsyncOperation = SceneManager.LoadSceneAsync(scene, mode);
-		loadSceneAsyncOperation.Completed += delegate
+		loadSceneAsyncOperation.Completed += (ILoadSceneAsyncOperation _) =>
 		{
 			s_instance.PopIsInLoadingScreenDelayed();
 		};
@@ -84,7 +84,7 @@
 			throw new InvalidOperationException("Already had instance!");
 		}
 		s_instance = this;
-		UnityEngine.Object.DontDestroyOnLoad(base.gameObject);
+		UnityEngine.Object.DontDestroyOnLoad(gameObject);
 	}
 
 	private void OnDestroy()
```

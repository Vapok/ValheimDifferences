# `PlatformPrefs.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+3/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/PlatformPrefs.cs
+++ b/PlatformPrefs.cs
@@ -138,10 +138,7 @@
 		{
 			preferencesProvider.DeleteAll();
 		}
-		else
-		{
-			PlayerPrefs.DeleteAll();
-		}
+		PlayerPrefs.DeleteAll();
 	}
 
 	public static void Save()
@@ -156,7 +153,7 @@
 		s_saveSemaphore.Wait();
 		BackgroundWorker backgroundWorker = new BackgroundWorker();
 		bool savedSuccessfully = false;
-		backgroundWorker.DoWork += delegate
+		backgroundWorker.DoWork += (object sender, DoWorkEventArgs e) =>
 		{
 			if (data != null)
 			{
@@ -165,7 +162,7 @@
 			}
 			s_saveSemaphore.Release();
 		};
-		backgroundWorker.RunWorkerCompleted += delegate(object sender, RunWorkerCompletedEventArgs e)
+		backgroundWorker.RunWorkerCompleted += (object sender, RunWorkerCompletedEventArgs e) =>
 		{
 			if (e.Error != null)
 			{
```

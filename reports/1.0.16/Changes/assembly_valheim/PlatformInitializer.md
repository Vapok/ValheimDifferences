# `PlatformInitializer.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/PlatformInitializer.cs
+++ b/PlatformInitializer.cs
@@ -104,7 +104,7 @@
 	{
 		SetMainThreadName();
 		ParseArguments();
-		PlatformConfiguration platformConfiguration = default(PlatformConfiguration);
+		PlatformConfiguration platformConfiguration = default;
 		SteamManager.Initialize();
 		platformConfiguration.SetBool("managesteamruntime", value: false);
 		platformConfiguration.SetUIntArray("acceptedappids", new uint[2] { 1223920u, 892970u });
@@ -140,7 +140,7 @@
 		SuspendManager.Initialize();
 		if (PlatformManager.DistributionPlatform.AchievementManager != null)
 		{
-			PlatformManager.DistributionPlatform.AchievementManager.Initialize(delegate
+			PlatformManager.DistributionPlatform.AchievementManager.Initialize(() =>
 			{
 				Achievements.SetPlatformInitialized();
 			});
@@ -179,7 +179,7 @@
 		{
 			return;
 		}
-		PlatformManager.DistributionPlatform.SaveDataProvider.InitializeAsync(delegate(bool succeeded)
+		PlatformManager.DistributionPlatform.SaveDataProvider.InitializeAsync((bool succeeded) =>
 		{
 			if (succeeded)
 			{
@@ -237,7 +237,7 @@
 		}
 		byte[] data = null;
 		BackgroundWorker backgroundWorker = new BackgroundWorker();
-		backgroundWorker.DoWork += delegate
+		backgroundWorker.DoWork += (object args, DoWorkEventArgs e) =>
 		{
 			if (!FileHelpers.FileExistsCloud("Preferences"))
 			{
@@ -260,10 +260,10 @@
 				fileReader?.Dispose();
 			}
 		};
-		backgroundWorker.RunWorkerCompleted += delegate
+		backgroundWorker.RunWorkerCompleted += (object args, RunWorkerCompletedEventArgs e) =>
 		{
 			ZLog.Log("Finished loading preference data!");
-			preferences.InitializeAsync(data, delegate(bool succeeded)
+			preferences.InitializeAsync(data, (bool succeeded) =>
 			{
 				if (!succeeded)
 				{
```

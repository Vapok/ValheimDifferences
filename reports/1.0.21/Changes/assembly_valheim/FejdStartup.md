# `FejdStartup.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `OnWorldStart() [Method Body Modified]`
- `Start() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/FejdStartup.cs
+++ b/FejdStartup.cs
@@ -457,6 +457,7 @@
 		}
 		CensorShittyWords.UGCPopupShown = (Action)Delegate.Remove(CensorShittyWords.UGCPopupShown, new Action(OnUGCPopupShown));
 		CensorShittyWords.UGCPopupShown = (Action)Delegate.Combine(CensorShittyWords.UGCPopupShown, new Action(OnUGCPopupShown));
+		SaveSystem.InvalidateCache();
 		SaveSystem.ClearWorldListCache(reload: true);
 		if (Application.platform == RuntimePlatform.OSXPlayer || Application.platform == RuntimePlatform.OSXEditor)
 		{
@@ -1634,6 +1635,12 @@
 
 	public void OnWorldStart()
 	{
+		if (m_world.m_fileSource.IsNotCloud() && PlatformManager.DistributionPlatform.Platform == "Steam")
+		{
+			SaveSystem.InvalidateCache(SaveDataType.World);
+			SaveSystem.ForceRefreshLocalCache(SaveDataType.World);
+			UpdateWorldList(centerSelection: true);
+		}
 		if (!SaveSystem.CanSaveToCloudStorage(m_world, m_profiles[m_profileIndex]) || Menu.ExceedCloudStorageTest)
 		{
 			m_cloudStorageWarningNextSave.SetActive(value: true);
```

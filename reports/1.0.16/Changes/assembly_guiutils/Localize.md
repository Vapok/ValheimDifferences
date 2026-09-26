# `Localize.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_guiutils.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Localize.cs
+++ b/Localize.cs
@@ -5,7 +5,7 @@
 {
 	private void Start()
 	{
-		Localization.instance.Localize(base.transform);
+		Localization.instance.Localize(transform);
 		Localization.OnLanguageChange = (Action)Delegate.Combine(Localization.OnLanguageChange, new Action(RelocalizeAllUponChange));
 		ZInput.OnInputLayoutChanged += RelocalizeAllUponChange;
 	}
@@ -18,11 +18,11 @@
 
 	private void RelocalizeAllUponChange()
 	{
-		Localization.instance.ReLocalizeAll(base.transform);
+		Localization.instance.ReLocalizeAll(transform);
 	}
 
 	public void RefreshLocalization()
 	{
-		Localization.instance.ReLocalizeVisible(base.transform);
+		Localization.instance.ReLocalizeVisible(transform);
 	}
 }
```

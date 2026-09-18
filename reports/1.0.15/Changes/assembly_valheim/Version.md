# `Version.cs` Diff (`1.0.14` $\rightarrow$ `1.0.15`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Version.cs
+++ b/Version.cs
@@ -165,7 +165,7 @@
 
 	public static readonly GameVersion FirstVersionWithModifiers = new GameVersion(0, 217, 8);
 
-	public static GameVersion CurrentVersion { get; } = new GameVersion(1, 0, 14);
+	public static GameVersion CurrentVersion { get; } = new GameVersion(1, 0, 15);
 
 	public static string GetVersionString(bool includeMercurialHash = false)
 	{
```

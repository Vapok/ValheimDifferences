# `Version.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Version.cs
+++ b/Version.cs
@@ -143,7 +143,7 @@
 		Original = 1
 	}
 
-	public const uint c_networkVersion = 41u;
+	public const uint c_networkVersion = 42u;
 
 	public const int c_WorldGenVersion = 2;
 
@@ -169,7 +169,7 @@
 
 	public static readonly GameVersion FirstVersionWithModifiers = new GameVersion(0, 217, 8);
 
-	public static GameVersion CurrentVersion { get; } = new GameVersion(1, 0, 21);
+	public static GameVersion CurrentVersion { get; } = new GameVersion(1, 0, 30);
 
 	public static string GetVersionString(bool includeMercurialHash = false)
 	{
```

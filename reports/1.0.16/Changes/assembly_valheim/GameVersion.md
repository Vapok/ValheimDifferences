# `GameVersion.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/GameVersion.cs
+++ b/GameVersion.cs
@@ -6,7 +6,7 @@
 
 	public int m_patch;
 
-	public static GameVersion None => default(GameVersion);
+	public static GameVersion None => default;
 
 	public GameVersion(int major, int minor, int patch)
 	{
@@ -23,7 +23,7 @@
 
 	public static bool TryParseGameVersion(string versionString, out GameVersion version)
 	{
-		version = default(GameVersion);
+		version = default;
 		string[] array = versionString.Split('.');
 		if (array.Length < 2)
 		{
```

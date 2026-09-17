# `CinematicsManager.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CinematicsManager.cs
+++ b/CinematicsManager.cs
@@ -63,6 +63,8 @@
 
 	public static List<GameObject> m_hiders = new List<GameObject>();
 
+	public static bool m_allUnlocked = false;
+
 	private static List<GameObject> m_hidden = new List<GameObject>();
 
 	private static bool m_playing;
```

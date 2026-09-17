# `Achievements.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Achievements.cs
+++ b/Achievements.cs
@@ -484,7 +484,7 @@
 				}
 				if (achievement.m_lenientBuildAchievement)
 				{
-					Piece.CheckLenientBuildAchUnlocked(achievement, showPopup: false, useTagStats: false);
+					Piece.CheckLenientBuildAchUnlocked(achievement, afterLocalPlayerExists: false, useTagStats: false);
 				}
 				if (achievement.CheckUnlocked())
 				{
```

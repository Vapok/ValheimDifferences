# `Piece.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+12/-15` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `public static void CheckLenientBuildAchUnlocked(Achievement buildAchievement, bool afterLocalPlayerExists, bool useTagStats)`
- `public static void CheckLenientBuildAchUnlocked(Achievement buildAchievement, bool showPopup, bool useTagStats)`

---

## 📝 Code Diff

```diff
--- a/Piece.cs
+++ b/Piece.cs
@@ -558,27 +558,19 @@
 
 	private static void CheckBuildLeniencyUnlocks()
 	{
-		List<Achievement> list = new List<Achievement>();
 		foreach (AchievementList achievementList in Achievements.m_instance.m_achievementLists)
 		{
 			foreach (Achievement achievement in achievementList.m_achievements)
 			{
-				if (achievement.m_lenientBuildAchievement)
+				if (achievement.m_lenientBuildAchievement && !achievement.m_unlocked)
 				{
-					list.Add(achievement);
+					CheckLenientBuildAchUnlocked(achievement, afterLocalPlayerExists: true, useTagStats: true);
 				}
 			}
 		}
-		foreach (Achievement item in list)
-		{
-			if (!item.m_unlocked)
-			{
-				CheckLenientBuildAchUnlocked(item, showPopup: true, useTagStats: true);
-			}
-		}
-	}
-
-	public static void CheckLenientBuildAchUnlocked(Achievement buildAchievement, bool showPopup, bool useTagStats)
+	}
+
+	public static void CheckLenientBuildAchUnlocked(Achievement buildAchievement, bool afterLocalPlayerExists, bool useTagStats)
 	{
 		float num = 0f;
 		float[] array = new float[20];
@@ -611,10 +603,15 @@
 				num2 += num7;
 			}
 		}
-		if (num2 > num && Achievements.CanGetAchievements(Player.m_localPlayer != null && Player.m_localPlayer.NoCostCheat()))
+		bool flag = true;
+		if (afterLocalPlayerExists)
+		{
+			flag = Achievements.CanGetAchievements();
+		}
+		if ((num2 > num) & flag)
 		{
 			buildAchievement.m_unlocked = true;
-			Achievements.AchievementEvent(buildAchievement, synchronize: true, showPopup);
+			Achievements.AchievementEvent(buildAchievement, synchronize: true, afterLocalPlayerExists);
 		}
 	}
 
```

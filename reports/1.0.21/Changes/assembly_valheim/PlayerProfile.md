# `PlayerProfile.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `GetStat() [Method Body Modified]`
- `public float GetStat(PlayerStatType stat)`
- `public float GetStat(PlayerStatType stat, DifficultyRequirement difficultyReq)`

---

## 📝 Code Diff

```diff
--- a/PlayerProfile.cs
+++ b/PlayerProfile.cs
@@ -774,7 +774,7 @@
 	{
 		if (Terminal.m_showTests)
 		{
-			ZLog.Log($"Playerstat increment {stat} by {amount} (total: {GetStat(stat)})");
+			ZLog.Log($"Playerstat increment {stat} by {amount} (total: {GetStat(stat, DifficultyRequirement.Any)})");
 		}
 		m_playerStats[0].m_stats.IncrementOrSet(stat, amount);
 		if (Achievements.CanGetAchievements(cheated))
@@ -952,11 +952,11 @@
 		}
 	}
 
-	public float GetStat(PlayerStatType stat)
+	public float GetStat(PlayerStatType stat, DifficultyRequirement difficultyReq)
 	{
 		if (Achievements.CanGetAchievements())
 		{
-			return m_playerStats[Achievements.GetCurrentAchievementDifficultyIndex()][stat];
+			return m_playerStats[(int)difficultyReq][stat];
 		}
 		return m_playerStats[0][stat];
 	}
```

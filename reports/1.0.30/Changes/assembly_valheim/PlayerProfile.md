# `PlayerProfile.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `LoadPlayerFromDisk() [Method Body Modified]`
- `SavePlayerToDisk() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/PlayerProfile.cs
+++ b/PlayerProfile.cs
@@ -348,7 +348,7 @@
 				int currentAchievementDifficultyIndex = Achievements.GetCurrentAchievementDifficultyIndex();
 				m_playerStats[0].m_knownWorlds.IncrementOrSet(ZNet.instance.GetWorldName(), num);
 				m_playerStats[currentAchievementDifficultyIndex].m_knownWorlds.IncrementOrSet(ZNet.instance.GetWorldName(), num);
-				for (int l = 0; l < 53; l++)
+				for (int l = 0; l < 56; l++)
 				{
 					if (ZoneSystem.instance.GetGlobalKey((GlobalKeys)l, out string value))
 					{
@@ -543,7 +543,7 @@
 			if (player >= Version.Player.Stats2)
 			{
 				m_usedCheats = zPackage.ReadBool();
-				m_dateCreated = DateTimeOffset.FromUnixTimeSeconds(zPackage.ReadLong()).Date;
+				m_dateCreated = DateTimeOffset.FromUnixTimeSeconds(zPackage.ReadLong()).LocalDateTime;
 				if (player < Version.Player.DeepNorth && player != Version.Player.AbandonedDN)
 				{
 					int num15 = zPackage.ReadInt();
```

# `Piece.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `CheckClusteredBuildPieceStats() [Method Body Modified]`
- `CheckLenientBuildAchUnlocked() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Piece.cs
+++ b/Piece.cs
@@ -546,7 +546,7 @@
 			if (num > 0)
 			{
 				PlayerStatType stat = (PlayerStatType)(171 + k);
-				float stat2 = playerProfile.GetStat(stat);
+				float stat2 = playerProfile.GetStat(stat, DifficultyRequirement.Any);
 				if ((float)num > stat2)
 				{
 					playerProfile.SetStat(stat, num);
@@ -597,7 +597,7 @@
 			PlayerProfile playerProfile = Game.instance.GetPlayerProfile();
 			for (int j = 0; j < statTrigger.Count; j++)
 			{
-				float stat = playerProfile.GetStat(statTrigger[j].m_stat);
+				float stat = playerProfile.GetStat(statTrigger[j].m_stat, DifficultyRequirement.Any);
 				float amountAboveEquals = statTrigger[j].m_amountAboveEquals;
 				float num7 = Mathf.Min(stat, amountAboveEquals * num3);
 				num2 += num7;
```

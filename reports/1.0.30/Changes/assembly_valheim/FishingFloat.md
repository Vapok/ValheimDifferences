# `FishingFloat.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Catch() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/FishingFloat.cs
+++ b/FishingFloat.cs
@@ -287,6 +287,10 @@
 		ItemDrop component = fish.GetComponent<ItemDrop>();
 		if ((object)component != null && component.m_itemData.m_quality <= 6)
 		{
+			if (component.m_itemData.m_quality == 5 && Game.instance.GetPlayerProfile().GetStat(PlayerStatType.FishCaughtTier4, DifficultyRequirement.Any) == 0f)
+			{
+				Game.instance.IncrementPlayerStat(PlayerStatType.FishCaughtTier4);
+			}
 			Game.instance.IncrementPlayerStat((PlayerStatType)(161 + component.m_itemData.m_quality));
 		}
 		return text;
```

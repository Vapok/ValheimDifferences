# `Player.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+15/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `SurvivedOneDay() [Method Body Modified]`
- `UpdateBaseValue() [Method Body Modified]`
- `UpdateStats() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Player.cs
+++ b/Player.cs
@@ -1983,7 +1983,7 @@
 			m_baseValueUpdateTimer = 0f;
 			m_baseValue = EffectArea.GetBaseValue(transform.position, 20f);
 			m_comfortLevel = SE_Rested.CalculateComfortLevel(this);
-			float stat = Game.instance.GetPlayerProfile().GetStat(PlayerStatType.MaxComfort);
+			float stat = Game.instance.GetPlayerProfile().GetStat(PlayerStatType.MaxComfort, DifficultyRequirement.Any);
 			if ((float)m_comfortLevel > stat)
 			{
 				Game.instance.GetPlayerProfile().SetStat(PlayerStatType.MaxComfort, m_comfortLevel);
@@ -2165,7 +2165,16 @@
 		{
 			m_seman.RemoveStatusEffect(SEMan.s_statusEffectEncumbered);
 		}
-		if (!HardDeath() && m_seman.GetStatusEffect(SEMan.s_statusEffectSoftDeath) == null)
+		StatusEffect statusEffect = m_seman.GetStatusEffect(SEMan.s_statusEffectSoftDeath);
+		if (statusEffect != null)
+		{
+			float num6 = m_hardDeathCooldown - m_timeSinceDeath;
+			if (Mathf.Abs(statusEffect.m_ttl - statusEffect.GetDuration() - num6) > 0.1f)
+			{
+				statusEffect.SetDuration(statusEffect.m_ttl - num6);
+			}
+		}
+		else if (!HardDeath())
 		{
 			m_seman.AddStatusEffect(SEMan.s_statusEffectSoftDeath, resetTime: false, 0, 0f, -1);
 		}
@@ -3129,7 +3138,7 @@
 		if (Physics.Raycast(pos, Vector3.down, out var hitInfo, 200f, m_terrainMask))
 		{
 			ZLog.Log(gameObject.name + " placed at height " + hitInfo.distance);
-			float stat = Game.instance.GetPlayerProfile().GetStat(PlayerStatType.MaxBuildingHeight);
+			float stat = Game.instance.GetPlayerProfile().GetStat(PlayerStatType.MaxBuildingHeight, DifficultyRequirement.Any);
 			if (hitInfo.distance > stat && IsBuiltOnMyFoundation(pos))
 			{
 				Game.instance.GetPlayerProfile().SetStat(PlayerStatType.MaxBuildingHeight, hitInfo.distance, cheated);
@@ -3138,7 +3147,7 @@
 		ZLog.Log(gameObject.name + " placed at world height " + pos.y);
 		if (!Character.InInterior(pos))
 		{
-			float stat2 = Game.instance.GetPlayerProfile().GetStat(PlayerStatType.MaxBuildingHeightWorld);
+			float stat2 = Game.instance.GetPlayerProfile().GetStat(PlayerStatType.MaxBuildingHeightWorld, DifficultyRequirement.Any);
 			if (pos.y > stat2 && IsBuiltOnMyFoundation(pos))
 			{
 				Game.instance.GetPlayerProfile().SetStat(PlayerStatType.MaxBuildingHeightWorld, pos.y, cheated);
@@ -6624,8 +6633,8 @@
 	public void SurvivedOneDay()
 	{
 		Game.instance.IncrementPlayerStat(PlayerStatType.ConsecutiveDaysSurvived);
-		float stat = Game.instance.GetPlayerProfile().GetStat(PlayerStatType.ConsecutiveDaysSurvived);
-		float stat2 = Game.instance.GetPlayerProfile().GetStat(PlayerStatType.ConsecutiveDaysSurvivedMax);
+		float stat = Game.instance.GetPlayerProfile().GetStat(PlayerStatType.ConsecutiveDaysSurvived, DifficultyRequirement.Any);
+		float stat2 = Game.instance.GetPlayerProfile().GetStat(PlayerStatType.ConsecutiveDaysSurvivedMax, DifficultyRequirement.Any);
 		if (stat > stat2)
 		{
 			Game.instance.GetPlayerProfile().SetStat(PlayerStatType.ConsecutiveDaysSurvivedMax, stat);
```

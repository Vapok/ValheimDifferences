# `Character.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+14/-9` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `UpdateAshlandsWater() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Character.cs
+++ b/Character.cs
@@ -120,6 +120,8 @@
 
 	[Tooltip("Should this character be killed in order to unlock achievements (e.g. KillAllCreatures)")]
 	public Utils.AchievementInclusion m_killedForAchievements;
+
+	public List<string> m_summonNameBlockers = new List<string>();
 
 	[UnderlinedHeader("Movement & Physics", 0.5f, 0.5f, 0.5f)]
 	public float m_speed = 10f;
@@ -1173,15 +1175,18 @@
 			{
 				num *= m_heatWaterTouchMultiplier;
 			}
-			if (!(num < 0f))
-			{
-				num = Mathf.Clamp01(num);
-				float num2 = 1f - GetEquipmentHeatResistanceModifier();
-				m_ashlandsOceanHeatLevel += num * dt * m_heatBuildupWater * num2;
-				if (m_ashlandsOceanHeatLevel > m_heatLevelFirstDamageThreshold)
-				{
-					m_ashlandsOceanHeatLevel = m_heatLevelFirstDamageThreshold;
-				}
+			if (num < 0f && m_ashlandsOceanHeatLevel > 0f)
+			{
+				m_ashlandsOceanHeatLevel -= dt * m_heatCooldownBase;
+				m_ashlandsOceanHeatLevel = Mathf.Clamp01(m_ashlandsOceanHeatLevel);
+				return;
+			}
+			num = Mathf.Clamp01(num);
+			float num2 = 1f - GetEquipmentHeatResistanceModifier();
+			m_ashlandsOceanHeatLevel += num * dt * m_heatBuildupWater * num2;
+			if (m_ashlandsOceanHeatLevel > m_heatLevelFirstDamageThreshold)
+			{
+				m_ashlandsOceanHeatLevel = m_heatLevelFirstDamageThreshold;
 			}
 		}
 	}
```

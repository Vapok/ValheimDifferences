# `Character.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+34/-30` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Character.cs
+++ b/Character.cs
@@ -1022,17 +1022,18 @@
 	private void UpdateHeatEffects(float dt)
 	{
 		bool flag = false;
+		float num = Mathf.Max(m_ashlandsOceanHeatLevel, m_lavaHeatLevel);
 		if (!(Player.m_localPlayer == this))
 		{
 			return;
 		}
-		GameCamera.instance.m_heatDistortImageEffect.enabled = m_lavaHeatLevel > 0f;
-		GameCamera.instance.m_heatDistortImageEffect.m_intensity = (flag ? 0f : m_lavaHeatLevel);
+		GameCamera.instance.m_heatDistortImageEffect.enabled = num > 0f;
+		GameCamera.instance.m_heatDistortImageEffect.m_intensity = (flag ? 0f : num);
 		if (!m_lavaHeatEffects.HasEffects())
 		{
 			return;
 		}
-		if (m_lavaHeatLevel > 0f && m_lavaHeatParticles.Count == 0 && !IsDead())
+		if (num > 0f && m_lavaHeatParticles.Count == 0 && !IsDead())
 		{
 			GameObject[] array = m_lavaHeatEffects.Create(base.transform.position, Quaternion.identity, base.transform);
 			foreach (KeyValuePair<ParticleSystem, float> lavaHeatParticle in m_lavaHeatParticles)
@@ -1064,7 +1065,7 @@
 		{
 			if (lavaHeatParticle2.Key != null)
 			{
-				lavaHeatParticle2.Key.emissionRate = m_lavaHeatLevel * lavaHeatParticle2.Value;
+				lavaHeatParticle2.Key.emissionRate = num * lavaHeatParticle2.Value;
 			}
 		}
 		if (Player.m_localPlayer == this)
@@ -1073,7 +1074,7 @@
 			{
 				if (item3 != null)
 				{
-					item3.SetVolumeModifier(IsDead() ? 0f : m_lavaHeatLevel);
+					item3.SetVolumeModifier(IsDead() ? 0f : num);
 				}
 			}
 		}
@@ -1156,23 +1157,31 @@
 
 	private void UpdateAshlandsWater(float dt)
 	{
-		if (m_tolerateFire || !InWater())
-		{
-			return;
-		}
-		float num = WorldGenerator.GetAshlandsOceanGradient(base.transform.position);
-		if (!IsSwimming())
-		{
-			num *= m_heatWaterTouchMultiplier;
-		}
-		if (!(num < 0f))
-		{
-			num = Mathf.Clamp01(num);
-			float num2 = 1f - GetEquipmentHeatResistanceModifier();
-			m_ashlandsOceanHeatLevel += num * dt * m_heatBuildupWater * num2;
-			if (m_ashlandsOceanHeatLevel > m_heatLevelFirstDamageThreshold)
-			{
-				m_ashlandsOceanHeatLevel = m_heatLevelFirstDamageThreshold;
+		if (!InWater())
+		{
+			m_ashlandsOceanHeatLevel -= dt * m_heatCooldownBase;
+			m_ashlandsOceanHeatLevel = Mathf.Clamp01(m_ashlandsOceanHeatLevel);
+		}
+		else
+		{
+			if (m_tolerateFire)
+			{
+				return;
+			}
+			float num = WorldGenerator.GetAshlandsOceanGradient(base.transform.position);
+			if (!IsSwimming())
+			{
+				num *= m_heatWaterTouchMultiplier;
+			}
+			if (!(num < 0f))
+			{
+				num = Mathf.Clamp01(num);
+				float num2 = 1f - GetEquipmentHeatResistanceModifier();
+				m_ashlandsOceanHeatLevel += num * dt * m_heatBuildupWater * num2;
+				if (m_ashlandsOceanHeatLevel > m_heatLevelFirstDamageThreshold)
+				{
+					m_ashlandsOceanHeatLevel = m_heatLevelFirstDamageThreshold;
+				}
 			}
 		}
 	}
@@ -2437,14 +2446,9 @@
 			DamageText.instance.ShowText(mod, hit.m_point, totalDamage, IsPlayer() || IsTamed());
 		}
 		Character attacker = hit.GetAttacker();
-		if (attacker != null)
-		{
-			bool num = attacker is Player player && (player.GetInventory().CheatedDamagingItemEquipped() || player.IsDebugFlying() || player.InGodMode() || player.InGhostMode());
-			bool flag = attacker.m_nview.GetZDO().GetBool(ZDOVars.s_cheated);
-			if (((num | flag) || (hit != null && hit.m_damage.GetTotalDamage() > 99999f)) && !PlayerProfile.s_bypassCheatChecks)
-			{
-				m_nview.GetZDO().Set(ZDOVars.s_cheated, value: true);
-			}
+		if (attacker != null && attacker.IsPlayer() && !IsPlayer() && attacker is Player player && (player.GetInventory().CheatedDamagingItemEquipped() || player.IsDebugFlying() || player.InGodMode() || player.InGhostMode()) && !PlayerProfile.s_bypassCheatChecks)
+		{
+			m_nview.GetZDO().Set(ZDOVars.s_cheated, value: true);
 		}
 		float health = GetHealth();
 		if (health > 0f)
```

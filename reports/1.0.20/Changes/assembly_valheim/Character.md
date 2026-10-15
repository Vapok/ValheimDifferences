# `Character.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `OnDeath() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Character.cs
+++ b/Character.cs
@@ -2455,7 +2455,7 @@
 		Character attacker = hit.GetAttacker();
 		if (attacker != null && attacker.IsPlayer() && !IsPlayer() && attacker is Player player && (player.GetInventory().CheatedDamagingItemEquipped() || player.IsDebugFlying() || player.InGodMode() || player.InGhostMode()) && !PlayerProfile.s_bypassCheatChecks)
 		{
-			m_nview.GetZDO().Set(ZDOVars.s_cheated, value: true);
+			m_nview.GetZDO().SetCheated(isCheated: true);
 		}
 		float health = GetHealth();
 		if (health > 0f)
@@ -2915,7 +2915,7 @@
 	{
 		PlayerProfile playerProfile = Game.instance.GetPlayerProfile();
 		Character character = m_lastHit?.GetAttacker();
-		bool flag = m_nview.GetZDO().GetBool(ZDOVars.s_cheated);
+		bool flag = m_nview.GetZDO().IsCheated();
 		bool flag2 = character == Player.m_localPlayer;
 		if (flag2 && IsPlayer() && this is Player player)
 		{
```

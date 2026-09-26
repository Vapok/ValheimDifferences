# `HitData.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+34/-34` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/HitData.cs
+++ b/HitData.cs
@@ -758,64 +758,64 @@
 		serializeFlags = (HitDefaults.SerializeFlags)((int)serializeFlags | ((!m_skillRaiseAmount.Equals(1f)) ? 32768 : 0));
 		serializeFlags = (HitDefaults.SerializeFlags)((int)serializeFlags | ((!m_damage.m_nonPlayer.Equals(0f)) ? 65536 : 0));
 		pkg.Write((uint)serializeFlags);
-		if ((serializeFlags & HitDefaults.SerializeFlags.Damage) != HitDefaults.SerializeFlags.None)
+		if ((serializeFlags & HitDefaults.SerializeFlags.Damage) != 0)
 		{
 			pkg.Write(m_damage.m_damage);
 		}
-		if ((serializeFlags & HitDefaults.SerializeFlags.DamageBlunt) != HitDefaults.SerializeFlags.None)
+		if ((serializeFlags & HitDefaults.SerializeFlags.DamageBlunt) != 0)
 		{
 			pkg.Write(m_damage.m_blunt);
 		}
-		if ((serializeFlags & HitDefaults.SerializeFlags.DamageSlash) != HitDefaults.SerializeFlags.None)
+		if ((serializeFlags & HitDefaults.SerializeFlags.DamageSlash) != 0)
 		{
 			pkg.Write(m_damage.m_slash);
 		}
-		if ((serializeFlags & HitDefaults.SerializeFlags.DamagePierce) != HitDefaults.SerializeFlags.None)
+		if ((serializeFlags & HitDefaults.SerializeFlags.DamagePierce) != 0)
 		{
 			pkg.Write(m_damage.m_pierce);
 		}
-		if ((serializeFlags & HitDefaults.SerializeFlags.DamageChop) != HitDefaults.SerializeFlags.None)
+		if ((serializeFlags & HitDefaults.SerializeFlags.DamageChop) != 0)
 		{
 			pkg.Write(m_damage.m_chop);
 		}
-		if ((serializeFlags & HitDefaults.SerializeFlags.DamagePickaxe) != HitDefaults.SerializeFlags.None)
+		if ((serializeFlags & HitDefaults.SerializeFlags.DamagePickaxe) != 0)
 		{
 			pkg.Write(m_damage.m_pickaxe);
 		}
-		if ((serializeFlags & HitDefaults.SerializeFlags.DamageFire) != HitDefaults.SerializeFlags.None)
+		if ((serializeFlags & HitDefaults.SerializeFlags.DamageFire) != 0)
 		{
 			pkg.Write(m_damage.m_fire);
 		}
-		if ((serializeFlags & HitDefaults.SerializeFlags.DamageFrost) != HitDefaults.SerializeFlags.None)
+		if ((serializeFlags & HitDefaults.SerializeFlags.DamageFrost) != 0)
 		{
 			pkg.Write(m_damage.m_frost);
 		}
-		if ((serializeFlags & HitDefaults.SerializeFlags.DamageLightning) != HitDefaults.SerializeFlags.None)
+		if ((serializeFlags & HitDefaults.SerializeFlags.DamageLightning) != 0)
 		{
 			pkg.Write(m_damage.m_lightning);
 		}
-		if ((serializeFlags & HitDefaults.SerializeFlags.DamagePoison) != HitDefaults.SerializeFlags.None)
+		if ((serializeFlags & HitDefaults.SerializeFlags.DamagePoison) != 0)
 		{
 			pkg.Write(m_damage.m_poison);
 		}
-		if ((serializeFlags & HitDefaults.SerializeFlags.DamageSpirit) != HitDefaults.SerializeFlags.None)
+		if ((serializeFlags & HitDefaults.SerializeFlags.DamageSpirit) != 0)
 		{
 			pkg.Write(m_damage.m_spirit);
 		}
-		if ((serializeFlags & HitDefaults.SerializeFlags.DamageNonPlayer) != HitDefaults.SerializeFlags.None)
+		if ((serializeFlags & HitDefaults.SerializeFlags.DamageNonPlayer) != 0)
 		{
 			pkg.Write(m_damage.m_nonPlayer);
 		}
 		pkg.Write(m_toolTier);
-		if ((serializeFlags & HitDefaults.SerializeFlags.PushForce) != HitDefaults.SerializeFlags.None)
+		if ((serializeFlags & HitDefaults.SerializeFlags.PushForce) != 0)
 		{
 			pkg.Write(m_pushForce);
 		}
-		if ((serializeFlags & HitDefaults.SerializeFlags.BackstabBonus) != HitDefaults.SerializeFlags.None)
+		if ((serializeFlags & HitDefaults.SerializeFlags.BackstabBonus) != 0)
 		{
 			pkg.Write(m_backstabBonus);
 		}
-		if ((serializeFlags & HitDefaults.SerializeFlags.StaggerMultiplier) != HitDefaults.SerializeFlags.None)
+		if ((serializeFlags & HitDefaults.SerializeFlags.StaggerMultiplier) != 0)
 		{
 			pkg.Write(m_staggerMultiplier);
 		}
@@ -840,12 +840,12 @@
 		pkg.Write(m_point);
 		pkg.Write(m_dir);
 		pkg.Write(m_statusEffectHash);
-		if ((serializeFlags & HitDefaults.SerializeFlags.Attacker) != HitDefaults.SerializeFlags.None)
+		if ((serializeFlags & HitDefaults.SerializeFlags.Attacker) != 0)
 		{
 			pkg.Write(m_attacker);
 		}
 		pkg.Write((short)m_skill);
-		if ((serializeFlags & HitDefaults.SerializeFlags.SkillRaiseAmount) != HitDefaults.SerializeFlags.None)
+		if ((serializeFlags & HitDefaults.SerializeFlags.SkillRaiseAmount) != 0)
 		{
 			pkg.Write(m_skillRaiseAmount);
 		}
@@ -864,22 +864,22 @@
 	{
 		HitDefaults.SerializeFlags serializeFlags = HitDefaults.SerializeFlags.None;
 		serializeFlags = (HitDefaults.SerializeFlags)pkg.ReadUInt();
-		m_damage.m_damage = (((serializeFlags & HitDefaults.SerializeFlags.Damage) != HitDefaults.SerializeFlags.None) ? pkg.ReadSingle() : 0f);
-		m_damage.m_blunt = (((serializeFlags & HitDefaults.SerializeFlags.DamageBlunt) != HitDefaults.SerializeFlags.None) ? pkg.ReadSingle() : 0f);
-		m_damage.m_slash = (((serializeFlags & HitDefaults.SerializeFlags.DamageSlash) != HitDefaults.SerializeFlags.None) ? pkg.ReadSingle() : 0f);
-		m_damage.m_pierce = (((serializeFlags & HitDefaults.SerializeFlags.DamagePierce) != HitDefaults.SerializeFlags.None) ? pkg.ReadSingle() : 0f);
-		m_damage.m_chop = (((serializeFlags & HitDefaults.SerializeFlags.DamageChop) != HitDefaults.SerializeFlags.None) ? pkg.ReadSingle() : 0f);
-		m_damage.m_pickaxe = (((serializeFlags & HitDefaults.SerializeFlags.DamagePickaxe) != HitDefaults.SerializeFlags.None) ? pkg.ReadSingle() : 0f);
-		m_damage.m_fire = (((serializeFlags & HitDefaults.SerializeFlags.DamageFire) != HitDefaults.SerializeFlags.None) ? pkg.ReadSingle() : 0f);
-		m_damage.m_frost = (((serializeFlags & HitDefaults.SerializeFlags.DamageFrost) != HitDefaults.SerializeFlags.None) ? pkg.ReadSingle() : 0f);
-		m_damage.m_lightning = (((serializeFlags & HitDefaults.SerializeFlags.DamageLightning) != HitDefaults.SerializeFlags.None) ? pkg.ReadSingle() : 0f);
-		m_damage.m_poison = (((serializeFlags & HitDefaults.SerializeFlags.DamagePoison) != HitDefaults.SerializeFlags.None) ? pkg.ReadSingle() : 0f);
-		m_damage.m_spirit = (((serializeFlags & HitDefaults.SerializeFlags.DamageSpirit) != HitDefaults.SerializeFlags.None) ? pkg.ReadSingle() : 0f);
-		m_damage.m_nonPlayer = (((serializeFlags & HitDefaults.SerializeFlags.DamageNonPlayer) != HitDefaults.SerializeFlags.None) ? pkg.ReadSingle() : 0f);
+		m_damage.m_damage = (((serializeFlags & HitDefaults.SerializeFlags.Damage) != 0) ? pkg.ReadSingle() : 0f);
+		m_damage.m_blunt = (((serializeFlags & HitDefaults.SerializeFlags.DamageBlunt) != 0) ? pkg.ReadSingle() : 0f);
+		m_damage.m_slash = (((serializeFlags & HitDefaults.SerializeFlags.DamageSlash) != 0) ? pkg.ReadSingle() : 0f);
+		m_damage.m_pierce = (((serializeFlags & HitDefaults.SerializeFlags.DamagePierce) != 0) ? pkg.ReadSingle() : 0f);
+		m_damage.m_chop = (((serializeFlags & HitDefaults.SerializeFlags.DamageChop) != 0) ? pkg.ReadSingle() : 0f);
+		m_damage.m_pickaxe = (((serializeFlags & HitDefaults.SerializeFlags.DamagePickaxe) != 0) ? pkg.ReadSingle() : 0f);
+		m_damage.m_fire = (((serializeFlags & HitDefaults.SerializeFlags.DamageFire) != 0) ? pkg.ReadSingle() : 0f);
+		m_damage.m_frost = (((serializeFlags & HitDefaults.SerializeFlags.DamageFrost) != 0) ? pkg.ReadSingle() : 0f);
+		m_damage.m_lightning = (((serializeFlags & HitDefaults.SerializeFlags.DamageLightning) != 0) ? pkg.ReadSingle() : 0f);
+		m_damage.m_poison = (((serializeFlags & HitDefaults.SerializeFlags.DamagePoison) != 0) ? pkg.ReadSingle() : 0f);
+		m_damage.m_spirit = (((serializeFlags & HitDefaults.SerializeFlags.DamageSpirit) != 0) ? pkg.ReadSingle() : 0f);
+		m_damage.m_nonPlayer = (((serializeFlags & HitDefaults.SerializeFlags.DamageNonPlayer) != 0) ? pkg.ReadSingle() : 0f);
 		m_toolTier = pkg.ReadShort();
-		m_pushForce = (((serializeFlags & HitDefaults.SerializeFlags.PushForce) != HitDefaults.SerializeFlags.None) ? pkg.ReadSingle() : 0f);
-		m_backstabBonus = (((serializeFlags & HitDefaults.SerializeFlags.BackstabBonus) != HitDefaults.SerializeFlags.None) ? pkg.ReadSingle() : 1f);
-		m_staggerMultiplier = (((serializeFlags & HitDefaults.SerializeFlags.StaggerMultiplier) != HitDefaults.SerializeFlags.None) ? pkg.ReadSingle() : 1f);
+		m_pushForce = (((serializeFlags & HitDefaults.SerializeFlags.PushForce) != 0) ? pkg.ReadSingle() : 0f);
+		m_backstabBonus = (((serializeFlags & HitDefaults.SerializeFlags.BackstabBonus) != 0) ? pkg.ReadSingle() : 1f);
+		m_staggerMultiplier = (((serializeFlags & HitDefaults.SerializeFlags.StaggerMultiplier) != 0) ? pkg.ReadSingle() : 1f);
 		byte b = pkg.ReadByte();
 		m_dodgeable = (b & 1) != 0;
 		m_blockable = (b & 2) != 0;
@@ -888,9 +888,9 @@
 		m_point = pkg.ReadVector3();
 		m_dir = pkg.ReadVector3();
 		m_statusEffectHash = pkg.ReadInt();
-		m_attacker = (((serializeFlags & HitDefaults.SerializeFlags.Attacker) != HitDefaults.SerializeFlags.None) ? pkg.ReadZDOID() : HitDefaults.s_attackerDefault);
+		m_attacker = (((serializeFlags & HitDefaults.SerializeFlags.Attacker) != 0) ? pkg.ReadZDOID() : HitDefaults.s_attackerDefault);
 		m_skill = (Skills.SkillType)pkg.ReadShort();
-		m_skillRaiseAmount = (((serializeFlags & HitDefaults.SerializeFlags.SkillRaiseAmount) != HitDefaults.SerializeFlags.None) ? pkg.ReadSingle() : 1f);
+		m_skillRaiseAmount = (((serializeFlags & HitDefaults.SerializeFlags.SkillRaiseAmount) != 0) ? pkg.ReadSingle() : 1f);
 		m_weakSpot = (short)pkg.ReadChar();
 		m_skillLevel = pkg.ReadSingle();
 		m_itemLevel = pkg.ReadShort();
```

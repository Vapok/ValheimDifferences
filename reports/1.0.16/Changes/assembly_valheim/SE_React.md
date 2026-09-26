# `SE_React.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SE_React.cs
+++ b/SE_React.cs
@@ -25,7 +25,7 @@
 			IProjectile component = Object.Instantiate(m_spawnObj, m_character.GetCenterPoint(), Quaternion.identity).GetComponent<IProjectile>();
 			if (component != null)
 			{
-				HitData.DamageTypes damage = default(HitData.DamageTypes);
+				HitData.DamageTypes damage = default;
 				damage.Add(((Projectile)component).m_damage);
 				damage.Add(m_damagePerLevel, m_itemLevel - 1);
 				HitData hitData = new HitData();
```

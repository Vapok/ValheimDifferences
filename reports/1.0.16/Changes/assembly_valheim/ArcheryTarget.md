# `ArcheryTarget.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ArcheryTarget.cs
+++ b/ArcheryTarget.cs
@@ -102,7 +102,7 @@
 		{
 			if (projectile.m_type.HasFlag(projectileHitEffect.m_type))
 			{
-				projectileHitEffect.m_effect.Create(hitPoint, base.transform.rotation);
+				projectileHitEffect.m_effect.Create(hitPoint, transform.rotation);
 			}
 		}
 		if (m_raiseSkillMultiplier > 0f && owner != null)
@@ -154,15 +154,15 @@
 		}
 		if (flag)
 		{
-			m_fullBullsEyeEffect.Create(hitPoint, base.transform.rotation);
+			m_fullBullsEyeEffect.Create(hitPoint, transform.rotation);
 		}
 		else if (m_scoreListSize > 0 && m_lastScores[1] == m_points)
 		{
-			m_doubleBullsEyeEffect.Create(hitPoint, base.transform.rotation);
+			m_doubleBullsEyeEffect.Create(hitPoint, transform.rotation);
 		}
 		else
 		{
-			m_bullsEyeEffect.Create(hitPoint, base.transform.rotation);
+			m_bullsEyeEffect.Create(hitPoint, transform.rotation);
 		}
 	}
 
```

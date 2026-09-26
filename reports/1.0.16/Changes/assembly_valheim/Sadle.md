# `Sadle.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Sadle.cs
+++ b/Sadle.cs
@@ -63,7 +63,7 @@
 
 	private void Awake()
 	{
-		m_character = base.gameObject.GetComponentInParent<Character>();
+		m_character = gameObject.GetComponentInParent<Character>();
 		m_nview = m_character.GetComponent<ZNetView>();
 		m_tambable = m_character.GetComponent<Tameable>();
 		m_monsterAI = m_character.GetComponent<MonsterAI>();
@@ -122,16 +122,16 @@
 				hitData.m_pushForce = 10f;
 				hitData.m_hitType = HitData.HitType.Drowning;
 				m_character.Damage(hitData);
-				Vector3 position = base.transform.position;
+				Vector3 position = transform.position;
 				position.y = m_character.GetLiquidLevel();
-				m_drownEffects.Create(position, base.transform.rotation);
+				m_drownEffects.Create(position, transform.rotation);
 			}
 		}
 	}
 
 	public bool UpdateRiding(float dt)
 	{
-		if (!base.isActiveAndEnabled)
+		if (!isActiveAndEnabled)
 		{
 			return false;
 		}
@@ -374,7 +374,7 @@
 		{
 			if (allCharacterZDO.m_uid.UserID == user)
 			{
-				m_haveValidUser = Vector3.Distance(allCharacterZDO.GetPosition(), base.transform.position) < m_maxUseRange;
+				m_haveValidUser = Vector3.Distance(allCharacterZDO.GetPosition(), transform.position) < m_maxUseRange;
 				break;
 			}
 		}
```

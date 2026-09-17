# `Attack.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+18/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Attack.cs
+++ b/Attack.cs
@@ -429,10 +429,24 @@
 		{
 			m_zanim.SetTrigger(text = m_attackAnimation);
 		}
-		if (character.IsPlayer() && m_attackType != AttackType.None && m_currentAttackCainLevel == 0 && (Player.m_localPlayer == null || !Player.m_localPlayer.AttackTowardsPlayerLookDir || m_attackType == AttackType.Projectile))
-		{
-			character.transform.rotation = character.GetLookYaw();
-			m_body.rotation = character.transform.rotation;
+		if (character.IsPlayer() && m_attackType != AttackType.None && m_currentAttackCainLevel == 0)
+		{
+			bool num2 = Player.m_localPlayer == null || !Player.m_localPlayer.AttackTowardsPlayerLookDir;
+			bool flag = Player.m_localPlayer == null || Player.m_localPlayer.AttackTowardsPlayerLookDir;
+			if (num2 || m_attackType == AttackType.Projectile)
+			{
+				character.transform.rotation = character.GetLookYaw();
+				m_body.rotation = character.transform.rotation;
+			}
+			else if (flag)
+			{
+				Vector3 moveDir = character.GetMoveDir();
+				if (moveDir.sqrMagnitude > 0f)
+				{
+					character.transform.rotation = Quaternion.LookRotation(moveDir);
+					m_body.rotation = character.transform.rotation;
+				}
+			}
 		}
 		weapon.m_lastAttackTime = Time.time;
 		m_animEvent.ResetChain();
```

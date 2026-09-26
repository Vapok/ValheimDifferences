# `NpcTalk.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/NpcTalk.cs
+++ b/NpcTalk.cs
@@ -111,7 +111,7 @@
 		}
 		if (m_seeTarget)
 		{
-			float num = Vector3.Distance(m_targetPlayer.transform.position, base.transform.position);
+			float num = Vector3.Distance(m_targetPlayer.transform.position, transform.position);
 			if (!m_didGreet && num < m_greetRange)
 			{
 				m_didGreet = true;
@@ -133,7 +133,7 @@
 		}
 		m_lastTargetUpdate = Time.time;
 		m_targetPlayer = null;
-		Player closestPlayer = Player.GetClosestPlayer(base.transform.position, m_maxRange);
+		Player closestPlayer = Player.GetClosestPlayer(transform.position, m_maxRange);
 		if (!(closestPlayer == null) && (!m_monsterAI.IsEnemy(closestPlayer) || m_talkToEnemies))
 		{
 			m_seeTarget = m_monsterAI.CanSeeTarget(closestPlayer);
@@ -152,7 +152,7 @@
 
 	public void OnPrivateAreaAttacked(Character attacker)
 	{
-		if (attacker.IsPlayer() && m_monsterAI.IsAggravatable() && !m_monsterAI.IsAggravated() && Vector3.Distance(base.transform.position, attacker.transform.position) < m_maxRange)
+		if (attacker.IsPlayer() && m_monsterAI.IsAggravatable() && !m_monsterAI.IsAggravated() && Vector3.Distance(transform.position, attacker.transform.position) < m_maxRange)
 		{
 			QueueSay(m_privateAreaAlarm, "Angry", null);
 		}
@@ -196,7 +196,7 @@
 			Say(queuedSay.text, queuedSay.trigger);
 			if (queuedSay.m_effect != null)
 			{
-				queuedSay.m_effect.Create(base.transform.position, Quaternion.identity);
+				queuedSay.m_effect.Create(transform.position, Quaternion.identity);
 			}
 		}
 	}
@@ -204,7 +204,7 @@
 	private void Say(string text, string trigger)
 	{
 		m_lastTalkTime = Time.time;
-		Chat.instance.SetNpcText(base.gameObject, Vector3.up * m_offset, 20f, m_hideDialogDelay, "", text, large: false);
+		Chat.instance.SetNpcText(gameObject, Vector3.up * m_offset, 20f, m_hideDialogDelay, "", text, large: false);
 		if (trigger.Length > 0)
 		{
 			m_animator.SetTrigger(trigger);
@@ -213,6 +213,6 @@
 
 	private bool InFactionBase()
 	{
-		return PrivateArea.InsideFactionArea(base.transform.position, m_character.GetFaction());
+		return PrivateArea.InsideFactionArea(transform.position, m_character.GetFaction());
 	}
 }
```

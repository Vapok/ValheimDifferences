# `Tameable.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+29/-19` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Tameable.cs
+++ b/Tameable.cs
@@ -174,7 +174,17 @@
 
 	public string GetName()
 	{
-		return Localization.instance.Localize(m_character ? m_character.m_name : (((bool)m_nview && m_nview.IsValid()) ? m_nview.GetZDO().GetString(ZDOVars.s_tamedName, m_piece.m_name) : m_piece.m_name));
+		Localization instance = Localization.instance;
+		string text;
+		if ((bool)m_character)
+		{
+			text = m_character.m_name;
+		}
+		else
+		{
+			text = (((bool)m_nview && m_nview.IsValid()) ? m_nview.GetZDO().GetString(ZDOVars.s_tamedName, m_piece.m_name) : m_piece.m_name);
+		}
+		return instance.Localize(text);
 	}
 
 	public bool Interact(Humanoid user, bool hold, bool alt)
@@ -193,13 +203,13 @@
 			return true;
 		}
 		string hoverName = GetHoverName();
-		object msg;
+		string msg;
 		if (IsTamed())
 		{
 			if (Time.time - m_lastPetTime > 1f)
 			{
 				m_lastPetTime = Time.time;
-				m_petEffect.Create(base.transform.position, base.transform.rotation);
+				m_petEffect.Create(transform.position, transform.rotation);
 				if (m_commandable)
 				{
 					Command(user);
@@ -225,7 +235,7 @@
 		IL_010e:
 		return true;
 		IL_0106:
-		user.Message(MessageHud.MessageType.Center, (string)msg);
+		user.Message(MessageHud.MessageType.Center, msg);
 		goto IL_010e;
 	}
 
@@ -285,7 +295,7 @@
 		}
 		if (string.IsNullOrEmpty(resolvedAuthor) || resolvedAuthor == "host")
 		{
-			return CensorShittyWords.FilterUGC(text, UGCType.Text, default(PlatformUserID), 0L);
+			return CensorShittyWords.FilterUGC(text, UGCType.Text, default, 0L);
 		}
 		return CensorShittyWords.FilterUGC(text, UGCType.Text, new PlatformUserID(resolvedAuthor), 0L);
 	}
@@ -346,14 +356,14 @@
 		}
 		m_nview.GetZDO().Set(ZDOVars.s_haveSaddleHash, value: false);
 		m_nview.InvokeRPC(ZNetView.Everybody, "SetSaddle", false);
-		Vector3 flyDirection = userPoint - base.transform.position;
+		Vector3 flyDirection = userPoint - transform.position;
 		SpawnSaddle(flyDirection);
 		return true;
 	}
 
 	private void SpawnSaddle(Vector3 flyDirection)
 	{
-		Rigidbody component = UnityEngine.Object.Instantiate(m_saddleItem.gameObject, base.transform.TransformPoint(m_dropSaddleOffset), Quaternion.identity).GetComponent<Rigidbody>();
+		Rigidbody component = UnityEngine.Object.Instantiate(m_saddleItem.gameObject, transform.TransformPoint(m_dropSaddleOffset), Quaternion.identity).GetComponent<Rigidbody>();
 		if ((bool)component)
 		{
 			Vector3 up = Vector3.up;
@@ -407,7 +417,7 @@
 			}
 			else
 			{
-				m_sootheEffect.Create(base.transform.position, base.transform.rotation);
+				m_sootheEffect.Create(transform.position, transform.rotation);
 			}
 		}
 	}
@@ -418,8 +428,8 @@
 		if (m_nview.IsValid() && m_nview.IsOwner() && (bool)m_monsterAI && (bool)m_character && !IsTamed())
 		{
 			m_monsterAI.MakeTame();
-			m_tamedEffect.Create(base.transform.position, base.transform.rotation);
-			Player closestPlayer = Player.GetClosestPlayer(base.transform.position, 30f);
+			m_tamedEffect.Create(transform.position, transform.rotation);
+			Player closestPlayer = Player.GetClosestPlayer(transform.position, 30f);
 			if ((bool)closestPlayer)
 			{
 				closestPlayer.Message(MessageHud.MessageType.Center, m_character.m_name + " $hud_tamedone");
@@ -570,7 +580,7 @@
 	{
 		if (IsHungry())
 		{
-			m_sootheEffect.Create(m_character ? m_character.GetCenterPoint() : base.transform.position, Quaternion.identity);
+			m_sootheEffect.Create(m_character ? m_character.GetCenterPoint() : transform.position, Quaternion.identity);
 		}
 		ResetFeedingTimer();
 	}
@@ -583,7 +593,7 @@
 		}
 		float remainingTime = GetRemainingTime();
 		s_nearbyPlayers.Clear();
-		Player.GetPlayersInRange(base.transform.position, m_tamingSpeedMultiplierRange, s_nearbyPlayers);
+		Player.GetPlayersInRange(transform.position, m_tamingSpeedMultiplierRange, s_nearbyPlayers);
 		foreach (Player s_nearbyPlayer in s_nearbyPlayers)
 		{
 			if (s_nearbyPlayer.GetSEMan().HaveStatusAttribute(StatusEffect.StatusAttribute.TamingBoost))
@@ -631,7 +641,7 @@
 		if (m_nview.IsValid() && m_nview.IsOwner() && m_unsummonDistance > 0f && (bool)m_monsterAI)
 		{
 			GameObject followTarget = m_monsterAI.GetFollowTarget();
-			if ((bool)followTarget && Vector3.Distance(followTarget.transform.position, base.gameObject.transform.position) > m_unsummonDistance)
+			if ((bool)followTarget && Vector3.Distance(followTarget.transform.position, gameObject.transform.position) > m_unsummonDistance)
 			{
 				UnSummon();
 			}
@@ -672,20 +682,20 @@
 				continue;
 			}
 			ZNetView component2 = item.GetComponent<ZNetView>();
-			object obj2;
+			string text2;
 			if ((object)component2 != null)
 			{
 				ZDO zDO = component2.GetZDO();
 				if (zDO != null)
 				{
-					obj2 = zDO.GetString(ZDOVars.s_follow);
+					text2 = zDO.GetString(ZDOVars.s_follow);
 					goto IL_00b7;
 				}
 			}
-			obj2 = "";
+			text2 = "";
 			goto IL_00b7;
 			IL_00b7:
-			if ((string)obj2 == text)
+			if (text2 == text)
 			{
 				MonsterAI component3 = item.GetComponent<MonsterAI>();
 				if ((object)component3 != null)
@@ -716,10 +726,10 @@
 
 	private void RPC_UnSummon(long sender)
 	{
-		m_unSummonEffect.Create(base.gameObject.transform.position, base.gameObject.transform.rotation);
+		m_unSummonEffect.Create(gameObject.transform.position, gameObject.transform.rotation);
 		if (m_nview.IsValid() && m_nview.IsOwner())
 		{
-			ZNetScene.instance.Destroy(base.gameObject);
+			ZNetScene.instance.Destroy(gameObject);
 		}
 	}
 }
```

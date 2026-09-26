# `Door.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+9/-9` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Door.cs
+++ b/Door.cs
@@ -64,11 +64,11 @@
 		{
 			if (state != 0)
 			{
-				m_openEffects.Create(base.transform.position, base.transform.rotation);
+				m_openEffects.Create(transform.position, transform.rotation);
 			}
 			else
 			{
-				m_closeEffects.Create(base.transform.position, base.transform.rotation);
+				m_closeEffects.Create(transform.position, transform.rotation);
 			}
 			m_animator.SetInteger("state", state);
 		}
@@ -101,7 +101,7 @@
 		{
 			return "";
 		}
-		if (m_checkGuardStone && !PrivateArea.CheckAccess(base.transform.position, 0f, flash: false))
+		if (m_checkGuardStone && !PrivateArea.CheckAccess(transform.position, 0f, flash: false))
 		{
 			return Localization.instance.Localize(m_name + "\n$piece_noaccess");
 		}
@@ -131,7 +131,7 @@
 		{
 			return false;
 		}
-		if (m_checkGuardStone && !PrivateArea.CheckAccess(base.transform.position))
+		if (m_checkGuardStone && !PrivateArea.CheckAccess(transform.position))
 		{
 			return true;
 		}
@@ -139,7 +139,7 @@
 		{
 			if (!HaveKey(character))
 			{
-				m_lockedEffects.Create(base.transform.position, base.transform.rotation);
+				m_lockedEffects.Create(transform.position, transform.rotation);
 				if (Game.m_worldLevel > 0 && HaveKey(character, matchWorldLevel: false))
 				{
 					character.Message(MessageHud.MessageType.Center, Localization.instance.Localize("$msg_ng_the_x") + m_keyItem.m_itemData.m_shared.m_name + Localization.instance.Localize("$msg_ng_x_is_too_low"));
@@ -156,7 +156,7 @@
 			}
 			character.Message(MessageHud.MessageType.Center, Localization.instance.Localize("$msg_door_usingkey", m_keyItem.m_itemData.m_shared.m_name));
 		}
-		Vector3 normalized = (character.transform.position - base.transform.position).normalized;
+		Vector3 normalized = (character.transform.position - transform.position).normalized;
 		Game.instance.IncrementPlayerStat((m_nview.GetZDO().GetInt(ZDOVars.s_state) == 0) ? PlayerStatType.DoorsOpened : PlayerStatType.DoorsClosed);
 		Open(normalized);
 		return true;
@@ -164,7 +164,7 @@
 
 	private void Open(Vector3 userDir)
 	{
-		bool flag = Vector3.Dot(base.transform.forward, userDir) < 0f;
+		bool flag = Vector3.Dot(transform.forward, userDir) < 0f;
 		m_nview.InvokeRPC("UseDoor", flag);
 	}
 
@@ -176,7 +176,7 @@
 			{
 				return false;
 			}
-			if (m_checkGuardStone && !PrivateArea.CheckAccess(base.transform.position))
+			if (m_checkGuardStone && !PrivateArea.CheckAccess(transform.position))
 			{
 				return true;
 			}
@@ -185,7 +185,7 @@
 			{
 				user.GetInventory().RemoveItem(item);
 			}
-			Vector3 normalized = (user.transform.position - base.transform.position).normalized;
+			Vector3 normalized = (user.transform.position - transform.position).normalized;
 			Open(normalized);
 			return true;
 		}
```

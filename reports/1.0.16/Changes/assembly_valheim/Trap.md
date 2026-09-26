# `Trap.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Trap.cs
+++ b/Trap.cs
@@ -56,7 +56,7 @@
 		m_piece = GetComponent<Piece>();
 		if (!m_aoe)
 		{
-			ZLog.LogError("Trap '" + base.gameObject.name + "' is missing AOE!");
+			ZLog.LogError("Trap '" + gameObject.name + "' is missing AOE!");
 		}
 		m_aoe.gameObject.SetActive(value: false);
 		if ((bool)m_nview)
@@ -124,7 +124,7 @@
 		{
 			return "";
 		}
-		if (!PrivateArea.CheckAccess(base.transform.position, 0f, flash: false))
+		if (!PrivateArea.CheckAccess(transform.position, 0f, flash: false))
 		{
 			return Localization.instance.Localize(m_name + "\n$piece_noaccess");
 		}
@@ -150,7 +150,7 @@
 		{
 			return false;
 		}
-		if (!PrivateArea.CheckAccess(base.transform.position))
+		if (!PrivateArea.CheckAccess(transform.position))
 		{
 			return true;
 		}
@@ -197,7 +197,7 @@
 		case 1:
 			if (idOfClientModifyingState == ZNet.GetUID())
 			{
-				m_armEffects.Create(base.transform.position, base.transform.rotation);
+				m_armEffects.Create(transform.position, transform.rotation);
 				Game.instance.IncrementPlayerStat(PlayerStatType.TrapArmed);
 			}
 			m_tempTriggeringHumanoid = null;
@@ -224,7 +224,7 @@
 				Game.instance.IncrementPlayerStat(PlayerStatType.TrapTriggered);
 				break;
 			}
-			m_onReceiveOwnershipActions.Add(delegate
+			m_onReceiveOwnershipActions.Add(() =>
 			{
 				Game.instance.IncrementPlayerStat(PlayerStatType.TrapTriggered);
 			});
@@ -249,8 +249,8 @@
 		}
 		m_nview.GetZDO().Set(ZDOVars.s_state, 2);
 		m_nview.GetZDO().Set(ZDOVars.s_triggered, (float)ZNet.instance.GetTimeSeconds());
-		UnityEngine.Object.Instantiate(m_aoe.gameObject, base.transform).SetActive(value: true);
-		m_triggerEffects.Create(base.transform.position, base.transform.rotation);
+		UnityEngine.Object.Instantiate(m_aoe.gameObject, transform).SetActive(value: true);
+		m_triggerEffects.Create(transform.position, transform.rotation);
 	}
 
 	private void RPC_RequestStateChange(long senderID, int value)
```

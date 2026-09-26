# `Turret.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+15/-15` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Turret.cs
+++ b/Turret.cs
@@ -240,7 +240,7 @@
 		}
 		else if (!HasAmmo())
 		{
-			forward = base.transform.forward + new Vector3(0f, -0.3f, 0f);
+			forward = transform.forward + new Vector3(0f, -0.3f, 0f);
 		}
 		else
 		{
@@ -249,12 +249,12 @@
 			{
 				m_scan = 0f;
 			}
-			forward = Quaternion.Euler(0f, base.transform.rotation.eulerAngles.y + (float)((m_scan - m_noTargetScanRate > 0f) ? 1 : (-1)) * m_horizontalAngle, 0f) * Vector3.forward;
+			forward = Quaternion.Euler(0f, transform.rotation.eulerAngles.y + (float)((m_scan - m_noTargetScanRate > 0f) ? 1 : (-1)) * m_horizontalAngle, 0f) * Vector3.forward;
 		}
 		forward.Normalize();
 		Quaternion quaternion = Quaternion.LookRotation(forward, Vector3.up);
 		Vector3 eulerAngles = quaternion.eulerAngles;
-		float y2 = base.transform.rotation.eulerAngles.y;
+		float y2 = transform.rotation.eulerAngles.y;
 		eulerAngles.y -= y2;
 		if (m_horizontalAngle >= 0f)
 		{
@@ -302,17 +302,17 @@
 		m_updateTargetTimer -= dt;
 		if (m_updateTargetTimer <= 0f)
 		{
-			m_updateTargetTimer = (Character.IsCharacterInRange(base.transform.position, 40f) ? m_updateTargetIntervalNear : m_updateTargetIntervalFar);
-			Character character = BaseAI.FindClosestCreature(base.transform, m_eye.transform.position, 0f, m_viewDistance, m_horizontalAngle, alerted: false, mistVision: false, passiveAggresive: true, m_targetPlayers, (m_targetItems.Count > 0) ? m_targetTamedConfig : m_targetTamed, m_targetEnemies, m_targetCharacters);
+			m_updateTargetTimer = (Character.IsCharacterInRange(transform.position, 40f) ? m_updateTargetIntervalNear : m_updateTargetIntervalFar);
+			Character character = BaseAI.FindClosestCreature(transform, m_eye.transform.position, 0f, m_viewDistance, m_horizontalAngle, alerted: false, mistVision: false, passiveAggresive: true, m_targetPlayers, (m_targetItems.Count > 0) ? m_targetTamedConfig : m_targetTamed, m_targetEnemies, m_targetCharacters);
 			if (character != m_target)
 			{
 				if ((bool)character)
 				{
-					m_newTargetEffect.Create(base.transform.position, base.transform.rotation);
+					m_newTargetEffect.Create(transform.position, transform.rotation);
 				}
 				else
 				{
-					m_lostTargetEffect.Create(base.transform.position, base.transform.rotation);
+					m_lostTargetEffect.Create(transform.position, transform.rotation);
 				}
 				m_nview.InvokeRPC(ZNetView.Everybody, "RPC_SetTarget", character ? character.GetZDOID() : ZDOID.None);
 			}
@@ -321,7 +321,7 @@
 		{
 			ZLog.Log("Target is gone");
 			m_nview.InvokeRPC(ZNetView.Everybody, "RPC_SetTarget", ZDOID.None);
-			m_lostTargetEffect.Create(base.transform.position, base.transform.rotation);
+			m_lostTargetEffect.Create(transform.position, transform.rotation);
 		}
 	}
 
@@ -345,7 +345,7 @@
 		{
 			m_nview.GetZDO().Set(ZDOVars.s_ammo, num - num2);
 		}
-		ZLog.Log($"Turret '{base.name}' is shooting {num2} projectiles, ammo: {num}/{m_maxAmmo}");
+		ZLog.Log($"Turret '{name}' is shooting {num2} projectiles, ammo: {num}/{m_maxAmmo}");
 		for (int i = 0; i < num2; i++)
 		{
 			Vector3 forward = transform.forward;
@@ -412,7 +412,7 @@
 		bool flag = IsCoolingDown();
 		if (!m_turretBodyArmed.activeInHierarchy && !flag)
 		{
-			m_reloadEffect.Create(base.transform.position, base.transform.rotation);
+			m_reloadEffect.Create(transform.position, transform.rotation);
 		}
 		m_turretBodyArmed.SetActive(!flag);
 		m_turretBodyUnarmed.SetActive(flag);
@@ -424,7 +424,7 @@
 		GameObject prefab = ZNetScene.instance.GetPrefab(ammoType);
 		if (!prefab)
 		{
-			ZLog.LogWarning("Turret '" + base.name + "' is trying to fire but has no ammo or default ammo!");
+			ZLog.LogWarning("Turret '" + name + "' is trying to fire but has no ammo or default ammo!");
 			return null;
 		}
 		return prefab.GetComponent<ItemDrop>().m_itemData;
@@ -440,7 +440,7 @@
 		{
 			return Localization.instance.Localize(m_name);
 		}
-		if (!PrivateArea.CheckAccess(base.transform.position, 0f, flash: false))
+		if (!PrivateArea.CheckAccess(transform.position, 0f, flash: false))
 		{
 			return Localization.instance.Localize(m_name + "\n$piece_noaccess");
 		}
@@ -518,7 +518,7 @@
 			}
 			SetTargets();
 			Player.m_localPlayer.Message(MessageHud.MessageType.Center, Localization.instance.Localize("$piece_turret_target_set_msg " + ((m_targetCharacters.Count == 0) ? "$piece_turret_target_everything" : m_targetsText)));
-			m_setTargetEffect.Create(base.transform.position, base.transform.rotation);
+			m_setTargetEffect.Create(transform.position, transform.rotation);
 			Game.instance.IncrementPlayerStat(PlayerStatType.TurretTrophySet);
 			return true;
 		}
@@ -629,7 +629,7 @@
 			GameObject prefab = ZNetScene.instance.GetPrefab(ammoType);
 			for (int i = 0; i < ammo; i++)
 			{
-				Vector3 position = base.transform.position + Vector3.up + UnityEngine.Random.insideUnitSphere * 0.3f;
+				Vector3 position = transform.position + Vector3.up + UnityEngine.Random.insideUnitSphere * 0.3f;
 				Quaternion rotation = Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f);
 				UnityEngine.Object.Instantiate(prefab, position, rotation);
 			}
@@ -655,7 +655,7 @@
 	{
 		if ((bool)m_marker && m_marker.isActiveAndEnabled)
 		{
-			m_marker.m_start = base.transform.rotation.eulerAngles.y - m_horizontalAngle;
+			m_marker.m_start = transform.rotation.eulerAngles.y - m_horizontalAngle;
 			m_marker.m_turns = m_horizontalAngle * 2f / 360f;
 		}
 	}
```

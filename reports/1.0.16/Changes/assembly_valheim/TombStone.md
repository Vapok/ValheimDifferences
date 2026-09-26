# `TombStone.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+12/-12` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/TombStone.cs
+++ b/TombStone.cs
@@ -43,7 +43,7 @@
 		if (m_nview.IsOwner() && m_nview.GetZDO().GetLong(ZDOVars.s_timeOfDeath, 0L) == 0L)
 		{
 			m_nview.GetZDO().Set(ZDOVars.s_timeOfDeath, ZNet.instance.GetTime().Ticks);
-			m_nview.GetZDO().Set(ZDOVars.s_spawnPoint, base.transform.position);
+			m_nview.GetZDO().Set(ZDOVars.s_spawnPoint, transform.position);
 		}
 		InvokeRepeating("UpdateDespawn", m_updateDt, m_updateDt);
 	}
@@ -192,7 +192,7 @@
 			if (!m_container.IsInUse() && m_container.GetInventory().NrOfItems() <= 0)
 			{
 				GiveBoost();
-				m_removeEffect.Create(base.transform.position, base.transform.rotation);
+				m_removeEffect.Create(transform.position, transform.rotation);
 				m_nview.Destroy();
 			}
 		}
@@ -224,22 +224,22 @@
 	{
 		if (!m_body)
 		{
-			m_body = FloatingTerrain.GetBody(base.gameObject);
-		}
-		Vector3 vec = m_nview.GetZDO().GetVec3(ZDOVars.s_spawnPoint, base.transform.position);
-		if (Utils.DistanceXZ(vec, base.transform.position) > 4f)
+			m_body = FloatingTerrain.GetBody(gameObject);
+		}
+		Vector3 vec = m_nview.GetZDO().GetVec3(ZDOVars.s_spawnPoint, transform.position);
+		if (Utils.DistanceXZ(vec, transform.position) > 4f)
 		{
 			ZLog.Log("Tombstone moved too far from spawn position, reseting position");
-			base.transform.position = vec;
+			transform.position = vec;
 			m_body.position = vec;
 			m_body.linearVelocity = Vector3.zero;
 		}
-		float groundHeight = ZoneSystem.instance.GetGroundHeight(base.transform.position);
-		if (base.transform.position.y < groundHeight - 1f)
-		{
-			Vector3 position = base.transform.position;
+		float groundHeight = ZoneSystem.instance.GetGroundHeight(transform.position);
+		if (transform.position.y < groundHeight - 1f)
+		{
+			Vector3 position = transform.position;
 			position.y = groundHeight + 0.5f;
-			base.transform.position = position;
+			transform.position = position;
 			m_body.position = position;
 			m_body.linearVelocity = Vector3.zero;
 		}
```

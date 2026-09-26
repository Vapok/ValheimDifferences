# `Valkyrie.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+22/-14` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valkyrie.cs
+++ b/Valkyrie.cs
@@ -51,7 +51,7 @@
 		m_animator = GetComponentInChildren<Animator>();
 		if (!m_nview.IsOwner())
 		{
-			base.enabled = false;
+			enabled = false;
 			return;
 		}
 		ZLog.Log("Setting up valkyrie ");
@@ -61,7 +61,7 @@
 		m_targetPoint = Player.m_localPlayer.transform.position + new Vector3(0f, m_dropHeight, 0f);
 		Vector3 position = m_targetPoint + vector * m_startDistance;
 		position.y = m_startAltitude;
-		base.transform.position = position;
+		transform.position = position;
 		m_descentStart = m_targetPoint + vector * m_startDescentDistance + vector2 * 200f;
 		m_descentStart.y = m_descentAltitude;
 		Vector3 vector3 = m_targetPoint - m_descentStart;
@@ -70,7 +70,7 @@
 		m_flyAwayPoint = m_targetPoint + vector3 * m_startDescentDistance;
 		m_flyAwayPoint.y = m_startAltitude;
 		SyncPlayer(doNetworkSync: true);
-		ZLog.Log("World pos " + base.transform.position.ToString() + "   " + ZNet.instance.GetReferencePosition().ToString());
+		ZLog.Log("World pos " + transform.position.ToString() + "   " + ZNet.instance.GetReferencePosition().ToString());
 	}
 
 	private void HideText()
@@ -111,8 +111,16 @@
 			m_notifiedMultiplayerStart = true;
 			ZNet.instance.SetMultiplayerUsageStart();
 		}
-		Vector3 vector = (m_droppedPlayer ? m_flyAwayPoint : ((!m_descent) ? m_descentStart : m_targetPoint));
-		if (Utils.DistanceXZ(vector, base.transform.position) < 0.5f)
+		Vector3 vector;
+		if (m_droppedPlayer)
+		{
+			vector = m_flyAwayPoint;
+		}
+		else
+		{
+			vector = ((!m_descent) ? m_descentStart : m_targetPoint);
+		}
+		if (Utils.DistanceXZ(vector, transform.position) < 0.5f)
 		{
 			if (!m_descent)
 			{
@@ -129,38 +137,38 @@
 				m_nview.Destroy();
 			}
 		}
-		Vector3 normalized = (vector - base.transform.position).normalized;
-		Vector3 vector2 = base.transform.position + normalized * 25f;
+		Vector3 normalized = (vector - transform.position).normalized;
+		Vector3 vector2 = transform.position + normalized * 25f;
 		if (ZoneSystem.instance.GetGroundHeight(vector2, out var height))
 		{
 			vector2.y = Mathf.Max(vector2.y, height + m_dropHeight);
 		}
-		Vector3 normalized2 = (vector2 - base.transform.position).normalized;
+		Vector3 normalized2 = (vector2 - transform.position).normalized;
 		Quaternion quaternion = Quaternion.LookRotation(normalized2);
 		Vector3 to = normalized2;
 		to.y = 0f;
 		to.Normalize();
-		Vector3 forward = base.transform.forward;
+		Vector3 forward = transform.forward;
 		forward.y = 0f;
 		forward.Normalize();
 		float num = Mathf.Clamp(Vector3.SignedAngle(forward, to, Vector3.up), -30f, 30f) / 30f;
 		quaternion = Quaternion.Euler(0f, 0f, num * 45f) * quaternion;
 		float num2 = (m_droppedPlayer ? (m_turnRate * 4f) : m_turnRate);
-		base.transform.rotation = Quaternion.RotateTowards(base.transform.rotation, quaternion, num2 * dt);
-		Vector3 vector3 = base.transform.forward * m_speed;
-		Vector3 vector4 = base.transform.position + vector3 * dt;
+		transform.rotation = Quaternion.RotateTowards(transform.rotation, quaternion, num2 * dt);
+		Vector3 vector3 = transform.forward * m_speed;
+		Vector3 vector4 = transform.position + vector3 * dt;
 		if (ZoneSystem.instance.GetGroundHeight(vector4, out var height2))
 		{
 			vector4.y = Mathf.Max(vector4.y, height2 + m_dropHeight);
 		}
-		base.transform.position = vector4;
+		transform.position = vector4;
 	}
 
 	public void DropPlayer(bool destroy = false)
 	{
 		ZLog.Log("We are here");
 		m_droppedPlayer = true;
-		Vector3 forward = base.transform.forward;
+		Vector3 forward = transform.forward;
 		forward.y = 0f;
 		forward.Normalize();
 		Player.m_localPlayer.transform.rotation = Quaternion.LookRotation(forward);
```

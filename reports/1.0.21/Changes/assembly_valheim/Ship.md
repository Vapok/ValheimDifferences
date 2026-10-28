# `Ship.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+9/-10` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `CustomFixedUpdate() [Method Body Modified]`
- `IsSailUp() [Method Body Modified]`
- `UpdateRudder() [Method Body Modified]`
- `UpdateSail() [Method Body Modified]`
- `UpdateSailSize() [Method Body Modified]`
- `private void UpdateSail(float dt)`
- `private void UpdateSail(float dt, bool haveControllingPlayer)`
- `private void UpdateSailSize(float dt)`
- `private void UpdateSailSize(float dt, bool haveControllingPlayer)`

---

## 📝 Code Diff

```diff
--- a/Ship.cs
+++ b/Ship.cs
@@ -311,7 +311,7 @@
 	{
 		bool flag = HaveControllingPlayer();
 		UpdateControlls(fixedDeltaTime);
-		UpdateSail(fixedDeltaTime);
+		UpdateSail(fixedDeltaTime, flag);
 		UpdateRudder(fixedDeltaTime, flag);
 		if ((bool)m_nview && !m_nview.IsOwner())
 		{
@@ -599,9 +599,9 @@
 		return true;
 	}
 
-	private void UpdateSail(float dt)
-	{
-		UpdateSailSize(dt);
+	private void UpdateSail(float dt, bool haveControllingPlayer)
+	{
+		UpdateSailSize(dt, haveControllingPlayer);
 		Vector3 windDir = EnvMan.instance.GetWindDir();
 		windDir = Vector3.Cross(Vector3.Cross(windDir, transform.up), transform.up);
 		if (m_speed == Speed.Full || m_speed == Speed.Half)
@@ -642,7 +642,7 @@
 		m_rudderObject.transform.localRotation = Quaternion.Slerp(m_rudderObject.transform.localRotation, b, 0.5f);
 	}
 
-	private void UpdateSailSize(float dt)
+	private void UpdateSailSize(float dt, bool haveControllingPlayer)
 	{
 		if (m_hasSail)
 		{
@@ -665,11 +665,10 @@
 				position = m_sailMidfurledPosition.position;
 				position2 = m_sailUnfurledPosition.position;
 			}
-			if (!flag && m_sailWasInPosition)
-			{
-				ZDOID zDOID = ((Player.m_localPlayer.GetPlayerID() == m_shipControlls.GetUser()) ? Player.m_localPlayer.GetZDOID() : ZDOID.None);
-				Debug.Log($"now swapping sailpos, using {m_changeSailPosEffect.m_effectPrefabs[0].m_prefab.name}, for this local player: {zDOID}");
-				m_changeSailPosEffect.Create(transform.position, Quaternion.identity, null, 1f, -1, zDOID);
+			if ((!flag && m_sailWasInPosition) & haveControllingPlayer)
+			{
+				ZDOID gamepadEffectsExclusiveToPlayer = ((Player.m_localPlayer.GetPlayerID() == m_shipControlls.GetUser()) ? Player.m_localPlayer.GetZDOID() : ZDOID.None);
+				m_changeSailPosEffect.Create(transform.position, Quaternion.identity, null, 1f, -1, gamepadEffectsExclusiveToPlayer);
 			}
 			float t = Utils.Frac(Mathf.Clamp(m_sailPosition, 0f, 0.999f) * 2f);
 			m_sailBottomTransform.position = Vector3.Lerp(position, position2, t);
```

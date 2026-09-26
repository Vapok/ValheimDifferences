# `Leviathan.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Leviathan.cs
+++ b/Leviathan.cs
@@ -64,7 +64,7 @@
 		{
 			return;
 		}
-		float liquidLevel = Floating.GetLiquidLevel(base.transform.position, m_waveScale);
+		float liquidLevel = Floating.GetLiquidLevel(transform.position, m_waveScale);
 		if (m_alignToWaterLevel)
 		{
 			if (liquidLevel > -100f)
@@ -91,7 +91,7 @@
 	{
 		if (UnityEngine.Random.value <= m_hitReactionChance && !m_left)
 		{
-			m_reactionEffects.Create(base.transform.position, base.transform.rotation);
+			m_reactionEffects.Create(transform.position, transform.rotation);
 			m_zanimator.SetTrigger("shake");
 			Invoke("Leave", m_leaveDelay);
 		}
@@ -102,7 +102,7 @@
 		if (m_nview.IsValid() && m_nview.IsOwner() && !m_left)
 		{
 			m_left = true;
-			m_leaveEffects.Create(base.transform.position, base.transform.rotation);
+			m_leaveEffects.Create(transform.position, transform.rotation);
 			m_zanimator.SetTrigger("dive");
 			m_nview.GetZDO().Set(ZDOVars.s_dead, value: true);
 			m_nview.InvokeRPC(ZNetView.Everybody, "RPC_Left");
@@ -111,7 +111,7 @@
 
 	private void RPC_Left(long sender)
 	{
-		if (Utils.DistanceXZ(base.transform.position, Player.m_localPlayer.transform.position) < m_playerCheckSize)
+		if (Utils.DistanceXZ(transform.position, Player.m_localPlayer.transform.position) < m_playerCheckSize)
 		{
 			Game.instance.IncrementPlayerStat(m_leaveStat);
 		}
@@ -119,7 +119,7 @@
 
 	private void OnDestroy()
 	{
-		if (m_left && m_nview.IsValid() && !m_nview.IsOwner() && Player.GetPlayersInRangeXZ(base.transform.position, 40f) == 0)
+		if (m_left && m_nview.IsValid() && !m_nview.IsOwner() && Player.GetPlayersInRangeXZ(transform.position, 40f) == 0)
 		{
 			m_nview.Destroy();
 		}
@@ -127,6 +127,6 @@
 
 	private void OnDrawGizmos()
 	{
-		Utils.DrawGizmoCircle(base.transform.position, m_playerCheckSize, 32);
+		Utils.DrawGizmoCircle(transform.position, m_playerCheckSize, 32);
 	}
 }
```

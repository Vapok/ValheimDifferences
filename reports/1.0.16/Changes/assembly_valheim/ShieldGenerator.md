# `ShieldGenerator.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+10/-10` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ShieldGenerator.cs
+++ b/ShieldGenerator.cs
@@ -116,9 +116,9 @@
 
 	private void Start()
 	{
-		if (Player.IsPlacementGhost(base.gameObject))
-		{
-			base.enabled = false;
+		if (Player.IsPlacementGhost(gameObject))
+		{
+			enabled = false;
 			m_isPlacementGhost = true;
 			return;
 		}
@@ -221,14 +221,14 @@
 		UpdateAttackCharge();
 		if ((bool)m_attackObject)
 		{
-			GameObject gameObject = UnityEngine.Object.Instantiate(m_attackObject, base.transform.position, base.transform.rotation);
+			GameObject gameObject = UnityEngine.Object.Instantiate(m_attackObject, transform.position, transform.rotation);
 			if (!m_damagePlayers)
 			{
 				gameObject.GetComponentInChildren<Aoe>()?.Setup(Player.m_localPlayer, Vector3.zero, 1f, null, null, null);
 			}
 		}
-		m_attackEffects.Create(base.transform.position, base.transform.rotation);
-		m_fuelAddedEffects.Create(base.transform.position, base.transform.rotation, base.transform);
+		m_attackEffects.Create(transform.position, transform.rotation);
+		m_fuelAddedEffects.Create(transform.position, transform.rotation, transform);
 	}
 
 	private void RPC_HitNow(long sender)
@@ -260,7 +260,7 @@
 			m_shieldDomeEffect.RemoveShield(this);
 			m_instances.Remove(this);
 			m_instanceChangeID++;
-			Character.SetupContinuousEffect(base.transform, base.transform.position, enabledEffect: false, m_shieldLowLoop, ref m_lowLoopInstances);
+			Character.SetupContinuousEffect(transform, transform.position, enabledEffect: false, m_shieldLowLoop, ref m_lowLoopInstances);
 		}
 	}
 
@@ -340,7 +340,7 @@
 		{
 			float fuel = GetFuel();
 			SetFuel(fuel + 1f);
-			m_fuelAddedEffects.Create(base.transform.position, base.transform.rotation, base.transform);
+			m_fuelAddedEffects.Create(transform.position, transform.rotation, transform);
 		}
 	}
 
@@ -421,7 +421,7 @@
 		}
 		if (m_shieldLowLoopFuelStart > 0f && m_nview.IsOwner())
 		{
-			Character.SetupContinuousEffect(base.transform, base.transform.position, m_lastFuel > 0f && m_lastFuel < m_shieldLowLoopFuelStart, m_shieldLowLoop, ref m_lowLoopInstances);
+			Character.SetupContinuousEffect(transform, transform.position, m_lastFuel > 0f && m_lastFuel < m_shieldLowLoopFuelStart, m_shieldLowLoop, ref m_lowLoopInstances);
 		}
 		if (m_nview.IsOwner() && fuel >= (float)m_maxFuel && m_nview.GetZDO().GetLong(ZDOVars.s_startTime, 0L) <= 0)
 		{
@@ -561,7 +561,7 @@
 			SetFuel(GetFuel() - num);
 		}
 		m_nview.InvokeRPC(ZNetView.Everybody, "RPC_HitNow");
-		m_shieldHitEffects.Create(position, Quaternion.LookRotation(base.transform.position.DirTo(position)));
+		m_shieldHitEffects.Create(position, Quaternion.LookRotation(transform.position.DirTo(position)));
 		UpdateShield();
 	}
 
```

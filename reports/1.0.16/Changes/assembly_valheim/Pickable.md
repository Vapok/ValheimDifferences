# `Pickable.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+12/-12` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Pickable.cs
+++ b/Pickable.cs
@@ -106,7 +106,7 @@
 			{
 				m_nview.ClaimOwnership();
 				m_nview.Destroy();
-				ZLog.Log("Destroying old picked " + base.name);
+				ZLog.Log("Destroying old picked " + name);
 			}
 		}
 	}
@@ -216,8 +216,8 @@
 				if (UnityEngine.Random.value < skillFactor * m_maxLevelBonusChance)
 				{
 					num = m_bonusYieldAmount;
-					DamageText.instance.ShowText(DamageText.TextType.Bonus, base.transform.position + GetSpawnOffset(), $"+{num}", player: true);
-					m_bonusEffect.Create(base.transform.position, Quaternion.identity, null, 1f, -1, character.GetZDOID());
+					DamageText.instance.ShowText(DamageText.TextType.Bonus, transform.position + GetSpawnOffset(), $"+{num}", player: true);
+					m_bonusEffect.Create(transform.position, Quaternion.identity, null, 1f, -1, character.GetZDOID());
 					ZLog.Log("Bonus food picked!");
 				}
 			}
@@ -229,7 +229,7 @@
 
 	private Vector3 GetSpawnOffset()
 	{
-		return (m_spawnOffsetLocalTransform ? base.transform.up : Vector3.up) * m_spawnOffset;
+		return (m_spawnOffsetLocalTransform ? transform.up : Vector3.up) * m_spawnOffset;
 	}
 
 	private void RPC_Pick(long sender, int bonus)
@@ -238,7 +238,7 @@
 		{
 			return;
 		}
-		Vector3 basePos = (m_pickEffectAtSpawnPoint ? (base.transform.position + GetSpawnOffset()) : base.transform.position);
+		Vector3 basePos = (m_pickEffectAtSpawnPoint ? (transform.position + GetSpawnOffset()) : transform.position);
 		m_pickEffector.Create(basePos, Quaternion.identity, null, 1f, -1, Player.m_localPlayer.GetZDOID());
 		int num = (m_dontScale ? m_amount : Mathf.Max(m_minAmountScaled, Game.instance.ScaleDrops(m_itemPrefab, m_amount)));
 		num += bonus;
@@ -256,7 +256,7 @@
 		}
 		if (m_aggravateRange > 0f)
 		{
-			BaseAI.AggravateAllInArea(base.transform.position, m_aggravateRange, BaseAI.AggravatedReason.Theif);
+			BaseAI.AggravateAllInArea(transform.position, m_aggravateRange, BaseAI.AggravatedReason.Theif);
 		}
 		m_nview.InvokeRPC(ZNetView.Everybody, "RPC_SetPicked", true);
 	}
@@ -307,11 +307,11 @@
 		m_enabled = value;
 		if ((bool)m_nview && m_nview.IsOwner() && m_nview.GetZDO() != null)
 		{
-			m_nview.GetZDO().Set(ZDOVars.s_enabled, base.enabled);
+			m_nview.GetZDO().Set(ZDOVars.s_enabled, enabled);
 		}
 		if ((bool)m_hideWhenPicked)
 		{
-			m_hideWhenPicked.SetActive(base.enabled && ShouldRespawn());
+			m_hideWhenPicked.SetActive(enabled && ShouldRespawn());
 		}
 	}
 
@@ -331,16 +331,16 @@
 	private void Drop(GameObject prefab, int offset, int stack)
 	{
 		Vector2 vector = UnityEngine.Random.insideUnitCircle * 0.2f;
-		Vector3 position = base.transform.position + GetSpawnOffset() + new Vector3(vector.x, 0.5f * (float)offset, vector.y);
+		Vector3 position = transform.position + GetSpawnOffset() + new Vector3(vector.x, 0.5f * (float)offset, vector.y);
 		Quaternion rotation = Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f);
-		GameObject obj = UnityEngine.Object.Instantiate(prefab, position, rotation);
-		ItemDrop component = obj.GetComponent<ItemDrop>();
+		GameObject gameObject = UnityEngine.Object.Instantiate(prefab, position, rotation);
+		ItemDrop component = gameObject.GetComponent<ItemDrop>();
 		if ((object)component != null)
 		{
 			component.SetStack(stack);
 			ItemDrop.OnCreateNew(component);
 		}
-		obj.GetComponent<Rigidbody>().linearVelocity = Vector3.up * 4f;
+		gameObject.GetComponent<Rigidbody>().linearVelocity = Vector3.up * 4f;
 	}
 
 	public bool UseItem(Humanoid user, ItemDrop.ItemData item)
```

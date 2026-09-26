# `ArmorStand.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+18/-17` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ArmorStand.cs
+++ b/ArmorStand.cs
@@ -79,7 +79,7 @@
 
 	private void Awake()
 	{
-		m_nview = (m_netViewOverride ? m_netViewOverride : base.gameObject.GetComponent<ZNetView>());
+		m_nview = (m_netViewOverride ? m_netViewOverride : gameObject.GetComponent<ZNetView>());
 		if (m_nview.GetZDO() == null)
 		{
 			return;
@@ -107,36 +107,36 @@
 			Switch obj = item.m_switch;
 			obj.m_onUse = (Switch.Callback)Delegate.Combine(obj.m_onUse, new Switch.Callback(UseItem));
 			Switch obj2 = item.m_switch;
-			obj2.m_onHover = (Switch.TooltipCallback)Delegate.Combine(obj2.m_onHover, (Switch.TooltipCallback)delegate
-			{
-				if (!PrivateArea.CheckAccess(base.transform.position, 0f, flash: false))
+			obj2.m_onHover = (Switch.TooltipCallback)Delegate.Combine(obj2.m_onHover, (Switch.TooltipCallback)(() =>
+			{
+				if (!PrivateArea.CheckAccess(transform.position, 0f, flash: false))
 				{
 					return Localization.instance.Localize(m_name + "\n$piece_noaccess");
 				}
 				string text = ((GetNrOfAttachedItems() > 0) ? "\n[<color=yellow><b>$KEY_Use</b></color>] $piece_itemstand_take" : "");
 				return Localization.instance.Localize(item.m_switch.m_hoverText + "\n[<color=yellow><b>$KEY_HotbarUse</b></color>] $piece_itemstand_attach" + text);
-			});
+			}));
 		}
 		if (!(m_changePoseSwitch != null) || !m_changePoseSwitch.gameObject.activeInHierarchy)
 		{
 			return;
 		}
 		Switch changePoseSwitch = m_changePoseSwitch;
-		changePoseSwitch.m_onUse = (Switch.Callback)Delegate.Combine(changePoseSwitch.m_onUse, (Switch.Callback)delegate
+		changePoseSwitch.m_onUse = (Switch.Callback)Delegate.Combine(changePoseSwitch.m_onUse, (Switch.Callback)((Switch caller, Humanoid user, ItemDrop.ItemData itemData) =>
 		{
 			if (!m_nview.IsOwner())
 			{
 				m_nview.InvokeRPC("RPC_RequestOwn");
 			}
-			if (!PrivateArea.CheckAccess(base.transform.position, 0f, flash: false))
+			if (!PrivateArea.CheckAccess(transform.position, 0f, flash: false))
 			{
 				return false;
 			}
 			m_nview.InvokeRPC(ZNetView.Everybody, "RPC_SetPose", (m_pose + 1 < m_poseCount) ? (m_pose + 1) : 0);
 			return true;
-		});
+		}));
 		Switch changePoseSwitch2 = m_changePoseSwitch;
-		changePoseSwitch2.m_onHover = (Switch.TooltipCallback)Delegate.Combine(changePoseSwitch2.m_onHover, (Switch.TooltipCallback)(() => (!PrivateArea.CheckAccess(base.transform.position, 0f, flash: false)) ? Localization.instance.Localize(m_name + "\n$piece_noaccess") : Localization.instance.Localize(m_name + "\n[<color=yellow><b>$KEY_Use</b></color>] Change pose ")));
+		changePoseSwitch2.m_onHover = (Switch.TooltipCallback)Delegate.Combine(changePoseSwitch2.m_onHover, (Switch.TooltipCallback)(() => (!PrivateArea.CheckAccess(transform.position, 0f, flash: false)) ? Localization.instance.Localize(m_name + "\n$piece_noaccess") : Localization.instance.Localize(m_name + "\n[<color=yellow><b>$KEY_Use</b></color>] Change pose ")));
 	}
 
 	private void Update()
@@ -145,7 +145,7 @@
 		{
 			return;
 		}
-		bool flag = Vector3.Distance(Player.m_localPlayer.transform.position, base.transform.position) > m_clothSimLodDistance * QualitySettings.lodBias;
+		bool flag = Vector3.Distance(Player.m_localPlayer.transform.position, transform.position) > m_clothSimLodDistance * QualitySettings.lodBias;
 		if (m_clothLodded == flag)
 		{
 			return;
@@ -178,7 +178,7 @@
 		m_poseAnimator.SetInteger("Pose", m_pose);
 		if (effect)
 		{
-			m_effects.Create(base.transform.position, Quaternion.identity);
+			m_effects.Create(transform.position, Quaternion.identity);
 		}
 		if (m_nview.IsOwner())
 		{
@@ -193,7 +193,7 @@
 
 	private bool UseItem(Switch caller, Humanoid user, ItemDrop.ItemData item)
 	{
-		if (!PrivateArea.CheckAccess(base.transform.position, 0f, flash: false))
+		if (!PrivateArea.CheckAccess(transform.position, 0f, flash: false))
 		{
 			return true;
 		}
@@ -305,9 +305,9 @@
 			GameObject itemPrefab = ObjectDB.instance.GetItemPrefab(hash);
 			if ((bool)itemPrefab)
 			{
-				GameObject obj = UnityEngine.Object.Instantiate(itemPrefab, m_dropSpawnPoint.position, m_dropSpawnPoint.rotation);
-				ItemDrop.LoadFromZDO(obj.GetComponent<ItemDrop>().m_itemData, m_nview.GetZDO(), index);
-				obj.GetComponent<Rigidbody>().linearVelocity = Vector3.up * 4f;
+				GameObject gameObject = UnityEngine.Object.Instantiate(itemPrefab, m_dropSpawnPoint.position, m_dropSpawnPoint.rotation);
+				ItemDrop.LoadFromZDO(gameObject.GetComponent<ItemDrop>().m_itemData, m_nview.GetZDO(), index);
+				gameObject.GetComponent<Rigidbody>().linearVelocity = Vector3.up * 4f;
 				m_destroyEffects.Create(m_dropSpawnPoint.position, Quaternion.identity);
 			}
 			m_nview.GetZDO().Set(s_itemKeyHashes[index], 0);
@@ -328,11 +328,12 @@
 				ItemDrop.ItemData itemData = m_queuedItem.Clone();
 				itemData.m_stack = 1;
 				m_nview.GetZDO().Set(s_itemKeyHashes[m_queuedSlot], m_queuedItem.m_dropPrefab.name.GetStableHashCode());
+				m_nview.GetZDO().Set(s_variantKeyHashes[m_queuedSlot], itemData.m_variant);
 				ItemDrop.SaveToZDO(itemData, m_nview.GetZDO(), m_queuedSlot);
 				localPlayer.UnequipItem(m_queuedItem);
 				localPlayer.GetInventory().RemoveOneItem(m_queuedItem);
-				m_nview.InvokeRPC(ZNetView.Everybody, "RPC_SetVisualItem", m_queuedSlot, itemData.m_dropPrefab.name, itemData.m_variant);
-				m_effects.Create(base.transform.position, Quaternion.identity);
+				m_nview.InvokeRPC(ZNetView.Everybody, "RPC_SetVisualItem", m_queuedSlot, itemData.m_dropPrefab.name.GetStableHashCode(), itemData.m_variant);
+				m_effects.Create(transform.position, Quaternion.identity);
 				Game.instance.IncrementPlayerStat(PlayerStatType.ArmorStandUses);
 			}
 			m_queuedItem = null;
```

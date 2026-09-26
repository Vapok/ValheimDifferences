# `ItemStand.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+17/-10` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ItemStand.cs
+++ b/ItemStand.cs
@@ -87,7 +87,7 @@
 
 	private void Awake()
 	{
-		m_nview = (m_netViewOverride ? m_netViewOverride : base.gameObject.GetComponent<ZNetView>());
+		m_nview = (m_netViewOverride ? m_netViewOverride : gameObject.GetComponent<ZNetView>());
 		if (m_nview.GetZDO() != null)
 		{
 			WearNTear component = GetComponent<WearNTear>();
@@ -118,7 +118,7 @@
 		{
 			return "";
 		}
-		if (!PrivateArea.CheckAccess(base.transform.position, 0f, flash: false))
+		if (!PrivateArea.CheckAccess(transform.position, 0f, flash: false))
 		{
 			return Localization.instance.Localize(m_name + "\n$piece_noaccess");
 		}
@@ -168,7 +168,7 @@
 
 	public bool Interact(Humanoid user, bool hold, bool alt)
 	{
-		if (!PrivateArea.CheckAccess(base.transform.position))
+		if (!PrivateArea.CheckAccess(transform.position))
 		{
 			return true;
 		}
@@ -220,7 +220,7 @@
 					return false;
 				}
 				user.Message(MessageHud.MessageType.Center, "$guardianstone_hook_power_activate ");
-				m_activatePowerEffects.Create(base.transform.position, base.transform.rotation);
+				m_activatePowerEffects.Create(transform.position, transform.rotation);
 				m_activatePowerEffectsPlayer.Create(user.transform.position, Quaternion.identity, user.transform);
 				Invoke("DelayedPowerActivation", m_powerActivationDelay);
 				return true;
@@ -251,7 +251,7 @@
 		{
 			localPlayer.SetGuardianPower(m_guardianPower.name);
 			Game.instance.IncrementPlayerStat(PlayerStatType.SetGuardianPower);
-			switch (base.name)
+			switch (name)
 			{
 			case "GP_Eikthyr":
 				Game.instance.IncrementPlayerStat(PlayerStatType.SetPowerEikthyr);
@@ -278,7 +278,7 @@
 				Game.instance.IncrementPlayerStat(PlayerStatType.SetPowerDeepNorth);
 				break;
 			default:
-				ZLog.LogWarning("Missing stat for guardian power: " + base.name);
+				ZLog.LogWarning("Missing stat for guardian power: " + name);
 				break;
 			}
 		}
@@ -346,9 +346,9 @@
 				quaternion = transform.transform.localRotation;
 				vector = transform.transform.localPosition;
 			}
-			GameObject obj = UnityEngine.Object.Instantiate(itemPrefab, m_dropSpawnPoint.position + vector, m_dropSpawnPoint.rotation * quaternion);
-			obj.GetComponent<ItemDrop>().LoadFromExternalZDO(m_nview.GetZDO());
-			obj.GetComponent<Rigidbody>().linearVelocity = Vector3.up * 4f;
+			GameObject gameObject = UnityEngine.Object.Instantiate(itemPrefab, m_dropSpawnPoint.position + vector, m_dropSpawnPoint.rotation * quaternion);
+			gameObject.GetComponent<ItemDrop>().LoadFromExternalZDO(m_nview.GetZDO());
+			gameObject.GetComponent<Rigidbody>().linearVelocity = Vector3.up * 4f;
 			m_effects.Create(m_dropSpawnPoint.position, Quaternion.identity);
 		}
 		m_nview.GetZDO().Set(ZDOVars.s_item, 0);
@@ -432,6 +432,13 @@
 		{
 			UnityEngine.Object.Destroy(m_visualItem);
 			return;
+		}
+		if (m_nview.IsOwner())
+		{
+			m_nview.GetZDO().Set(ZDOVars.s_item, m_visualHash);
+			m_nview.GetZDO().Set(ZDOVars.s_variant, m_visualVariant);
+			m_nview.GetZDO().Set(ZDOVars.s_quality, quality);
+			m_nview.GetZDO().Set(ZDOVars.s_type, m_orientation);
 		}
 		GameObject itemPrefab = ObjectDB.instance.GetItemPrefab(itemHash);
 		if (itemPrefab == null)
@@ -564,7 +571,7 @@
 		{
 			foreach (OrientationSettings itemStandOffset in obj.m_shared.m_itemStandOffsets)
 			{
-				if ((m_orientationType & itemStandOffset.m_orientations) != Orientation.None)
+				if ((m_orientationType & itemStandOffset.m_orientations) != 0)
 				{
 					matched.Add(itemStandOffset);
 				}
```

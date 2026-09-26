# `VisEquipment.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/VisEquipment.cs
+++ b/VisEquipment.cs
@@ -234,7 +234,7 @@
 		set
 		{
 			m_snowLevel = Mathf.Clamp01(value);
-			MaterialMan.instance.SetValue(base.gameObject, Shader.PropertyToID("_SnowCover"), m_snowLevel);
+			MaterialMan.instance.SetValue(gameObject, Shader.PropertyToID("_SnowCover"), m_snowLevel);
 		}
 	}
 
@@ -291,12 +291,12 @@
 	private void SetupFacialHairNonPlayer()
 	{
 		ZDO zDO = m_nview.GetZDO();
-		bool num = m_nview.IsOwner();
-		if (num && zDO.GetInt(ZDOVars.s_hairItem) == 0 && !zDO.GetBool(ZDOVars.s_noHair))
+		bool flag = m_nview.IsOwner();
+		if (flag && zDO.GetInt(ZDOVars.s_hairItem) == 0 && !zDO.GetBool(ZDOVars.s_noHair))
 		{
 			SetupNpcHair(zDO);
 		}
-		if (num && zDO.GetInt(ZDOVars.s_beardItem) == 0 && !zDO.GetBool(ZDOVars.s_noBeard))
+		if (flag && zDO.GetInt(ZDOVars.s_beardItem) == 0 && !zDO.GetBool(ZDOVars.s_noBeard))
 		{
 			SetupNpcBeard(zDO);
 		}
@@ -349,7 +349,7 @@
 	{
 		if (m_useAllTrails)
 		{
-			MeleeWeaponTrail[] componentsInChildren = base.gameObject.GetComponentsInChildren<MeleeWeaponTrail>();
+			MeleeWeaponTrail[] componentsInChildren = gameObject.GetComponentsInChildren<MeleeWeaponTrail>();
 			for (int i = 0; i < componentsInChildren.Length; i++)
 			{
 				componentsInChildren[i].Emit = enabled;
@@ -850,7 +850,7 @@
 			{
 				ItemDrop.ItemData.HelmetHairSettings helmetHairSettings = (accessory switch
 				{
-					ItemDrop.ItemData.AccessoryType.Hair => component.m_itemData.m_shared.m_helmetHairSettings, 
+					ItemDrop.ItemData.AccessoryType.Hair => (IEnumerable<ItemDrop.ItemData.HelmetHairSettings>)component.m_itemData.m_shared.m_helmetHairSettings, 
 					ItemDrop.ItemData.AccessoryType.Beard => component.m_itemData.m_shared.m_helmetBeardSettings, 
 					_ => throw new Exception("Acecssory type not implemented"), 
 				}).FirstOrDefault((ItemDrop.ItemData.HelmetHairSettings x) => x.m_setting == type);
@@ -1444,6 +1444,6 @@
 
 	private void RefreshSnowLevel()
 	{
-		MaterialMan.instance.SetValue(base.gameObject, Shader.PropertyToID("_SnowCover"), m_snowLevel);
+		MaterialMan.instance.SetValue(gameObject, Shader.PropertyToID("_SnowCover"), m_snowLevel);
 	}
 }
```

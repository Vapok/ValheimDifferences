# `Inventory.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Save() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Inventory.cs
+++ b/Inventory.cs
@@ -834,7 +834,7 @@
 
 	public void Save(ZPackage pkg)
 	{
-		pkg.Write(109);
+		pkg.Write(110);
 		pkg.Write((ushort)m_inventory.Count);
 		foreach (ItemDrop.ItemData item in m_inventory)
 		{
@@ -1075,13 +1075,13 @@
 		component.m_itemData.m_equipped = equipped;
 		component.SetQuality(quality);
 		component.m_itemData.m_variant = variant;
-		component.ResetVariantIfInvalid();
 		component.m_itemData.m_crafterID = crafterID;
 		component.m_itemData.m_crafterName = crafterName;
 		component.m_itemData.m_customData = customData;
 		component.m_itemData.m_worldLevel = (byte)worldLevel;
 		component.m_itemData.m_pickedUp = pickedUp;
-		component.m_itemData.m_cheated = cheated || component.m_itemData.GetDamage().GetTotalDamage() > 10000f;
+		component.m_itemData.m_cheated = cheated;
+		component.EnsureValid();
 		AddItem(component.m_itemData, component.m_itemData.m_stack, pos.x, pos.y, skipValidPositionCheck);
 		UnityEngine.Object.Destroy(gameObject);
 		return true;
```

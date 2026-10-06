# `Inventory.cs` Diff (`1.0.16` $\rightarrow$ `1.0.17`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Inventory.cs
+++ b/Inventory.cs
@@ -1075,6 +1075,7 @@
 		component.m_itemData.m_equipped = equipped;
 		component.SetQuality(quality);
 		component.m_itemData.m_variant = variant;
+		component.ResetVariantIfInvalid();
 		component.m_itemData.m_crafterID = crafterID;
 		component.m_itemData.m_crafterName = crafterName;
 		component.m_itemData.m_customData = customData;
```

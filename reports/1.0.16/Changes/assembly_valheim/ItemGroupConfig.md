# `Valheim.UI/ItemGroupConfig.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/ItemGroupConfig.cs
+++ b/Valheim.UI/ItemGroupConfig.cs
@@ -79,7 +79,7 @@
 		elements.Add(itemElement);
 		if (radial.IsHoverMenu)
 		{
-			itemElement.AdvancedCloseOnInteract = delegate(RadialBase radialBase, RadialArray<RadialMenuElement> radialArray)
+			itemElement.AdvancedCloseOnInteract = (RadialBase radialBase, RadialArray<RadialMenuElement> radialArray) =>
 			{
 				Player localPlayer = Player.m_localPlayer;
 				if (!localPlayer)
@@ -104,7 +104,7 @@
 			{
 				return;
 			}
-			itemElement.AdvancedCloseOnInteract = delegate(RadialBase radialBase, RadialArray<RadialMenuElement> radialArray)
+			itemElement.AdvancedCloseOnInteract = (RadialBase radialBase, RadialArray<RadialMenuElement> radialArray) =>
 			{
 				Player localPlayer = Player.m_localPlayer;
 				return !localPlayer || radialArray.GetArray.Where((RadialMenuElement e) => e is ItemElement).Cast<ItemElement>().All((ItemElement element) => !localPlayer.CanEat(element.m_data, showMessages: false));
```

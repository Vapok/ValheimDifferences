# `Valheim.UI/RadialInventoryInfo.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+12/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/RadialInventoryInfo.cs
+++ b/Valheim.UI/RadialInventoryInfo.cs
@@ -84,8 +84,17 @@
 			if (data.TryGetArmorDifference(out var difference))
 			{
 				string text = Player.m_localPlayer.GetBodyArmor().ToString();
-				string text2 = ((difference > 0f) ? "<color=green>+" : ((difference == 0f) ? "<color=orange>+" : "<color=red>")) + difference + "</color>";
-				m_armorText.text = text + " " + text2;
+				string text2;
+				if (difference > 0f)
+				{
+					text2 = "<color=green>+";
+				}
+				else
+				{
+					text2 = ((difference == 0f) ? "<color=orange>+" : "<color=red>");
+				}
+				string text3 = text2 + difference + "</color>";
+				m_armorText.text = text + " " + text3;
 			}
 			else
 			{
@@ -96,7 +105,7 @@
 
 	internal void HideToolTip(RadialMenuAnimationManager animator)
 	{
-		animator.StartUniqueTween(() => m_currentTooltipHeight, delegate(float newHeight)
+		animator.StartUniqueTween(() => m_currentTooltipHeight, (float newHeight) =>
 		{
 			ResizeTooltipHeight(newHeight);
 			if (MinHeightCheck())
```

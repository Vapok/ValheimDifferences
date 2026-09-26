# `Valheim.UI/ThrowElement.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+9/-9` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/ThrowElement.cs
+++ b/Valheim.UI/ThrowElement.cs
@@ -66,11 +66,11 @@
 
 	private void SetProperties(ItemDrop.ItemData item)
 	{
-		base.Name = "";
-		base.Interact = null;
-		base.SubTitle = "";
-		base.SecondaryInteract = null;
-		base.Name = Localization.instance.Localize(item.m_shared.m_name);
+		Name = "";
+		Interact = null;
+		SubTitle = "";
+		SecondaryInteract = null;
+		Name = Localization.instance.Localize(item.m_shared.m_name);
 		m_data = item;
 		SetInteraction(item);
 		SetSubTitle(item);
@@ -81,21 +81,21 @@
 
 	private void SetDescription(ItemDrop.ItemData item)
 	{
-		base.Description = item.GetTooltip();
+		Description = item.GetTooltip();
 		int num = Mathf.CeilToInt((float)ThrowAmount * m_data.GetNonStackedWeight());
 		string newWeightString = $"\n$item_weight: <color=orange>{item.GetNonStackedWeight()} ({item.GetWeight()} - {num} $item_total)</color>";
-		base.Description = string.Join("\n", from line in base.Description.Split('\n')
+		Description = string.Join("\n", from line in Description.Split('\n')
 			select (!line.StartsWith("$item_weight:")) ? line : newWeightString);
 	}
 
 	private void SetSubTitle(ItemDrop.ItemData item)
 	{
-		base.SubTitle = ((item.m_shared.m_maxStackSize > 1) ? $"{item.m_stack} - {ThrowAmount} / {item.m_shared.m_maxStackSize}" : "");
+		SubTitle = ((item.m_shared.m_maxStackSize > 1) ? $"{item.m_stack} - {ThrowAmount} / {item.m_shared.m_maxStackSize}" : "");
 	}
 
 	protected void SetInteraction(ItemDrop.ItemData item)
 	{
-		base.Interact = delegate
+		Interact = () =>
 		{
 			if ((bool)Player.m_localPlayer)
 			{
```

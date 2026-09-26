# `Valheim.UI/ItemElement.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+17/-17` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/ItemElement.cs
+++ b/Valheim.UI/ItemElement.cs
@@ -20,19 +20,19 @@
 
 	public void Init(ItemDrop.ItemData item)
 	{
-		base.Name = "";
-		base.Interact = null;
-		base.SubTitle = "";
-		base.SecondaryInteract = null;
+		Name = "";
+		Interact = null;
+		SubTitle = "";
+		SecondaryInteract = null;
 		m_go.SetActive(item != null);
 		if (item != null)
 		{
 			m_data = item;
 			SetInteraction(item);
-			base.Name = Localization.instance.Localize(item.m_shared.m_name);
-			base.Description = item.GetTooltip();
+			Name = Localization.instance.Localize(item.m_shared.m_name);
+			Description = item.GetTooltip();
 			m_icon.sprite = item?.GetIcon();
-			base.Activated = (m_data.m_equipped ? 1f : 0f);
+			Activated = (m_data.m_equipped ? 1f : 0f);
 			SetAmount(item);
 			SetDurability(item);
 		}
@@ -40,19 +40,19 @@
 
 	public void UpdateQueueAndActivation(float progress, Player.MinorActionData data, int queueCount)
 	{
-		base.Queued = progress <= 0.01f && (base.Queued || queueCount > 1);
-		base.Activated = ((data.m_type == Player.MinorActionData.ActionType.Unequip) ? (1f - progress) : progress);
+		Queued = progress <= 0.01f && (Queued || queueCount > 1);
+		Activated = ((data.m_type == Player.MinorActionData.ActionType.Unequip) ? (1f - progress) : progress);
 	}
 
 	public void UpdateQueueAndActivation(bool equipActionQueued)
 	{
-		base.Queued = equipActionQueued;
-		base.Activated = (m_data.m_equipped ? 1f : 0f);
+		Queued = equipActionQueued;
+		Activated = (m_data.m_equipped ? 1f : 0f);
 	}
 
 	protected virtual void SetInteraction(ItemDrop.ItemData item)
 	{
-		base.Interact = delegate
+		Interact = () =>
 		{
 			if ((bool)Player.m_localPlayer)
 			{
@@ -60,7 +60,7 @@
 			}
 			return true;
 		};
-		HoverMenuInteract = delegate(GameObject hoverObject)
+		HoverMenuInteract = (GameObject hoverObject) =>
 		{
 			if ((bool)Player.m_localPlayer)
 			{
@@ -68,7 +68,7 @@
 			}
 			return true;
 		};
-		base.SecondaryInteract = delegate
+		SecondaryInteract = () =>
 		{
 			if ((bool)Player.m_localPlayer)
 			{
@@ -76,7 +76,7 @@
 			}
 			return true;
 		};
-		base.TryOpenSubRadial = delegate(RadialBase menu, int currentIndex)
+		TryOpenSubRadial = (RadialBase menu, int currentIndex) =>
 		{
 			if (m_data.m_stack <= 1 || m_data.m_shared.m_maxStackSize <= 1)
 			{
@@ -86,7 +86,7 @@
 			menu.QueuedOpen(RadialData.SO.ThrowGroupConfig, menu.CurrentConfig);
 			return true;
 		};
-		base.CloseOnInteract = () => m_data == null || !m_data.IsEquipable();
+		CloseOnInteract = () => m_data == null || !m_data.IsEquipable();
 	}
 
 	public void UpdateDurabilityAndAmount()
@@ -105,7 +105,7 @@
 				m_amount.text = $"{item.m_stack} / {item.m_shared.m_maxStackSize}";
 				m_stackText = item.m_stack;
 			}
-			base.SubTitle = m_amount.text;
+			SubTitle = m_amount.text;
 		}
 		else
 		{
```

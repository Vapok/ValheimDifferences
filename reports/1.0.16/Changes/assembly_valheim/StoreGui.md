# `StoreGui.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/StoreGui.cs
+++ b/StoreGui.cs
@@ -186,7 +186,7 @@
 		}
 		if (flag)
 		{
-			m_buyEffects.Create(base.transform.position, Quaternion.identity);
+			m_buyEffects.Create(transform.position, Quaternion.identity);
 			m_selectedItem.m_buyPlayerEffects.Create(Player.m_localPlayer.transform.position, Quaternion.identity);
 			if (m_selectedItem.m_levelUpEffect)
 			{
@@ -213,7 +213,7 @@
 			Player.m_localPlayer.GetInventory().AddItem(m_coinPrefab.gameObject.name, stack, m_coinPrefab.m_itemData.m_quality, m_coinPrefab.m_itemData.m_variant, 0L, "", cheated);
 			string text = "";
 			text = ((sellableItem.m_stack <= 1) ? sellableItem.m_shared.m_name : (sellableItem.m_stack + "x" + sellableItem.m_shared.m_name));
-			m_sellEffects.Create(base.transform.position, Quaternion.identity);
+			m_sellEffects.Create(transform.position, Quaternion.identity);
 			Player.m_localPlayer.Message(MessageHud.MessageType.TopLeft, Localization.instance.Localize("$msg_sold", text, stack.ToString()), 0, sellableItem.m_shared.m_icons[0]);
 			m_trader.OnSold();
 			FillList();
@@ -287,7 +287,7 @@
 			{
 				component4.color = Color.grey;
 			}
-			element.GetComponent<Button>().onClick.AddListener(delegate
+			element.GetComponent<Button>().onClick.AddListener(() =>
 			{
 				OnSelectedItem(element);
 			});
```

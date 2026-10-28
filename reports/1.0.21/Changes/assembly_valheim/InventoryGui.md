# `InventoryGui.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+9/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Awake() [Method Body Modified]`
- `OnReleasedOutside() [Method Body Modified]`
- `OnStackAll() [Method Body Modified]`
- `private void OnReleasedOutside()`

---

## 📝 Code Diff

```diff
--- a/InventoryGui.cs
+++ b/InventoryGui.cs
@@ -400,7 +400,7 @@
 		UIDragHandler component = m_dropButton.GetComponent<UIDragHandler>();
 		component.m_onReleasedOn = (Action<UIDragHandler>)Delegate.Combine(component.m_onReleasedOn, (Action<UIDragHandler>)((UIDragHandler _) =>
 		{
-			OnDropOutside();
+			OnReleasedOutside();
 		}));
 		m_craftButton.onClick.AddListener(OnCraftPressed);
 		m_craftCancelButton.onClick.AddListener(OnCraftCancelPressed);
@@ -836,6 +836,14 @@
 		{
 			SetupDragItem(null, null, 1);
 			m_currentContainer.GetInventory().StackAll(Player.m_localPlayer.GetInventory());
+		}
+	}
+
+	private void OnReleasedOutside()
+	{
+		if (ZInput.IsTouchActive())
+		{
+			OnDropOutside();
 		}
 	}
 
```

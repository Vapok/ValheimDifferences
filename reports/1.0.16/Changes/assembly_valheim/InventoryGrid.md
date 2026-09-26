# `InventoryGrid.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+8/-8` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/InventoryGrid.cs
+++ b/InventoryGrid.cs
@@ -91,7 +91,7 @@
 
 	public void ResetView()
 	{
-		RectTransform rectTransform = base.transform as RectTransform;
+		RectTransform rectTransform = transform as RectTransform;
 		if (m_gridRoot.rect.height > rectTransform.rect.height)
 		{
 			m_gridRoot.pivot = new Vector2(m_gridRoot.pivot.x, 1f);
@@ -244,7 +244,7 @@
 
 	private void UpdateGui(Player player, ItemDrop.ItemData dragItem)
 	{
-		RectTransform rectTransform = base.transform as RectTransform;
+		RectTransform rectTransform = transform as RectTransform;
 		int width = m_inventory.GetWidth();
 		int height = m_inventory.GetHeight();
 		if (m_selected.x >= width - 1)
@@ -271,19 +271,19 @@
 				for (int j = 0; j < width; j++)
 				{
 					Vector2 vector2 = new Vector3((float)j * m_elementSpace, (float)i * (0f - m_elementSpace));
-					GameObject obj = UnityEngine.Object.Instantiate(m_elementPrefab, m_gridRoot);
-					(obj.transform as RectTransform).anchoredPosition = vector + vector2;
-					UIInputHandler componentInChildren = obj.GetComponentInChildren<UIInputHandler>();
+					GameObject gameObject = UnityEngine.Object.Instantiate(m_elementPrefab, m_gridRoot);
+					(gameObject.transform as RectTransform).anchoredPosition = vector + vector2;
+					UIInputHandler componentInChildren = gameObject.GetComponentInChildren<UIInputHandler>();
 					componentInChildren.m_onRightDown = (Action<UIInputHandler>)Delegate.Combine(componentInChildren.m_onRightDown, new Action<UIInputHandler>(OnRightDown));
 					componentInChildren.m_onLeftDown = (Action<UIInputHandler>)Delegate.Combine(componentInChildren.m_onLeftDown, new Action<UIInputHandler>(OnLeftDown));
 					componentInChildren.m_onLeftClick = (Action<UIInputHandler>)Delegate.Combine(componentInChildren.m_onLeftClick, new Action<UIInputHandler>(OnLeftClick));
 					componentInChildren.m_onLeftUp = (Action<UIInputHandler>)Delegate.Combine(componentInChildren.m_onLeftUp, new Action<UIInputHandler>(OnLeftRelease));
 					componentInChildren.m_onPointerEnter = (Action<UIInputHandler>)Delegate.Combine(componentInChildren.m_onPointerEnter, new Action<UIInputHandler>(OnPointerEnter));
-					UIDragHandler componentInChildren2 = obj.GetComponentInChildren<UIDragHandler>();
+					UIDragHandler componentInChildren2 = gameObject.GetComponentInChildren<UIDragHandler>();
 					componentInChildren2.m_onBeginDrag = (Action<UIDragHandler>)Delegate.Combine(componentInChildren2.m_onBeginDrag, new Action<UIDragHandler>(OnBeginDrag));
 					componentInChildren2.m_onEndDrag = (Action<UIDragHandler>)Delegate.Combine(componentInChildren2.m_onEndDrag, new Action<UIDragHandler>(OnDragEnd));
 					componentInChildren2.m_onReleasedOn = (Action<UIDragHandler>)Delegate.Combine(componentInChildren2.m_onReleasedOn, new Action<UIDragHandler>(OnReleasedOn));
-					TMP_Text component = obj.transform.Find("binding").GetComponent<TMP_Text>();
+					TMP_Text component = gameObject.transform.Find("binding").GetComponent<TMP_Text>();
 					if ((bool)player && i == 0)
 					{
 						component.text = (j + 1).ToString();
@@ -292,7 +292,7 @@
 					{
 						component.enabled = false;
 					}
-					InventoryElement component2 = obj.GetComponent<InventoryElement>();
+					InventoryElement component2 = gameObject.GetComponent<InventoryElement>();
 					component2.Initialize(j, i);
 					m_elements.Add(component2);
 				}
```

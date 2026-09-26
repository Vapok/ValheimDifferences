# `BuildUi.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+9/-9` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/BuildUi.cs
+++ b/BuildUi.cs
@@ -116,7 +116,7 @@
 	{
 		get
 		{
-			if (base.gameObject.activeSelf)
+			if (gameObject.activeSelf)
 			{
 				return m_searchField.isFocused;
 			}
@@ -144,7 +144,7 @@
 		{
 			Button component = item.GetComponent<Button>();
 			int tabIndex = num;
-			component.onClick.AddListener(delegate
+			component.onClick.AddListener(() =>
 			{
 				SelectPieceList(tabIndex);
 			});
@@ -194,11 +194,11 @@
 	private void SubscribeEvents()
 	{
 		m_searchField.onValueChanged.AddListener(UpdateSearch);
-		m_searchField.onSelect.AddListener(delegate
+		m_searchField.onSelect.AddListener((string _) =>
 		{
 			m_tabHandler.m_keybaordInput = false;
 		});
-		m_searchField.onDeselect.AddListener(delegate
+		m_searchField.onDeselect.AddListener((string _) =>
 		{
 			m_tabHandler.m_keybaordInput = true;
 		});
@@ -336,11 +336,11 @@
 
 	private void ShowDeletePopup(BuildUiTagButton button)
 	{
-		UnifiedPopup.Push(new YesNoPopup("$menu_removefavoritecategory", button.m_displayName, delegate
+		UnifiedPopup.Push(new YesNoPopup("$menu_removefavoritecategory", button.m_displayName, () =>
 		{
 			m_favoritePieceList.RemoveTag(button.m_tagId);
 			UnifiedPopup.Pop();
-		}, delegate
+		}, () =>
 		{
 			UnifiedPopup.Pop();
 		}));
@@ -477,7 +477,7 @@
 	private void OnFavoriteTagsChanged()
 	{
 		RefreshFavorites();
-		if (base.gameObject.activeSelf)
+		if (gameObject.activeSelf)
 		{
 			SelectPieceList(m_currentPieceList);
 		}
@@ -631,7 +631,7 @@
 		{
 			UpdateSearch(m_searchField.text);
 		}
-		base.gameObject.SetActive(value: true);
+		gameObject.SetActive(value: true);
 		ConfigureButtonNavigation();
 	}
 
@@ -665,7 +665,7 @@
 	{
 		ReturnAllTagButtonsToPool();
 		m_favoritesDropdown.Close();
-		base.gameObject.SetActive(value: false);
+		gameObject.SetActive(value: false);
 	}
 
 	public void OnHoverPiece(BuildUiPieceButton button)
```

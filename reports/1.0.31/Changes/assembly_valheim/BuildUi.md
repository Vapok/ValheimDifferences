# `BuildUi.cs` Diff (`1.0.30` $\rightarrow$ `1.0.31`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+22/-8` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `FavoritePiece() [Method Body Modified]`
- `OnTouchLongPressStarted() [Method Body Modified]`
- `SearchFieldDeselect() [Method Body Modified]`
- `SearchFieldSelect() [Method Body Modified]`
- `SubscribeEvents() [Method Body Modified]`
- `UnsubscribeEvents() [Method Body Modified]`
- `private void SearchFieldDeselect(string _)`
- `private void SearchFieldSelect(string _)`

---

## 📝 Code Diff

```diff
--- a/BuildUi.cs
+++ b/BuildUi.cs
@@ -200,14 +200,8 @@
 	private void SubscribeEvents()
 	{
 		m_searchField.onValueChanged.AddListener(UpdateSearch);
-		m_searchField.onSelect.AddListener((string _) =>
-		{
-			m_tabHandler.m_keybaordInput = false;
-		});
-		m_searchField.onDeselect.AddListener((string _) =>
-		{
-			m_tabHandler.m_keybaordInput = true;
-		});
+		m_searchField.onSelect.AddListener(SearchFieldSelect);
+		m_searchField.onDeselect.AddListener(SearchFieldDeselect);
 		ZInput.OnInputLayoutChanged += OnLayoutChanged;
 		m_recentPieceList.PieceAdded += OnRecentPieceAdded;
 		m_recentPieceList.PieceRemoved += OnRecentPieceRemoved;
@@ -219,6 +213,16 @@
 		TouchLongPress.Performed += OnTouchLongPressPerformed;
 	}
 
+	private void SearchFieldSelect(string _)
+	{
+		m_tabHandler.m_keybaordInput = false;
+	}
+
+	private void SearchFieldDeselect(string _)
+	{
+		m_tabHandler.m_keybaordInput = true;
+	}
+
 	private void OnTouchLongPressStarted()
 	{
 		bool flag = m_currentHoveredPieceButton != null;
@@ -243,7 +247,16 @@
 
 	private void UnsubscribeEvents()
 	{
+		m_searchField.onValueChanged.RemoveListener(UpdateSearch);
+		m_searchField.onSelect.RemoveListener(SearchFieldSelect);
+		m_searchField.onDeselect.RemoveListener(SearchFieldDeselect);
 		ZInput.OnInputLayoutChanged -= OnLayoutChanged;
+		m_recentPieceList.PieceAdded -= OnRecentPieceAdded;
+		m_recentPieceList.PieceRemoved -= OnRecentPieceRemoved;
+		m_favoritePieceList.PieceAdded -= OnFavoritePieceAdded;
+		m_favoritePieceList.PieceRemoved -= OnFavoritePieceRemoved;
+		m_favoritePieceList.TagsChanged -= OnFavoriteTagsChanged;
+		m_favoritesDropdown.Closed -= OnFavoritesDropdownClosed;
 		TouchLongPress.Started -= OnTouchLongPressStarted;
 		TouchLongPress.Performed -= OnTouchLongPressPerformed;
 	}
@@ -718,6 +731,7 @@
 		}
 		if (m_favoritePieceList.TagCount > 0)
 		{
+			RefreshFavorites();
 			m_favoritesDropdown.Open(btn.transform.position, btn.Piece, m_favoritePieceList.GetTags(btn.Piece.gameObject.name));
 		}
 		else if (flag)
```

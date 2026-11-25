# `BuildUi.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+150/-78` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `ConfigureButtonNavigation() [Method Body Modified]`
- `FavoritePiece() [Method Body Modified]`
- `FocusPiece() [Method Body Modified]`
- `FocusPieceListScrolling() [Method Body Modified]`
- `FocusPieceListScrolling() [Method Removed]`
- `FocusScrollingAt() [Method Body Modified]`
- `FocusScrollingAt() [Method Removed]`
- `FocusTag() [Method Body Modified]`
- `FocusTagListScrolling() [Method Body Modified]`
- `FocusTagListScrolling() [Method Removed]`
- `GetCurrentTagButton() [Method Body Modified]`
- `GetSearchFieldNavigation() [Method Body Modified]`
- `GetSpecialButtonNavigation() [Method Body Modified]`
- `NavigationUpdate() [Method Body Modified]`
- `OnDestroy() [Method Body Modified]`
- `OnDestroy() [Method Removed]`
- `OnDisable() [Method Body Modified]`
- `OnEnable() [Method Body Modified]`
- `OnFavoritesDropdownClosed() [Method Body Modified]`
- `OnHoverPiece() [Method Body Modified]`
- `OnLayoutChanged() [Method Body Modified]`
- `OnNavigatedToPieceButton() [Method Body Modified]`
- `OnNavigatedToTag() [Method Body Modified]`
- `OnSelectTag() [Method Body Modified]`
- `OnTouchLongPressPerformed() [Method Body Modified]`
- `OpenBuildMenu() [Method Body Modified]`
- `PressedFavoriteButton() [Method Body Modified]`
- `PressedFavoriteButton() [Method Removed]`
- `ScrollToTop() [Method Body Modified]`
- `SelectFirstAvailableButton() [Method Body Modified]`
- `SelectFirstPiece() [Method Body Modified]`
- `SelectPiece() [Method Body Modified]`
- `SelectTag() [Method Body Modified]`
- `Start() [Method Body Modified]`
- `UpdatePieceButtons() [Method Body Modified]`
- `UpdatePieceSelection() [Method Body Modified]`
- `UpdateSearch() [Method Body Modified]`
- `UpdateTriggerNavigation() [Method Body Modified]`
- `m_lastSelectedPieceBtn [Field Removed, was GameObject]`
- `private IEnumerator FocusPieceListScrolling(RectTransform element)`
- `private IEnumerator FocusTagListScrolling(RectTransform element)`
- `private Navigation GetSearchFieldNavigation()`
- `private static void FocusScrollingAt(RectTransform target, ScrollRect scrollRect)`
- `private static void FocusScrollingAt(RectTransform target, ScrollRect scrollRect, bool instant = false)`
- `private void FocusTag(GameObject tagObject)`
- `private void OnDestroy()`
- `private void OnDisable()`
- `private void OnEnable()`
- `private void ScrollToSelected(bool instant = false)`
- `private void ScrollToTop(ScrollRect scrollRect)`
- `public void FavoritePiece(BuildUiPieceButton btn)`
- `public void PressedFavoriteButton(BuildUiPieceButton btn)`
- `public void SelectPiece(BuildUiPieceButton pieceButton)`
- `public void SelectTag(GameObject tagObject)`
- `static bool PressedGamepadFavorite()`
- `static bool PressedGamepadMouseFavorite()`

---

## 📝 Code Diff

```diff
--- a/BuildUi.cs
+++ b/BuildUi.cs
@@ -1,9 +1,9 @@
 using System;
-using System.Collections;
 using System.Collections.Generic;
 using System.IO;
 using System.Text;
 using GUIFramework;
+using TMPro;
 using UnityEngine;
 using UnityEngine.EventSystems;
 using UnityEngine.UI;
@@ -110,7 +110,9 @@
 
 	private BuildUiTagButton m_currentHoveredTagButton;
 
-	private GameObject m_lastSelectedPieceBtn;
+	private RectTransform tagListFocus;
+
+	private RectTransform pieceListFocus;
 
 	public bool SearchFieldFocused
 	{
@@ -164,11 +166,15 @@
 
 	private void Start()
 	{
+		Close();
+	}
+
+	private void OnEnable()
+	{
 		SubscribeEvents();
-		Close();
-	}
-
-	private void OnDestroy()
+	}
+
+	private void OnDisable()
 	{
 		UnsubscribeEvents();
 	}
@@ -227,7 +233,7 @@
 	{
 		if (m_currentHoveredPieceButton != null)
 		{
-			PressedFavoriteButton(m_currentHoveredPieceButton);
+			FavoritePiece(m_currentHoveredPieceButton);
 		}
 		else if (m_currentHoveredTagButton != null)
 		{
@@ -244,7 +250,11 @@
 
 	private void OnLayoutChanged()
 	{
-		EventSystem.current.SetSelectedGameObject(null);
+		GameObject currentSelectedGameObject = EventSystem.current.currentSelectedGameObject;
+		if (currentSelectedGameObject != null && currentSelectedGameObject.GetComponent<TMP_InputField>() == null)
+		{
+			EventSystem.current.SetSelectedGameObject(null);
+		}
 		m_favoritesDropdown.Close();
 	}
 
@@ -266,7 +276,7 @@
 		button.SetToggled(on: true);
 		if (select)
 		{
-			button.GetComponent<Selectable>().Select();
+			SelectTag(button.gameObject);
 		}
 	}
 
@@ -309,6 +319,7 @@
 			return;
 		}
 		SetCurrentTag(tagId);
+		OnHoverPiece(null);
 		UpdatePieceButtons();
 	}
 
@@ -316,6 +327,11 @@
 	{
 		OnHoverTag(tagId);
 		FocusTag(tagId);
+		m_currentHoveredPieceButton = null;
+		if (ZInput.IsExclusiveGamepadActive() && tagId != -10 && tagId != m_currentTagId)
+		{
+			OnSelectTag(tagId);
+		}
 	}
 
 	private void RemoveTag(int tagId)
@@ -372,10 +388,11 @@
 			m_previousPieceButtonsTemp.Push(m_pieceButtons[i]);
 		}
 		m_pieceButtons.Clear();
-		foreach (Piece tempPiece in m_tempPieces)
-		{
+		for (int j = 0; j < m_tempPieces.Count; j++)
+		{
+			Piece piece = m_tempPieces[j];
 			BuildUiPieceButton result;
-			if (tempPiece.m_repairPiece || tempPiece.m_removePiece)
+			if (piece.m_repairPiece || piece.m_removePiece)
 			{
 				if (!pieceList.ShowTags)
 				{
@@ -396,7 +413,8 @@
 				m_pieceButtons.Add(result);
 			}
 			result.gameObject.SetActive(value: true);
-			result.Setup(tempPiece, this);
+			result.name = $"BuildPieceButton_{j}";
+			result.Setup(piece, this);
 		}
 		m_tempPieces.Clear();
 		BuildUiPieceButton result2;
@@ -420,6 +438,7 @@
 		if (!string.IsNullOrEmpty(term) && m_currentTagId != -1)
 		{
 			SetCurrentTag(-1, select: false);
+			FocusTag(-1);
 			UpdatePieceButtons();
 			return;
 		}
@@ -527,18 +546,17 @@
 		m_currentPieceList = tabIndex;
 		m_favoritesDropdown.Close();
 		UpdateTagButtons(refreshOnly);
-		SelectFirstAvailableButton();
 	}
 
 	private void SelectFirstAvailableButton()
 	{
 		if (m_tagListContainer.gameObject.activeSelf)
 		{
-			m_showAllTagsButton.GetComponent<Selectable>().Select();
+			SelectTag(m_showAllTagsButton.gameObject);
 		}
 		else if (m_pieceButtonsContainer.GetActiveChildCount() > 0)
 		{
-			m_pieceButtonsContainer.GetActiveChild(0).GetComponent<Selectable>().Select();
+			SelectFirstPiece();
 		}
 	}
 
@@ -633,6 +651,7 @@
 		}
 		gameObject.SetActive(value: true);
 		ConfigureButtonNavigation();
+		ScrollToSelected(instant: true);
 	}
 
 	private void UpdatePieceSelection(Piece selectedPiece)
@@ -644,7 +663,7 @@
 			{
 				if (pieceButton.gameObject.activeSelf && pieceButton.Piece.gameObject.name == selectedPiece.gameObject.name)
 				{
-					EventSystem.current.SetSelectedGameObject(pieceButton.gameObject);
+					SelectPiece(pieceButton);
 					flag = true;
 					break;
 				}
@@ -652,12 +671,12 @@
 		}
 		if (!flag && m_pieceButtonsContainer.GetActiveChildCount() > 0)
 		{
-			EventSystem.current.SetSelectedGameObject(m_pieceButtonsContainer.GetActiveChild(0).gameObject);
+			SelectFirstPiece();
 			flag = true;
 		}
 		if (!flag && m_tagListContainer.gameObject.activeSelf)
 		{
-			EventSystem.current.SetSelectedGameObject(m_showAllTagsButton.gameObject);
+			SelectTag(m_showAllTagsButton.gameObject);
 		}
 	}
 
@@ -672,6 +691,10 @@
 	{
 		if (!(button == null) || !m_favoritesDropdown.IsOpen())
 		{
+			if (!button && ZInput.IsExclusiveGamepadActive())
+			{
+				ScrollToTop(m_pieceScrollRect);
+			}
 			m_currentHoveredPieceButton = button;
 			Hud.instance.OnHoverPiece(button?.Piece);
 		}
@@ -679,14 +702,13 @@
 
 	public void OnNavigatedToPieceButton(BuildUiPieceButton button)
 	{
-		OnHoverPiece(button);
 		if ((bool)button)
 		{
 			FocusPiece(button);
 		}
 	}
 
-	public void PressedFavoriteButton(BuildUiPieceButton btn)
+	public void FavoritePiece(BuildUiPieceButton btn)
 	{
 		Piece piece = btn.Piece;
 		bool flag = m_favoritePieceList.IsFavorite(piece);
@@ -744,11 +766,29 @@
 		return result;
 	}
 
+	public void SelectTag(GameObject tagObject)
+	{
+		if (!EventSystem.current.alreadySelecting)
+		{
+			EventSystem.current.SetSelectedGameObject(tagObject);
+			FocusTag(tagObject);
+		}
+	}
+
+	public void SelectPiece(BuildUiPieceButton pieceButton)
+	{
+		if (!EventSystem.current.alreadySelecting)
+		{
+			EventSystem.current.SetSelectedGameObject(pieceButton.gameObject);
+			FocusPiece(pieceButton);
+		}
+	}
+
 	public void SelectFirstPiece()
 	{
 		if (m_pieceButtonsContainer.GetActiveChildCount() > 0)
 		{
-			EventSystem.current.SetSelectedGameObject(m_pieceButtonsContainer.GetActiveChild(0).gameObject);
+			SelectPiece(m_pieceButtonsContainer.GetActiveChild(0).GetComponent<BuildUiPieceButton>());
 		}
 	}
 
@@ -798,12 +838,13 @@
 
 	private void ConfigureButtonNavigation()
 	{
-		GridNavigationUtility.ConfigureExplicitNavigation(m_pieceButtonsContainer, GetPieceListEdgeNavigation());
+		GridNavigationUtility.ConfigureExplicitNavigation(m_pieceButtonsContainer, GetPieceListEdgeNavigation(), shouldWrapHorizontally: true);
 		GridNavigationUtility.ConfigureExplicitNavigation(m_tagListScrollContent, GetTagListEdgeNavigation());
 		if (m_specialPieceButton != null)
 		{
 			m_specialPieceButton.GetComponent<Button>().navigation = GetSpecialButtonNavigation();
 		}
+		m_searchField.navigation = GetSearchFieldNavigation();
 	}
 
 	private void NavigationUpdate()
@@ -812,25 +853,24 @@
 		{
 			return;
 		}
-		if ((ZInput.IsGamepadActive() && ZInput.GetButtonDown("JoyButtonX")) || (ZInput.IsGamepadMouseActive() && ZInput.GetButtonDown("JoyRStick")))
+		if ((PressedGamepadFavorite() || PressedGamepadMouseFavorite()) && EventSystem.current.currentSelectedGameObject != m_searchField.gameObject)
 		{
 			if (!m_favoritesDropdown.IsOpen() && (bool)m_currentHoveredPieceButton)
 			{
-				m_lastSelectedPieceBtn = EventSystem.current.currentSelectedGameObject;
-				PressedFavoriteButton(m_currentHoveredPieceButton);
+				FavoritePiece(m_currentHoveredPieceButton);
 			}
 			else if (m_favoritesDropdown.IsOpen())
 			{
 				m_favoritesDropdown.Close();
 			}
+			if (m_currentHoveredTagButton != null && m_currentHoveredPieceButton == null)
+			{
+				m_currentHoveredTagButton.OnDelete(null);
+			}
 		}
 		if ((ZInput.GetKey(KeyCode.F) || ZInput.GetButtonDown("JoyLStick")) && m_searchField.gameObject.activeInHierarchy)
 		{
 			m_searchField.ActivateInputField();
-		}
-		if ((ZInput.GetButtonDown("JoyButtonX") || (ZInput.IsGamepadMouseActive() && ZInput.GetButtonDown("JoyRStick"))) && m_currentHoveredTagButton != null)
-		{
-			m_currentHoveredTagButton.OnDelete(null);
 		}
 		if (ZInput.GetButtonDown("JoyButtonY") && m_specialPieceButton != null)
 		{
@@ -849,6 +889,7 @@
 				Hud.CloseBuildUi();
 			}
 		}
+		UpdateTriggerNavigation();
 		if (ZInput.IsExclusiveGamepadActive() && !ZInput.IsTouchActive())
 		{
 			GameObject currentSelectedGameObject = EventSystem.current.currentSelectedGameObject;
@@ -857,32 +898,37 @@
 				SelectFirstAvailableButton();
 			}
 		}
+		if (ZInput.IsExclusiveGamepadActive())
+		{
+			ScrollToSelected();
+		}
+		static bool PressedGamepadFavorite()
+		{
+			if (ZInput.IsGamepadActive())
+			{
+				return ZInput.GetButtonDown("JoyButtonX");
+			}
+			return false;
+		}
+		static bool PressedGamepadMouseFavorite()
+		{
+			if (ZInput.IsGamepadMouseActive())
+			{
+				return ZInput.GetButtonDown("JoyRStick");
+			}
+			return false;
+		}
 	}
 
 	private void UpdateTriggerNavigation()
 	{
-		int num = (ZInput.GetButtonDown("JoyLTrigger") ? (-1) : 0) + (ZInput.GetButtonDown("JoyRTrigger") ? 1 : 0);
-		if (num == 0 || m_favoritesDropdown.IsOpen())
-		{
-			return;
-		}
-		int num2 = -1;
-		if ((bool)EventSystem.current.currentSelectedGameObject?.GetComponent<BuildUiTagButton>())
-		{
-			num2 = 0;
-		}
-		else if ((bool)EventSystem.current.currentSelectedGameObject?.GetComponent<BuildUiPieceButton>())
-		{
-			num2 = 1;
-		}
-		int num3 = Mathf.Clamp(num2 + num, 0, 1);
-		if (num2 != -1 && num3 != num2)
-		{
-			if (num3 == 0)
-			{
-				EventSystem.current.SetSelectedGameObject(GetCurrentTagButton());
-			}
-			else
+		if (!m_favoritesDropdown.IsOpen())
+		{
+			if (ZInput.GetButtonDown("JoyLTrigger"))
+			{
+				SelectTag(GetCurrentTagButton());
+			}
+			if (ZInput.GetButtonDown("JoyRTrigger") && (!m_currentHoveredPieceButton || m_currentHoveredPieceButton == m_specialPieceButton))
 			{
 				SelectFirstPiece();
 			}
@@ -891,48 +937,64 @@
 
 	private void OnFavoritesDropdownClosed()
 	{
-		if ((object)m_lastSelectedPieceBtn != null)
-		{
-			EventSystem.current.SetSelectedGameObject(m_lastSelectedPieceBtn);
-			m_lastSelectedPieceBtn = null;
+		if ((object)m_currentHoveredPieceButton != null)
+		{
+			EventSystem.current.SetSelectedGameObject(m_currentHoveredPieceButton.gameObject);
 		}
 	}
 
 	private void FocusTag(int tagId)
 	{
-		if (ZInput.IsExclusiveGamepadActive() && !ZInput.IsTouchActive() && TryGetTagButtonById(tagId, out var button))
-		{
-			StartCoroutine(FocusTagListScrolling(button.transform as RectTransform));
+		if (TryGetTagButtonById(tagId, out var button))
+		{
+			FocusTag(button.gameObject);
+		}
+	}
+
+	private void FocusTag(GameObject tagObject)
+	{
+		if (ZInput.IsExclusiveGamepadActive() && !ZInput.IsTouchActive())
+		{
+			tagListFocus = tagObject.transform as RectTransform;
+			pieceListFocus = null;
 		}
 	}
 
 	private void FocusPiece(BuildUiPieceButton button)
 	{
+		OnHoverPiece(button);
 		if (ZInput.IsExclusiveGamepadActive() && !ZInput.IsTouchActive())
 		{
-			StartCoroutine(FocusPieceListScrolling(button.GetComponent<RectTransform>()));
-		}
-	}
-
-	private IEnumerator FocusTagListScrolling(RectTransform element)
-	{
-		yield return null;
-		Canvas.ForceUpdateCanvases();
-		FocusScrollingAt(element, m_tagListScrollRect);
-	}
-
-	private IEnumerator FocusPieceListScrolling(RectTransform element)
-	{
-		yield return null;
-		Canvas.ForceUpdateCanvases();
-		FocusScrollingAt(element, m_pieceScrollRect);
-	}
-
-	private static void FocusScrollingAt(RectTransform target, ScrollRect scrollRect)
+			pieceListFocus = button.gameObject.GetComponent<RectTransform>();
+		}
+	}
+
+	private void ScrollToSelected(bool instant = false)
+	{
+		if ((bool)tagListFocus)
+		{
+			FocusScrollingAt(tagListFocus, m_tagListScrollRect, instant);
+		}
+		if ((bool)pieceListFocus && pieceListFocus.gameObject.activeInHierarchy)
+		{
+			FocusScrollingAt(pieceListFocus, m_pieceScrollRect, instant);
+		}
+	}
+
+	private void ScrollToTop(ScrollRect scrollRect)
+	{
+		scrollRect.content.anchoredPosition = new Vector2(0f, 0f);
+	}
+
+	private static void FocusScrollingAt(RectTransform target, ScrollRect scrollRect, bool instant = false)
 	{
 		float y = scrollRect.viewport.InverseTransformPoint(target.position).y;
 		float y2 = scrollRect.viewport.rect.center.y;
 		float num = (y - y2) * 1f;
+		if (!instant)
+		{
+			num *= 0.1f;
+		}
 		if (!Mathf.Approximately(num, 0f))
 		{
 			Vector2 anchoredPosition = scrollRect.content.anchoredPosition;
@@ -970,6 +1032,16 @@
 		};
 	}
 
+	private Navigation GetSearchFieldNavigation()
+	{
+		return new Navigation
+		{
+			mode = Navigation.Mode.Explicit,
+			selectOnDown = GetCurrentTagButton().GetComponent<Selectable>(),
+			selectOnRight = m_specialPieceButton?.GetComponent<Button>()
+		};
+	}
+
 	private GameObject GetCurrentTagButton()
 	{
 		if (!TryGetTagButtonById(m_currentTagId, out var button))
```

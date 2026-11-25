# `BuildUiPieceButton.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Awake() [Method Body Modified]`
- `OnDestroy() [Method Body Modified]`
- `OnMiddleClick() [Method Body Modified]`
- `OnPointerEnter() [Method Body Modified]`
- `Setup() [Method Body Modified]`
- `private void OnDestroy()`

---

## 📝 Code Diff

```diff
--- a/BuildUiPieceButton.cs
+++ b/BuildUiPieceButton.cs
@@ -40,11 +40,17 @@
 		inputHandler3.m_onMiddleClick = (Action<UIInputHandler>)Delegate.Combine(inputHandler3.m_onMiddleClick, new Action<UIInputHandler>(OnMiddleClick));
 		m_button = GetComponent<Button>();
 		m_button.onClick.AddListener(OnClickButton);
+		Localization.OnLanguageChange = (Action)Delegate.Combine(Localization.OnLanguageChange, new Action(RefreshSearchTerm));
+	}
+
+	private void OnDestroy()
+	{
+		Localization.OnLanguageChange = (Action)Delegate.Remove(Localization.OnLanguageChange, new Action(RefreshSearchTerm));
 	}
 
 	private void OnMiddleClick(UIInputHandler obj)
 	{
-		m_buildUi.PressedFavoriteButton(this);
+		m_buildUi.FavoritePiece(this);
 	}
 
 	private void OnPointerEnter(UIInputHandler obj)
@@ -81,7 +87,6 @@
 		RefreshFavorite();
 		m_upgradeArrow.gameObject.SetActive(Piece.m_isUpgrade);
 		RefreshSearchTerm();
-		Localization.OnLanguageChange = (Action)Delegate.Combine(Localization.OnLanguageChange, new Action(RefreshSearchTerm));
 		UpdateRequirements();
 	}
 
```

# `BuildUiFavoritesDropdown.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+10/-10` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/BuildUiFavoritesDropdown.cs
+++ b/BuildUiFavoritesDropdown.cs
@@ -34,20 +34,20 @@
 	{
 		m_buildUi = GetComponentInParent<BuildUi>();
 		UIInputHandler component = GetComponent<UIInputHandler>();
-		component.m_onPointerExit = (Action<UIInputHandler>)Delegate.Combine(component.m_onPointerExit, (Action<UIInputHandler>)delegate
+		component.m_onPointerExit = (Action<UIInputHandler>)Delegate.Combine(component.m_onPointerExit, (Action<UIInputHandler>)((UIInputHandler handler) =>
 		{
 			m_mouseOver = false;
-		});
-		component.m_onPointerEnter = (Action<UIInputHandler>)Delegate.Combine(component.m_onPointerEnter, (Action<UIInputHandler>)delegate
+		}));
+		component.m_onPointerEnter = (Action<UIInputHandler>)Delegate.Combine(component.m_onPointerEnter, (Action<UIInputHandler>)((UIInputHandler handler) =>
 		{
 			m_mouseOver = true;
-		});
-		base.gameObject.SetActive(value: false);
+		}));
+		gameObject.SetActive(value: false);
 	}
 
 	public bool IsOpen()
 	{
-		return base.gameObject.activeSelf;
+		return gameObject.activeSelf;
 	}
 
 	public void OnClickRemoveFromFavorites()
@@ -100,7 +100,7 @@
 
 	public void Open(Vector2 pos, Piece pieceName, HashSet<int> categories)
 	{
-		base.transform.position = pos;
+		transform.position = pos;
 		m_currentPiece = pieceName;
 		foreach (BuildUiFavoriteCategoryCheckButton checkButton in m_checkButtons)
 		{
@@ -108,16 +108,16 @@
 		}
 		m_openTimer = 0f;
 		m_mouseOver = true;
-		base.gameObject.SetActive(value: true);
+		gameObject.SetActive(value: true);
 		EventSystem.current.SetSelectedGameObject(removeFromFavsButton.gameObject);
 		backgroundCloseButton.gameObject.SetActive(value: true);
 	}
 
 	public void Close()
 	{
-		if (base.gameObject.activeSelf)
+		if (gameObject.activeSelf)
 		{
-			base.gameObject.SetActive(value: false);
+			gameObject.SetActive(value: false);
 			backgroundCloseButton.gameObject.SetActive(value: false);
 			m_currentPiece = null;
 			Closed?.Invoke();
```

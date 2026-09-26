# `BuildUiTagButton.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/BuildUiTagButton.cs
+++ b/BuildUiTagButton.cs
@@ -56,7 +56,7 @@
 		UIInputHandler inputHandler3 = m_inputHandler;
 		inputHandler3.m_onPointerExit = (Action<UIInputHandler>)Delegate.Combine(inputHandler3.m_onPointerExit, new Action<UIInputHandler>(OnPointerExit));
 		GetComponent<Button>().onClick.AddListener(OnClick);
-		m_rectTransform = base.transform as RectTransform;
+		m_rectTransform = transform as RectTransform;
 		m_baseHeight = m_rectTransform.sizeDelta.y;
 	}
 
@@ -77,7 +77,7 @@
 		if (addCategoryButton)
 		{
 			m_tagId = -10;
-			base.gameObject.name = "Add tag button";
+			gameObject.name = "Add tag button";
 		}
 		text = Localization.instance.Localize("$hud_addfavoritecategory");
 		foreach (TextMeshProUGUI textMesh in m_textMeshes)
```

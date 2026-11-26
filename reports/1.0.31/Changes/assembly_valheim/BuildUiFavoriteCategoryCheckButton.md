# `BuildUiFavoriteCategoryCheckButton.cs` Diff (`1.0.30` $\rightarrow$ `1.0.31`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+0/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Awake() [Method Body Modified]`
- `Awake() [Method Removed]`
- `OnClick() [Method Body Modified]`
- `private void Awake()`

---

## 📝 Code Diff

```diff
--- a/BuildUiFavoriteCategoryCheckButton.cs
+++ b/BuildUiFavoriteCategoryCheckButton.cs
@@ -32,11 +32,6 @@
 		}
 	}
 
-	private void Awake()
-	{
-		m_check.gameObject.SetActive(value: false);
-	}
-
 	private void OnClick()
 	{
 		m_check.gameObject.SetActive(m_favoritesDropdown.ToggleCategory(Category));
```

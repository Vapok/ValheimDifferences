# `AchievementsGui.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+15/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `CloseDetails() [Method Body Modified]`
- `NavigateAchievements() [Method Body Modified]`
- `OnDisable() [Method Body Modified]`
- `OnEnable() [Method Body Modified]`
- `ResetSelected() [Method Body Modified]`
- `Start() [Method Body Modified]`
- `Update() [Method Body Modified]`
- `private void OnDisable()`
- `private void ResetSelected()`

---

## 📝 Code Diff

```diff
--- a/AchievementsGui.cs
+++ b/AchievementsGui.cs
@@ -71,7 +71,6 @@
 	private void Start()
 	{
 		m_width = UnityEngine.Object.FindAnyObjectByType<GridLayoutGroup>().constraintCount;
-		m_selected = new Vector2i(0, 0);
 	}
 
 	private void Update()
@@ -96,7 +95,7 @@
 	private void NavigateAchievements()
 	{
 		m_achievementsList[m_previousSelectedIndex].transform.Find("selected").gameObject.SetActive(value: false);
-		if (!ZInput.IsGamepadActive())
+		if (!ZInput.IsExclusiveGamepadActive() || ZInput.IsTouchActive())
 		{
 			return;
 		}
@@ -207,6 +206,20 @@
 	private void OnEnable()
 	{
 		CloseDetails();
+		ResetSelected();
+		ZInput.OnInputLayoutChanged += ResetSelected;
+		ZInput.OnTouchLayoutChanged += ResetSelected;
+	}
+
+	private void OnDisable()
+	{
+		ZInput.OnInputLayoutChanged -= ResetSelected;
+		ZInput.OnTouchLayoutChanged -= ResetSelected;
+	}
+
+	private void ResetSelected()
+	{
+		m_selected = new Vector2i(0, 0);
 	}
 
 	private void CloseDetails()
```

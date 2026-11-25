# `GridNavigationUtility.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+47/-14` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `DefaultOrWrap() [Method Body Modified]`
- `GetChildSelectables() [Method Body Modified]`
- `GetColumnCountFromLaidOutChildren() [Method Body Modified]`
- `GetSelectable() [Method Body Modified]`
- `GetSelectableBelow() [Method Body Modified]`
- `private static Selectable DefaultOrWrap(Selectable defaultOption, int nextIndex)`
- `private static Selectable GetSelectable(int index)`
- `private static Selectable GetSelectableBelow(int i, int columns)`
- `public static void ConfigureExplicitNavigation(RectTransform grid, Navigation gridEdgeNavigation = default(Navigation))`
- `public static void ConfigureExplicitNavigation(RectTransform grid, Navigation gridEdgeNavigation = default(Navigation), bool shouldWrapHorizontally = false)`

---

## 📝 Code Diff

```diff
--- a/GridNavigationUtility.cs
+++ b/GridNavigationUtility.cs
@@ -7,8 +7,11 @@
 {
 	private static List<Selectable> _selectables;
 
-	public static void ConfigureExplicitNavigation(RectTransform grid, Navigation gridEdgeNavigation = default(Navigation))
+	private static bool _shouldWrapHorizontally;
+
+	public static void ConfigureExplicitNavigation(RectTransform grid, Navigation gridEdgeNavigation = default(Navigation), bool shouldWrapHorizontally = false)
 	{
+		_shouldWrapHorizontally = shouldWrapHorizontally;
 		Canvas.ForceUpdateCanvases();
 		LayoutRebuilder.ForceRebuildLayoutImmediate(grid);
 		Canvas.ForceUpdateCanvases();
@@ -27,16 +30,55 @@
 				int num2 = i / num;
 				int num3 = i % num;
 				bool flag = num3 > 0;
-				navigation.selectOnLeft = (flag ? GetSelectable(i - 1) : gridEdgeNavigation.selectOnLeft);
+				navigation.selectOnLeft = (flag ? GetSelectable(i - 1) : DefaultOrWrap(gridEdgeNavigation.selectOnLeft, i - 1));
 				bool flag2 = num3 < num - 1 && i + 1 < _selectables.Count;
-				navigation.selectOnRight = (flag2 ? GetSelectable(i + 1) : gridEdgeNavigation.selectOnRight);
+				navigation.selectOnRight = (flag2 ? GetSelectable(i + 1) : DefaultOrWrap(gridEdgeNavigation.selectOnRight, i + 1));
 				bool flag3 = num2 > 0;
 				navigation.selectOnUp = (flag3 ? GetSelectable(i - num) : gridEdgeNavigation.selectOnUp);
-				int num4 = i + num;
-				navigation.selectOnDown = ((num4 < _selectables.Count) ? GetSelectable(num4) : gridEdgeNavigation.selectOnDown);
+				Selectable selectableBelow = GetSelectableBelow(i, num);
+				navigation.selectOnDown = (selectableBelow ? selectableBelow : gridEdgeNavigation.selectOnDown);
 				_selectables[i].navigation = navigation;
 			}
+			_selectables.Clear();
 		}
+	}
+
+	private static Selectable GetSelectable(int index)
+	{
+		if (index < 0 || index >= _selectables.Count)
+		{
+			return null;
+		}
+		return _selectables[index];
+	}
+
+	private static Selectable GetSelectableBelow(int i, int columns)
+	{
+		Selectable result = null;
+		int num = i + columns;
+		if (num < _selectables.Count)
+		{
+			result = GetSelectable(num);
+		}
+		else if (i / columns < (_selectables.Count - 1) / columns)
+		{
+			List<Selectable> selectables = _selectables;
+			result = selectables[selectables.Count - 1];
+		}
+		return result;
+	}
+
+	private static Selectable DefaultOrWrap(Selectable defaultOption, int nextIndex)
+	{
+		if (defaultOption != null)
+		{
+			return defaultOption;
+		}
+		if (_shouldWrapHorizontally && nextIndex > 0 && nextIndex < _selectables.Count)
+		{
+			return _selectables[nextIndex];
+		}
+		return null;
 	}
 
 	private static IEnumerable<Selectable> GetChildSelectables(RectTransform grid)
@@ -53,15 +95,6 @@
 				}
 			}
 		}
-	}
-
-	private static Selectable GetSelectable(int index)
-	{
-		if (index < 0 || index >= _selectables.Count)
-		{
-			return null;
-		}
-		return _selectables[index];
 	}
 
 	private static int GetColumnCountFromLaidOutChildren(List<Selectable> selectables)
```

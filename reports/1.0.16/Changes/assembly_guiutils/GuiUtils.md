# `GuiUtils.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_guiutils.dll`
* **Status**: `🟡 MODIFIED` (`+6/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `public static void SetNavigationHorizontal(Selectable left, Selectable right)`

---

## 📝 Code Diff

```diff
--- a/GuiUtils.cs
+++ b/GuiUtils.cs
@@ -35,4 +35,10 @@
 		SetNavigationDown(top, bottom);
 		SetNavigationUp(bottom, top);
 	}
+
+	public static void SetNavigationHorizontal(Selectable left, Selectable right)
+	{
+		SetNavigationRight(left, right);
+		SetNavigationLeft(right, left);
+	}
 }
```

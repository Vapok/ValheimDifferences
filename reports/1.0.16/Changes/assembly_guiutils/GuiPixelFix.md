# `GuiPixelFix.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_guiutils.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/GuiPixelFix.cs
+++ b/GuiPixelFix.cs
@@ -4,7 +4,7 @@
 {
 	private void LateUpdate()
 	{
-		RectTransform rectTransform = base.transform as RectTransform;
+		RectTransform rectTransform = transform as RectTransform;
 		if (!(rectTransform.parent == null))
 		{
 			Rect rect = (rectTransform.parent as RectTransform).rect;
```

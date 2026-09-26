# `Valheim.UI/ScrollRectExtensions.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+12/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/ScrollRectExtensions.cs
+++ b/Valheim.UI/ScrollRectExtensions.cs
@@ -9,10 +9,18 @@
 	{
 		Vector2 vector = scrollRect.viewport.transform.InverseTransformPoint(child.position);
 		float height = scrollRect.viewport.rect.height;
-		bool num = vector.y > 0f;
-		bool flag = 0f - vector.y + child.rect.height > height;
-		float num2 = (num ? (0f - vector.y) : (flag ? (0f - vector.y + child.rect.height - height) : 0f));
-		scrollRect.content.anchoredPosition = new Vector2(0f, scrollRect.content.anchoredPosition.y + num2);
+		bool flag = vector.y > 0f;
+		bool flag2 = 0f - vector.y + child.rect.height > height;
+		float num;
+		if (flag)
+		{
+			num = 0f - vector.y;
+		}
+		else
+		{
+			num = (flag2 ? (0f - vector.y + child.rect.height - height) : 0f);
+		}
+		scrollRect.content.anchoredPosition = new Vector2(0f, scrollRect.content.anchoredPosition.y + num);
 	}
 
 	public static bool IsVisible(this ScrollRect scrollRect, RectTransform child)
```

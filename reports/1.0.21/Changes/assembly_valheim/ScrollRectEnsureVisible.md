# `ScrollRectEnsureVisible.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+24/-21` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `CenterOnItem() [Method Body Modified]`
- `Reset() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/ScrollRectEnsureVisible.cs
+++ b/ScrollRectEnsureVisible.cs
@@ -34,29 +34,32 @@
 
 	public void CenterOnItem(RectTransform target)
 	{
-		if (!mInitialized)
+		if (!ZInput.IsTouchActive())
 		{
-			Initialize();
+			if (!mInitialized)
+			{
+				Initialize();
+			}
+			Vector3 worldPointInWidget = GetWorldPointInWidget(mScrollTransform, GetWidgetWorldPoint(target));
+			Vector3 vector = GetWorldPointInWidget(mScrollTransform, GetWidgetWorldPoint(maskTransform)) - worldPointInWidget;
+			vector.z = 0f;
+			if (!mScrollRect.horizontal)
+			{
+				vector.x = 0f;
+			}
+			if (!mScrollRect.vertical)
+			{
+				vector.y = 0f;
+			}
+			Vector2 vector2 = new Vector2(vector.x / (mContent.rect.size.x - mScrollTransform.rect.size.x), vector.y / (mContent.rect.size.y - mScrollTransform.rect.size.y));
+			Vector2 normalizedPosition = mScrollRect.normalizedPosition - vector2;
+			if (mScrollRect.movementType != ScrollRect.MovementType.Unrestricted)
+			{
+				normalizedPosition.x = Mathf.Clamp01(normalizedPosition.x);
+				normalizedPosition.y = Mathf.Clamp01(normalizedPosition.y);
+			}
+			mScrollRect.normalizedPosition = normalizedPosition;
 		}
-		Vector3 worldPointInWidget = GetWorldPointInWidget(mScrollTransform, GetWidgetWorldPoint(target));
-		Vector3 vector = GetWorldPointInWidget(mScrollTransform, GetWidgetWorldPoint(maskTransform)) - worldPointInWidget;
-		vector.z = 0f;
-		if (!mScrollRect.horizontal)
-		{
-			vector.x = 0f;
-		}
-		if (!mScrollRect.vertical)
-		{
-			vector.y = 0f;
-		}
-		Vector2 vector2 = new Vector2(vector.x / (mContent.rect.size.x - mScrollTransform.rect.size.x), vector.y / (mContent.rect.size.y - mScrollTransform.rect.size.y));
-		Vector2 normalizedPosition = mScrollRect.normalizedPosition - vector2;
-		if (mScrollRect.movementType != ScrollRect.MovementType.Unrestricted)
-		{
-			normalizedPosition.x = Mathf.Clamp01(normalizedPosition.x);
-			normalizedPosition.y = Mathf.Clamp01(normalizedPosition.y);
-		}
-		mScrollRect.normalizedPosition = normalizedPosition;
 	}
 
 	private void Reset()
```

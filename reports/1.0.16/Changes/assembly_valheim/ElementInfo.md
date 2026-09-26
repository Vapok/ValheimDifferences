# `Valheim.UI/ElementInfo.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/ElementInfo.cs
+++ b/Valheim.UI/ElementInfo.cs
@@ -37,7 +37,7 @@
 		{
 			if (m_background == null)
 			{
-				m_background = base.gameObject.GetComponent<Image>();
+				m_background = gameObject.GetComponent<Image>();
 			}
 			return m_background;
 		}
@@ -61,7 +61,7 @@
 		{
 			if (m_rectTransform == null)
 			{
-				m_rectTransform = base.transform as RectTransform;
+				m_rectTransform = transform as RectTransform;
 			}
 			return m_rectTransform;
 		}
@@ -257,12 +257,12 @@
 	{
 		Radius = radius + startOffset;
 		Alpha = 0f;
-		manager.StartTween(() => Alpha, delegate(float val)
+		manager.StartTween(() => Alpha, (float val) =>
 		{
 			Alpha = val;
 		}, id, 0.8f, duration + 0.1f, alphaEasingType);
 		manager.StartTween(m_inventoryInfo.SetAlpha, id, 0f, 1f, duration + 0.1f, alphaEasingType);
-		manager.StartTween(() => Radius, delegate(float val)
+		manager.StartTween(() => Radius, (float val) =>
 		{
 			Radius = val;
 		}, id, radius, duration, positionEasingType);
@@ -270,15 +270,15 @@
 
 	internal void CloseAnimation(RadialMenuAnimationManager manager, string id, float duration, float radius, float startOffset, EasingType alphaEasingType, EasingType positionEasingType)
 	{
-		manager.StartTween(() => Alpha, delegate(float val)
+		manager.StartTween(() => Alpha, (float val) =>
 		{
 			Alpha = val;
 		}, id, 0f, duration, alphaEasingType);
 		manager.StartTween(m_inventoryInfo.SetAlpha, id, 1f, 0f, duration, alphaEasingType);
-		manager.StartTween(() => Radius, delegate(float val)
+		manager.StartTween(() => Radius, (float val) =>
 		{
 			Radius = val;
-		}, id, radius + startOffset, duration + 0.1f, positionEasingType, delegate
+		}, id, radius + startOffset, duration + 0.1f, positionEasingType, () =>
 		{
 			Radius = radius;
 		});
```

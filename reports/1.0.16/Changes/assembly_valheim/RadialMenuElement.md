# `Valheim.UI/RadialMenuElement.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+10/-10` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/RadialMenuElement.cs
+++ b/Valheim.UI/RadialMenuElement.cs
@@ -45,7 +45,7 @@
 			{
 				return m_rectTransform;
 			}
-			m_rectTransform = base.transform as RectTransform;
+			m_rectTransform = transform as RectTransform;
 			RectTransform rectTransform = m_rectTransform;
 			RectTransform rectTransform2 = m_rectTransform;
 			Vector2 vector = (m_rectTransform.pivot = new Vector2(0.5f, 0.5f));
@@ -78,7 +78,7 @@
 
 	public string Description { get; protected set; }
 
-	public string ID => base.gameObject.GetInstanceID().ToString();
+	public string ID => gameObject.GetInstanceID().ToString();
 
 	public Func<RadialBase, RadialArray<RadialMenuElement>, bool> AdvancedCloseOnInteract { get; set; }
 
@@ -213,13 +213,13 @@
 	internal void OpenAnimation(RadialMenuAnimationManager manager, string id, float duration, float distance, float startOffset, EasingType alphaEasingType, EasingType positionEasingType)
 	{
 		LocalPosition = LocalPosition.normalized * (distance + startOffset);
-		manager.StartTween(() => LocalPosition, delegate(Vector3 val)
+		manager.StartTween(() => LocalPosition, (Vector3 val) =>
 		{
 			LocalPosition = val;
 		}, id, LocalPosition.normalized * distance, duration, positionEasingType);
 		float alpha = Alpha;
 		Alpha = 0f;
-		manager.StartTween(() => Alpha, delegate(float val)
+		manager.StartTween(() => Alpha, (float val) =>
 		{
 			Alpha = val;
 		}, id, alpha, duration + 0.1f, alphaEasingType);
@@ -227,11 +227,11 @@
 
 	internal void CloseAnimation(RadialMenuAnimationManager manager, string id, float duration, float distance, float startOffset, EasingType alphaEasingType, EasingType positionEasingType)
 	{
-		manager.StartTween(() => LocalPosition, delegate(Vector3 val)
+		manager.StartTween(() => LocalPosition, (Vector3 val) =>
 		{
 			LocalPosition = val;
 		}, id, LocalPosition.normalized * (distance + startOffset), duration + 0.1f, positionEasingType);
-		manager.StartTween(() => Alpha, delegate(float val)
+		manager.StartTween(() => Alpha, (float val) =>
 		{
 			Alpha = val;
 		}, id, 0f, duration + 0.1f, alphaEasingType);
@@ -239,7 +239,7 @@
 
 	internal void StartHoverSelect(RadialMenuAnimationManager manager, float duration, EasingType easingType, Action onEnd)
 	{
-		manager.StartUniqueTween(() => Hovering, delegate(float val)
+		manager.StartUniqueTween(() => Hovering, (float val) =>
 		{
 			Hovering = val;
 		}, ID + "_hov", 1f, (Hovering > 0f) ? (duration - duration * Hovering) : duration, easingType, onEnd);
@@ -247,7 +247,7 @@
 
 	internal void ResetHoverSelect(RadialMenuAnimationManager manager, float duration, EasingType easingType)
 	{
-		manager.StartUniqueTween(() => Hovering, delegate(float val)
+		manager.StartUniqueTween(() => Hovering, (float val) =>
 		{
 			Hovering = val;
 		}, ID + "_hov", 0f, Hovering * duration, easingType);
@@ -255,7 +255,7 @@
 
 	internal void StartNudge(RadialMenuAnimationManager manager, float distance, float duration, EasingType easingType)
 	{
-		manager.StartUniqueTween(() => LocalPosition, delegate(Vector3 val)
+		manager.StartUniqueTween(() => LocalPosition, (Vector3 val) =>
 		{
 			LocalPosition = val;
 		}, ID + "_nug", LocalPosition.normalized * distance, duration, easingType);
@@ -263,7 +263,7 @@
 
 	internal void ResetNudge(RadialMenuAnimationManager manager, float distance, float duration, EasingType easingType)
 	{
-		manager.StartUniqueTween(() => LocalPosition, delegate(Vector3 val)
+		manager.StartUniqueTween(() => LocalPosition, (Vector3 val) =>
 		{
 			LocalPosition = val;
 		}, ID + "_nug", LocalPosition.normalized * distance, duration, easingType);
```

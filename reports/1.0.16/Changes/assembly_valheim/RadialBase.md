# `Valheim.UI/RadialBase.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+29/-11` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/RadialBase.cs
+++ b/Valheim.UI/RadialBase.cs
@@ -271,14 +271,14 @@
 	{
 		get
 		{
-			return base.gameObject.activeSelf;
+			return gameObject.activeSelf;
 		}
 		private set
 		{
 			m_isClosing = false;
 			m_elementInfo.Clear();
 			m_cursor.gameObject.SetActive(value: false);
-			base.gameObject.SetActive(value);
+			gameObject.SetActive(value);
 			GameCamera.instance?.UpdateMouseCapture();
 		}
 	}
@@ -492,7 +492,18 @@
 		m_currentLayer = ((StartItemIndex > 0) ? Mathf.FloorToInt((float)StartItemIndex / (float)MaxElementsPerLayer) : 0);
 		m_previousClosestPoint = (m_closestPoint = ((StartItemIndex > 0) ? ((int)UIMath.Mod(StartItemIndex, MaxElementsPerLayer)) : ((!(m_previousInput != Vector2.zero)) ? ((int)UIMath.Mod(UIMath.AngleToRadialPoint(m_inputAngle, m_segmentSize) - StartOffset, MaxElementsPerLayer)) : 0)));
 		UpdateSelectionIndex();
-		m_previousCursorTarget = (m_cursorTarget = ((m_index != -1) ? UIMath.Mod((float)(m_index + StartOffset) * m_segmentSize, 360f) : ((StartItemIndex > 0) ? (UIMath.Mod(StartItemIndex, MaxElementsPerLayer) * m_segmentSize) : ((float)m_closestPoint * m_segmentSize))));
+		ref float previousCursorTarget = ref m_previousCursorTarget;
+		ref float cursorTarget = ref m_cursorTarget;
+		float num;
+		if (m_index != -1)
+		{
+			num = UIMath.Mod((float)(m_index + StartOffset) * m_segmentSize, 360f);
+		}
+		else
+		{
+			num = ((StartItemIndex > 0) ? (UIMath.Mod(StartItemIndex, MaxElementsPerLayer) * m_segmentSize) : ((float)m_closestPoint * m_segmentSize));
+		}
+		previousCursorTarget = (cursorTarget = num);
 		if (m_nrOfLayers > 0 && m_index != -1)
 		{
 			SetFadeAnchor((float)m_index * m_segmentSize, instant: true);
@@ -702,7 +713,14 @@
 			{
 				if (selected is ThrowElement)
 				{
-					lastUsed = ((!(LastUsed is ItemElement itemElement)) ? LastUsed : ((!m_localPlayerRef.GetInventory().ContainsItem(itemElement.m_data)) ? null : LastUsed));
+					if (LastUsed is ItemElement itemElement)
+					{
+						lastUsed = ((!m_localPlayerRef.GetInventory().ContainsItem(itemElement.m_data)) ? null : LastUsed);
+					}
+					else
+					{
+						lastUsed = LastUsed;
+					}
 				}
 				else if (!(selected is ItemElement itemElement2))
 				{
@@ -897,7 +915,7 @@
 		if ((bool)oldSelected)
 		{
 			oldSelected.Selected = false;
-			m_highlighter.SetParent(base.transform);
+			m_highlighter.SetParent(transform);
 			if (oldSelected is GroupElement groupElement)
 			{
 				groupElement.ChangeToDeselectColor();
@@ -1070,7 +1088,7 @@
 			float scale = GetScale(e);
 			if (!Mathf.Approximately(e.Scale, scale))
 			{
-				m_animationManager.StartUniqueTween(() => e.Scale, delegate(float val)
+				m_animationManager.StartUniqueTween(() => e.Scale, (float val) =>
 				{
 					e.Scale = val;
 				}, e.ID + "_scale", scale, m_reFade ? (RadialData.SO.ElementFadeDuration * RadialData.SO.ReFadeMultiplier) : RadialData.SO.ElementFadeDuration, RadialData.SO.ElementScaleEasingType);
@@ -1097,7 +1115,7 @@
 			}
 			else
 			{
-				m_animationManager.StartUniqueTween(() => e.Alpha, delegate(float val)
+				m_animationManager.StartUniqueTween(() => e.Alpha, (float val) =>
 				{
 					e.Alpha = val;
 				}, e.ID, alpha, m_reFade ? (RadialData.SO.ElementFadeDuration * RadialData.SO.ReFadeMultiplier) : RadialData.SO.ElementFadeDuration, RadialData.SO.ElementFadeEasingType);
@@ -1112,17 +1130,17 @@
 			}
 			else if (e == m_selected)
 			{
-				m_animationManager.StartUniqueTween(() => e.Scale, delegate(float val)
+				m_animationManager.StartUniqueTween(() => e.Scale, (float val) =>
 				{
 					e.Scale = val;
-				}, e.ID + "_scale", scale, m_reFade ? (RadialData.SO.ElementFadeDuration * RadialData.SO.ReFadeMultiplier) : RadialData.SO.ElementFadeDuration, RadialData.SO.ElementScaleEasingType, null, delegate
+				}, e.ID + "_scale", scale, m_reFade ? (RadialData.SO.ElementFadeDuration * RadialData.SO.ReFadeMultiplier) : RadialData.SO.ElementFadeDuration, RadialData.SO.ElementScaleEasingType, null, () =>
 				{
 					m_highlighter.localScale = Vector3.one;
 				});
 			}
 			else
 			{
-				m_animationManager.StartUniqueTween(() => e.Scale, delegate(float val)
+				m_animationManager.StartUniqueTween(() => e.Scale, (float val) =>
 				{
 					e.Scale = val;
 				}, e.ID + "_scale", scale, m_reFade ? (RadialData.SO.ElementFadeDuration * RadialData.SO.ReFadeMultiplier) : RadialData.SO.ElementFadeDuration, RadialData.SO.ElementScaleEasingType);
@@ -1199,7 +1217,7 @@
 			m_cursor.localRotation = UIMath.AngleToRotation(m_cursorTarget);
 			return;
 		}
-		m_animationManager.StartUniqueAngleTween(delegate(float val)
+		m_animationManager.StartUniqueAngleTween((float val) =>
 		{
 			m_cursor.localRotation = UIMath.AngleToRotation(val);
 		}, m_cursorID, m_previousCursorTarget, m_cursorTarget, m_reFade ? (RadialData.SO.CursorSpeed * RadialData.SO.ReFadeMultiplier) : RadialData.SO.CursorSpeed, RadialData.SO.CursorEasingType);
```

# `UITooltip.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_guiutils.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UITooltip.cs
+++ b/UITooltip.cs
@@ -109,7 +109,7 @@
 				m_tooltip.transform.position = m_fixedPosition;
 				return;
 			}
-			RectTransform obj = base.gameObject.transform as RectTransform;
+			RectTransform obj = gameObject.transform as RectTransform;
 			Vector3[] array = new Vector3[4];
 			obj.GetWorldCorners(array);
 			m_tooltip.transform.position = (array[1] + array[2]) / 2f;
@@ -152,7 +152,7 @@
 		{
 			if (m_tooltip == null)
 			{
-				m_tooltip = Object.Instantiate(m_tooltipPrefab, base.transform.GetComponentInParent<Canvas>().transform);
+				m_tooltip = Object.Instantiate(m_tooltipPrefab, transform.GetComponentInParent<Canvas>().transform);
 			}
 			UpdateTextElements();
 			Utils.ClampUIToScreen(m_tooltip.transform.GetChild(0).transform as RectTransform);
```

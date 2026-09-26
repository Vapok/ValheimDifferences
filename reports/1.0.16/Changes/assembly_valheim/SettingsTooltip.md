# `Valheim.SettingsGui/SettingsTooltip.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+11/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.SettingsGui/SettingsTooltip.cs
+++ b/Valheim.SettingsGui/SettingsTooltip.cs
@@ -77,21 +77,21 @@
 	{
 		if (m_tooltip == null)
 		{
-			Debug.LogWarning("No tooltip object set, removing tooltip component from " + base.gameObject.name);
+			Debug.LogWarning("No tooltip object set, removing tooltip component from " + gameObject.name);
 			Object.Destroy(this);
 			return;
 		}
 		m_selectable = (m_selectableOverride ? m_selectableOverride : GetComponent<Selectable>());
 		if (m_selectable == null)
 		{
-			Debug.LogWarning("No selectable found, removing tooltip component from " + base.gameObject.name);
+			Debug.LogWarning("No selectable found, removing tooltip component from " + gameObject.name);
 			Object.Destroy(this);
 			return;
 		}
 		m_parentCanvas = GetComponentInParent<Canvas>();
 		if (m_parentCanvas == null)
 		{
-			Debug.LogWarning("No canvas in parent found, removing tooltip component from " + base.gameObject.name);
+			Debug.LogWarning("No canvas in parent found, removing tooltip component from " + gameObject.name);
 			Object.Destroy(this);
 			return;
 		}
@@ -238,7 +238,14 @@
 		}
 		Vector3[] array = new Vector3[4];
 		Transform transform = m_selectable.transform.Find("Background");
-		component = ((m_positionOverride != null) ? m_positionOverride : ((!(transform != null)) ? m_selectable.gameObject.GetComponent<RectTransform>() : transform.GetComponent<RectTransform>()));
+		if (m_positionOverride != null)
+		{
+			component = m_positionOverride;
+		}
+		else
+		{
+			component = ((!(transform != null)) ? m_selectable.gameObject.GetComponent<RectTransform>() : transform.GetComponent<RectTransform>());
+		}
 		component.GetWorldCorners(array);
 		Vector2 vector = new Vector2(array[3].x - array[0].x, array[1].y - array[0].y);
 		Vector3[] array2 = new Vector3[4];
```

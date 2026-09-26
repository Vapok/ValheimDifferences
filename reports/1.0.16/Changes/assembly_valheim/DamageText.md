# `DamageText.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+20/-12` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/DamageText.cs
+++ b/DamageText.cs
@@ -98,21 +98,29 @@
 			WorldTextInstance worldTextInstance = new WorldTextInstance();
 			worldTextInstance.m_duration = m_textDuration;
 			worldTextInstance.m_worldPos = pos + Random.insideUnitSphere * 0.5f;
-			worldTextInstance.m_gui = Object.Instantiate(m_worldTextBase, base.transform);
+			worldTextInstance.m_gui = Object.Instantiate(m_worldTextBase, transform);
 			worldTextInstance.m_textField = worldTextInstance.m_gui.GetComponent<TMP_Text>();
 			m_worldTexts.Add(worldTextInstance);
 			text = Localization.instance.Localize(text);
-			Color color = ((mySelf && type <= TextType.Immune) ? ((!(text == "0")) ? new Color(1f, 0f, 0f, 1f) : new Color(0.5f, 0.5f, 0.5f, 1f)) : (type switch
-			{
-				TextType.Normal => new Color(1f, 1f, 1f, 1f), 
-				TextType.Resistant => new Color(0.6f, 0.6f, 0.6f, 1f), 
-				TextType.Weak => new Color(1f, 1f, 0f, 1f), 
-				TextType.Immune => new Color(0.6f, 0.6f, 0.6f, 1f), 
-				TextType.TooHard => new Color(0.8f, 0.7f, 0.7f, 1f), 
-				TextType.Bonus => new Color(1f, 0.63f, 0.24f, 1f), 
-				TextType.Heal => new Color(0.5f, 1f, 0.5f, 0.7f), 
-				_ => Color.white, 
-			}));
+			Color color;
+			if (mySelf && type <= TextType.Immune)
+			{
+				color = ((!(text == "0")) ? new Color(1f, 0f, 0f, 1f) : new Color(0.5f, 0.5f, 0.5f, 1f));
+			}
+			else
+			{
+				color = type switch
+				{
+					TextType.Normal => new Color(1f, 1f, 1f, 1f), 
+					TextType.Resistant => new Color(0.6f, 0.6f, 0.6f, 1f), 
+					TextType.Weak => new Color(1f, 1f, 0f, 1f), 
+					TextType.Immune => new Color(0.6f, 0.6f, 0.6f, 1f), 
+					TextType.TooHard => new Color(0.8f, 0.7f, 0.7f, 1f), 
+					TextType.Bonus => new Color(1f, 0.63f, 0.24f, 1f), 
+					TextType.Heal => new Color(0.5f, 1f, 0.5f, 0.7f), 
+					_ => Color.white, 
+				};
+			}
 			worldTextInstance.m_textField.color = color;
 			if (distance > m_smallFontDistance)
 			{
```

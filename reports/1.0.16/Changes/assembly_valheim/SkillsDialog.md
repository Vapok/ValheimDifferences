# `SkillsDialog.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+12/-12` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SkillsDialog.cs
+++ b/SkillsDialog.cs
@@ -122,25 +122,25 @@
 		for (int j = 0; j < skillList.Count; j++)
 		{
 			Skills.Skill skill = skillList[j];
-			GameObject obj = m_elements[j];
-			obj.SetActive(value: true);
-			RectTransform rectTransform = obj.transform as RectTransform;
+			GameObject gameObject = m_elements[j];
+			gameObject.SetActive(value: true);
+			RectTransform rectTransform = gameObject.transform as RectTransform;
 			rectTransform.anchoredPosition = new Vector2(0f, (float)(-j) * m_spacing);
-			obj.GetComponentInChildren<UITooltip>().Set("", skill.m_info.m_description, m_tooltipAnchor, new Vector2(0f, Math.Min(255f, rectTransform.localPosition.y + 10f)));
-			Utils.FindChild(obj.transform, "icon").GetComponent<Image>().sprite = skill.m_info.m_icon;
-			Utils.FindChild(obj.transform, "name").GetComponent<TMP_Text>().text = Localization.instance.Localize("$skill_" + skill.m_info.m_skill.ToString().ToLower());
+			gameObject.GetComponentInChildren<UITooltip>().Set("", skill.m_info.m_description, m_tooltipAnchor, new Vector2(0f, Math.Min(255f, rectTransform.localPosition.y + 10f)));
+			Utils.FindChild(gameObject.transform, "icon").GetComponent<Image>().sprite = skill.m_info.m_icon;
+			Utils.FindChild(gameObject.transform, "name").GetComponent<TMP_Text>().text = Localization.instance.Localize("$skill_" + skill.m_info.m_skill.ToString().ToLower());
 			float skillLevel = player.GetSkills().GetSkillLevel(skill.m_info.m_skill);
-			Utils.FindChild(obj.transform, "leveltext").GetComponent<TMP_Text>().text = ((int)skill.m_level).ToString();
-			TMP_Text component = Utils.FindChild(obj.transform, "bonustext").GetComponent<TMP_Text>();
+			Utils.FindChild(gameObject.transform, "leveltext").GetComponent<TMP_Text>().text = ((int)skill.m_level).ToString();
+			TMP_Text component = Utils.FindChild(gameObject.transform, "bonustext").GetComponent<TMP_Text>();
 			bool flag = skillLevel != Mathf.Floor(skill.m_level);
 			component.gameObject.SetActive(flag);
 			if (flag)
 			{
 				component.text = (skillLevel - skill.m_level).ToString("+0");
 			}
-			Utils.FindChild(obj.transform, "levelbar_total").GetComponent<GuiBar>().SetValue(skillLevel / 100f);
-			Utils.FindChild(obj.transform, "levelbar").GetComponent<GuiBar>().SetValue(skill.m_level / 100f);
-			Utils.FindChild(obj.transform, "currentlevel").GetComponent<GuiBar>().SetValue(skill.GetLevelPercentage());
+			Utils.FindChild(gameObject.transform, "levelbar_total").GetComponent<GuiBar>().SetValue(skillLevel / 100f);
+			Utils.FindChild(gameObject.transform, "levelbar").GetComponent<GuiBar>().SetValue(skill.m_level / 100f);
+			Utils.FindChild(gameObject.transform, "currentlevel").GetComponent<GuiBar>().SetValue(skill.GetLevelPercentage());
 		}
 		for (int k = skillList.Count; k < m_elements.Count; k++)
 		{
@@ -154,7 +154,7 @@
 
 	public void OnClose()
 	{
-		base.gameObject.SetActive(value: false);
+		gameObject.SetActive(value: false);
 	}
 
 	public void SkillClicked(GameObject selectedObject)
```

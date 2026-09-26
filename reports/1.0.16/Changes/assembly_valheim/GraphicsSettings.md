# `Valheim.SettingsGui/GraphicsSettings.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+31/-23` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.SettingsGui/GraphicsSettings.cs
+++ b/Valheim.SettingsGui/GraphicsSettings.cs
@@ -287,20 +287,20 @@
 			GraphicsSettingInt graphicsSettingInt = (GraphicsSettingInt)(1 << i);
 			if (Enum.IsDefined(typeof(GraphicsSettingInt), graphicsSettingInt) && graphicsSettingInt.IsShownToUser() && !graphicsSettingInt.IsPresentSetting() && graphicsSettingInt != GraphicsSettingInt.Target3DResolutionVertical && graphicsSettingInt != GraphicsSettingInt.UpscalingAlgorithm)
 			{
-				GameObject obj = UnityEngine.Object.Instantiate(m_qualitySliderPrefab, m_qualitySliderPrefab.transform.parent);
-				obj.transform.SetSiblingIndex(num++);
-				Slider component = obj.GetComponent<Slider>();
-				TMP_Text component2 = obj.transform.Find("Label").GetComponent<TMP_Text>();
-				Transform obj2 = obj.transform.Find("Info");
-				TMP_Text component3 = obj2.Find("Value").GetComponent<TMP_Text>();
-				Transform obj3 = obj2.Find("Warning");
-				Image component4 = obj3.GetComponent<Image>();
-				SettingsTooltip component5 = obj3.GetComponent<SettingsTooltip>();
+				GameObject gameObject = UnityEngine.Object.Instantiate(m_qualitySliderPrefab, m_qualitySliderPrefab.transform.parent);
+				gameObject.transform.SetSiblingIndex(num++);
+				Slider component = gameObject.GetComponent<Slider>();
+				TMP_Text component2 = gameObject.transform.Find("Label").GetComponent<TMP_Text>();
+				Transform transform = gameObject.transform.Find("Info");
+				TMP_Text component3 = transform.Find("Value").GetComponent<TMP_Text>();
+				Transform transform2 = transform.Find("Warning");
+				Image component4 = transform2.GetComponent<Image>();
+				SettingsTooltip component5 = transform2.GetComponent<SettingsTooltip>();
 				RangeIntInclusive range = graphicsSettingInt.GetRange();
 				component.minValue = range.m_minValue;
 				component.maxValue = range.m_maxValue;
 				component2.text = graphicsSettingInt.ToDisplayName();
-				obj.SetActive(value: true);
+				gameObject.SetActive(value: true);
 				QualitySliderData item = new QualitySliderData(graphicsSettingInt, component, component3, component4, component5);
 				m_qualitySliders.Add(item);
 				m_dynamicQualitySliders.Add(component);
@@ -312,11 +312,11 @@
 			GraphicsSettingBool graphicsSettingBool = (GraphicsSettingBool)(1 << j);
 			if (Enum.IsDefined(typeof(GraphicsSettingBool), graphicsSettingBool) && graphicsSettingBool.IsShownToUser() && !graphicsSettingBool.IsPresentSetting())
 			{
-				GameObject obj4 = UnityEngine.Object.Instantiate(m_qualityTogglePrefab, m_qualityTogglePrefab.transform.parent);
-				obj4.transform.SetSiblingIndex(num++);
-				GuiToggle componentInChildren = obj4.GetComponentInChildren<GuiToggle>();
+				GameObject gameObject2 = UnityEngine.Object.Instantiate(m_qualityTogglePrefab, m_qualityTogglePrefab.transform.parent);
+				gameObject2.transform.SetSiblingIndex(num++);
+				GuiToggle componentInChildren = gameObject2.GetComponentInChildren<GuiToggle>();
 				componentInChildren.transform.Find("Label").GetComponent<TMP_Text>().text = graphicsSettingBool.ToDisplayName();
-				obj4.SetActive(value: true);
+				gameObject2.SetActive(value: true);
 				QualityToggleData item2 = new QualityToggleData(graphicsSettingBool, componentInChildren);
 				m_qualityToggles.Add(item2);
 				m_dynamicQualityToggles.Add(componentInChildren);
@@ -337,11 +337,11 @@
 	private void SubscribeEvents()
 	{
 		GraphicsSettingsManager.GraphicsSettingsChanged += UpdateUI;
-		m_resolutionDropdown.onValueChanged.AddListener(delegate
+		m_resolutionDropdown.onValueChanged.AddListener((int _) =>
 		{
 			OnResolutionOptionModified();
 		});
-		m_fullscreenToggle.onValueChanged.AddListener(delegate
+		m_fullscreenToggle.onValueChanged.AddListener((bool _) =>
 		{
 			OnResolutionOptionModified();
 		});
@@ -350,7 +350,7 @@
 		{
 			QualityDropdownData ui = m_qualityDropdowns[num];
 			ui.m_dropdown.OnExpandedStateChange += OnDropdownExpanded;
-			ui.m_dropdown.onValueChanged.AddListener(delegate
+			ui.m_dropdown.onValueChanged.AddListener((int _) =>
 			{
 				OnDropdownValueUpdated(ui.m_setting);
 			});
@@ -358,7 +358,7 @@
 		for (int num2 = 0; num2 < m_qualitySliders.Count; num2++)
 		{
 			QualitySliderData ui2 = m_qualitySliders[num2];
-			ui2.m_slider.onValueChanged.AddListener(delegate
+			ui2.m_slider.onValueChanged.AddListener((float _) =>
 			{
 				OnSliderValueUpdated(ui2.m_setting);
 			});
@@ -366,7 +366,7 @@
 		for (int num3 = 0; num3 < m_qualityToggles.Count; num3++)
 		{
 			QualityToggleData ui3 = m_qualityToggles[num3];
-			ui3.m_toggle.onValueChanged.AddListener(delegate
+			ui3.m_toggle.onValueChanged.AddListener((bool _) =>
 			{
 				OnToggleValueUpdated(ui3.m_setting);
 			});
@@ -420,7 +420,7 @@
 		SaveRevertableResolutionSetting();
 		ApplyResolution(m_resolutionOptions[m_resolutionDropdown.value]);
 		m_resolutionSwitchDialog.SetActive(value: true);
-		if (m_resolutionSwitchDialog.transform.parent == base.transform)
+		if (m_resolutionSwitchDialog.transform.parent == transform)
 		{
 			m_resolutionSwitchDialog.transform.parent = m_resolutionSwitchDialog.transform.parent.parent;
 		}
@@ -582,7 +582,7 @@
 		{
 			list.Add(target3DResolutionVertical);
 		}
-		list.Sort(delegate(int a, int b)
+		list.Sort((int a, int b) =>
 		{
 			if (a == 0)
 			{
@@ -690,7 +690,15 @@
 			}
 		}
 		Selectable selectable = m_graphicPresetLeft;
-		Selectable target = ((list.Count > 0) ? list[0] : ((list2.Count <= 0) ? backButton : list2[0]));
+		Selectable target;
+		if (list.Count > 0)
+		{
+			target = list[0];
+		}
+		else
+		{
+			target = ((list2.Count <= 0) ? backButton : list2[0]);
+		}
 		GuiUtils.SetNavigationDown(m_graphicPresetLeft, target);
 		GuiUtils.SetNavigationDown(m_graphicPresetRight, target);
 		target = ((list2.Count <= 0) ? backButton : list2[0]);
@@ -1018,7 +1026,7 @@
 		{
 			m_resolutions.Add(m_oldResolution);
 		}
-		m_resolutions.Sort(delegate(Resolution a, Resolution b)
+		m_resolutions.Sort((Resolution a, Resolution b) =>
 		{
 			if (a.width != b.width)
 			{
```

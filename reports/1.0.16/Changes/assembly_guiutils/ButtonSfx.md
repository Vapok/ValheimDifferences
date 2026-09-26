# `ButtonSfx.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_guiutils.dll`
* **Status**: `🟡 MODIFIED` (`+32/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `private void Awake()`
- `private void OnDisable()`
- `private void OnEnable()`
- `private void Start()`

---

## 📝 Code Diff

```diff
--- a/ButtonSfx.cs
+++ b/ButtonSfx.cs
@@ -18,22 +18,44 @@
 
 	private Selectable m_selectable;
 
+	private Button m_button;
+
+	private Toggle m_toggle;
+
 	private static SfxTimer m_sfxTimer = new SfxTimer();
 
 	private static SfxTimer m_vibrationTimer = new SfxTimer();
 
 	private const int m_minDeltaFrames = 2;
 
-	private void Start()
+	private void Awake()
 	{
-		m_selectable = GetComponent<Selectable>();
-		if (m_selectable is Button button)
+		Selectable component = GetComponent<Selectable>();
+		m_button = component as Button;
+		m_toggle = component as Toggle;
+	}
+
+	private void OnEnable()
+	{
+		if (m_button != null)
 		{
-			button.onClick.AddListener(OnClick);
+			m_button.onClick.AddListener(OnClick);
 		}
-		else if (m_selectable is Toggle toggle)
+		else if (m_toggle != null)
 		{
-			toggle.onValueChanged.AddListener(OnChange);
+			m_toggle.onValueChanged.AddListener(OnChange);
+		}
+	}
+
+	private void OnDisable()
+	{
+		if (m_button != null)
+		{
+			m_button.onClick.RemoveListener(OnClick);
+		}
+		else if (m_toggle != null)
+		{
+			m_toggle.onValueChanged.RemoveListener(OnChange);
 		}
 	}
 
@@ -49,7 +71,10 @@
 
 	public void OnSelect(BaseEventData eventData)
 	{
-		PlaySfx(m_selectSfxPrefab, m_selectSfxPrefabVibrationOnly);
+		if (!ZInput.IsTouchActive())
+		{
+			PlaySfx(m_selectSfxPrefab, m_selectSfxPrefabVibrationOnly);
+		}
 	}
 
 	public void OnPointerEnter(PointerEventData eventData)
```

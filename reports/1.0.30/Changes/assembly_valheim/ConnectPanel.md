# `ConnectPanel.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+87/-23` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## ⚠️ Modified Fields (Type Signature Changes)

- `public/static m_frameTime`: `TMP_Text` ➔ `float`

---

## 🔍 Identified Changes & Methods

- `IsVisible() [Method Body Modified]`
- `Start() [Method Body Modified]`
- `Update() [Method Body Modified]`
- `UpdateConnectPanelGUI() [Method Body Modified]`
- `UpdateFps() [Method Body Modified]`
- `UpdatePerformancePanelGUI() [Method Body Modified]`
- `m_frameTime [Field Type: TMP_Text ➔ float]`
- `m_root [Field Removed, was Transform]`
- `private void UpdateConnectPanelGUI()`
- `private void UpdatePerformancePanelGUI()`

---

## 📝 Code Diff

```diff
--- a/ConnectPanel.cs
+++ b/ConnectPanel.cs
@@ -9,7 +9,8 @@
 {
 	private static ConnectPanel m_instance;
 
-	public Transform m_root;
+	[Header("Connect")]
+	public Transform m_connectRoot;
 
 	public TMP_Text m_serverField;
 
@@ -67,7 +68,7 @@
 
 	public TMP_Text m_fps;
 
-	public TMP_Text m_frameTime;
+	public TMP_Text m_frameTimeTextC;
 
 	public TMP_Text m_ping;
 
@@ -79,16 +80,39 @@
 
 	public TMP_Text m_serverOptions;
 
+	[Header("Performance")]
+	public Transform m_performanceRoot;
+
+	public TMP_Text m_frameTimeTextP;
+
+	public TMP_Text m_mainThreadTimeText;
+
+	public TMP_Text m_mainThreadPresentWaitTimeText;
+
+	public TMP_Text m_renderThreadTimeText;
+
+	public TMP_Text m_gpuTimeText;
+
 	private int m_frameSamples;
 
 	private float m_frameTimer;
 
+	private float m_frameTime;
+
+	private float m_mainThreadTime;
+
+	private float m_mainThreadPresentWaitTime;
+
+	private float m_renderThreadTime;
+
+	private float m_gpuTime;
+
 	public static ConnectPanel instance => m_instance;
 
 	private void Start()
 	{
 		m_instance = this;
-		m_root.gameObject.SetActive(value: false);
+		m_connectRoot.gameObject.SetActive(value: false);
 		m_playerListBaseSize = m_playerList.rect.height;
 	}
 
@@ -96,7 +120,7 @@
 	{
 		if ((bool)m_instance)
 		{
-			return m_instance.m_root.gameObject.activeSelf;
+			return m_instance.m_connectRoot.gameObject.activeSelf;
 		}
 		return false;
 	}
@@ -105,12 +129,36 @@
 	{
 		if ((ZInput.GetKeyDown(KeyCode.F2) || (ZInput.GetButton("JoyLTrigger") && ZInput.GetButton("JoyLBumper") && ZInput.GetButtonDown("JoyChat"))) && DemoMode.Disabled)
 		{
-			m_root.gameObject.SetActive(!m_root.gameObject.activeSelf);
-		}
-		if (!m_root.gameObject.activeInHierarchy)
-		{
-			return;
-		}
+			bool activeSelf = m_connectRoot.gameObject.activeSelf;
+			bool activeSelf2 = m_performanceRoot.gameObject.activeSelf;
+			m_connectRoot.gameObject.SetActive(!activeSelf && !activeSelf2);
+			m_performanceRoot.gameObject.SetActive(activeSelf && FrameTimingManager.IsFeatureEnabled());
+		}
+		if (m_connectRoot.gameObject.activeInHierarchy || m_performanceRoot.gameObject.activeSelf)
+		{
+			UpdateFps();
+			if (m_connectRoot.gameObject.activeInHierarchy)
+			{
+				UpdateConnectPanelGUI();
+			}
+			else if (m_performanceRoot.gameObject.activeSelf)
+			{
+				UpdatePerformancePanelGUI();
+			}
+		}
+	}
+
+	private void UpdatePerformancePanelGUI()
+	{
+		m_frameTimeTextP.text = (m_frameTime * 1000f).ToString("0.0") + "ms";
+		m_mainThreadTimeText.text = (m_mainThreadTime * 1000f).ToString("0.0") + "ms";
+		m_mainThreadPresentWaitTimeText.text = (m_mainThreadPresentWaitTime * 1000f).ToString("0.0") + "ms";
+		m_renderThreadTimeText.text = (m_renderThreadTime * 1000f).ToString("0.0") + "ms";
+		m_gpuTimeText.text = (m_gpuTime * 1000f).ToString("0.0") + "ms";
+	}
+
+	private void UpdateConnectPanelGUI()
+	{
 		if (!ZNet.instance.IsServer() && ZNet.GetConnectionStatus() == ZNet.ConnectionStatus.Connected)
 		{
 			m_serverField.gameObject.SetActive(value: true);
@@ -121,7 +169,14 @@
 			m_serverField.gameObject.SetActive(value: false);
 		}
 		m_worldField.text = ZNet.instance.GetWorldName();
-		UpdateFps();
+		if (m_frameTimer > 1f)
+		{
+			float num = m_frameTimer / (float)m_frameSamples;
+			m_fps.text = (1f / num).ToString("0.0");
+			m_frameTimeTextC.text = "( " + (num * 1000f).ToString("0.0") + "ms )";
+			m_frameSamples = 0;
+			m_frameTimer = 0f;
+		}
 		m_serverOptions.text = Localization.instance.Localize(Game.m_serverOptionsSummary);
 		m_myPort.gameObject.SetActive(ZNet.instance.IsServer());
 		m_myPort.text = ZNet.instance.GetHostPort().ToString();
@@ -153,7 +208,7 @@
 		}
 		m_connections.text = text;
 		List<ZNet.PlayerInfo> playerList = ZNet.instance.GetPlayerList();
-		float num = 16f;
+		float num2 = 16f;
 		if (playerList.Count != m_playerListElements.Count)
 		{
 			foreach (GameObject playerListElement in m_playerListElements)
@@ -164,10 +219,10 @@
 			for (int i = 0; i < playerList.Count; i++)
 			{
 				GameObject gameObject = Object.Instantiate(m_playerElement, m_playerList);
-				(gameObject.transform as RectTransform).anchoredPosition = new Vector2(0f, (float)i * (0f - num));
+				(gameObject.transform as RectTransform).anchoredPosition = new Vector2(0f, (float)i * (0f - num2));
 				m_playerListElements.Add(gameObject);
 			}
-			float b = (float)playerList.Count * num;
+			float b = (float)playerList.Count * num2;
 			b = Mathf.Max(m_playerListBaseSize, b);
 			m_playerList.SetSizeWithCurrentAnchors(RectTransform.Axis.Vertical, b);
 			m_playerListScroll.value = 1f;
@@ -187,15 +242,24 @@
 
 	private void UpdateFps()
 	{
-		m_frameTimer += Time.deltaTime;
-		m_frameSamples++;
-		if (m_frameTimer > 1f)
-		{
-			float num = m_frameTimer / (float)m_frameSamples;
-			m_fps.text = (1f / num).ToString("0.0");
-			m_frameTime.text = "( " + (num * 1000f).ToString("00.0") + "ms )";
-			m_frameSamples = 0;
-			m_frameTimer = 0f;
+		if (FrameTimingManager.IsFeatureEnabled())
+		{
+			FrameTiming[] array = new FrameTiming[1];
+			if (FrameTimingManager.GetLatestTimings((uint)array.Length, array) != 0)
+			{
+				m_frameTime = (float)array[0].cpuFrameTime / 1000f;
+				m_mainThreadTime = (float)array[0].cpuMainThreadFrameTime / 1000f;
+				m_mainThreadPresentWaitTime = (float)array[0].cpuMainThreadPresentWaitTime / 1000f;
+				m_renderThreadTime = (float)array[0].cpuRenderThreadFrameTime / 1000f;
+				m_gpuTime = (float)array[0].gpuFrameTime / 1000f;
+				m_frameTimer += m_frameTime;
+				m_frameSamples++;
+			}
+		}
+		else
+		{
+			m_frameTimer += Time.deltaTime;
+			m_frameSamples++;
 		}
 	}
 
```

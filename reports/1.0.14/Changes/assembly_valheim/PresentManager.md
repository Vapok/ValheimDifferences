# `PresentManager.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `public void RequestTargetFrameRate(int targetFrameRate, int targetRefreshRate)`
- `public void RequestTargetFrameRate(int value)`

---

## 📝 Code Diff

```diff
--- a/PresentManager.cs
+++ b/PresentManager.cs
@@ -25,6 +25,8 @@
 
 	private int m_requestedTargetFrameRate = -1;
 
+	private int m_requestedRefreshRate = -1;
+
 	private int m_targetFrameRate = -1;
 
 	private bool m_setVSyncEnabled;
@@ -67,9 +69,10 @@
 
 	public event Action ResolutionChanged;
 
-	public void RequestTargetFrameRate(int value)
-	{
-		m_requestedTargetFrameRate = ((value < 30 || value > 360) ? (-1) : value);
+	public void RequestTargetFrameRate(int targetFrameRate, int targetRefreshRate)
+	{
+		m_requestedTargetFrameRate = ((targetFrameRate < 30 || targetFrameRate > 360) ? (-1) : targetFrameRate);
+		m_requestedRefreshRate = ((targetRefreshRate < 30 || targetRefreshRate > 360) ? (-1) : targetRefreshRate);
 		UpdatePresentSettings();
 	}
 
@@ -273,7 +276,7 @@
 	{
 		if (!m_isComputer && !m_isXbox)
 		{
-			PresentRefreshRate presentRefreshRate = (((m_requestedTargetFrameRate <= 0 || !FrameRateIsSubmultipleOfRefreshRate((uint)m_requestedTargetFrameRate, s_hz59_94, 0.002f)) && IsSupportedRefreshRate(s_hz119_88)) ? s_hz119_88 : s_hz59_94);
+			PresentRefreshRate presentRefreshRate = (((m_requestedRefreshRate <= 0 || !FrameRateIsSubmultipleOfRefreshRate((uint)m_requestedRefreshRate, s_hz59_94, 0.002f)) && IsSupportedRefreshRate(s_hz119_88)) ? s_hz119_88 : s_hz59_94);
 			if (!m_currentDisplayRefreshRate.Equals(presentRefreshRate))
 			{
 				m_currentDisplayRefreshRate = presentRefreshRate;
```

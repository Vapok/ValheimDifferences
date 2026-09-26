# `PresentManager.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+11/-11` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/PresentManager.cs
+++ b/PresentManager.cs
@@ -94,7 +94,7 @@
 				return true;
 			}
 		}
-		lowestRefreshRate = default(PresentRefreshRate);
+		lowestRefreshRate = default;
 		return false;
 	}
 
@@ -184,7 +184,7 @@
 
 	private void UpdatePresentSettingsForXbox()
 	{
-		bool num = UpdateTargetFrameRate();
+		bool flag = UpdateTargetFrameRate();
 		int limitedFrameRate = GetLimitedFrameRate(m_targetFrameRate);
 		if (m_actualFrameRateLimit != limitedFrameRate)
 		{
@@ -199,7 +199,7 @@
 			Resolution currentResolution = Screen.currentResolution;
 			Screen.SetResolution(currentResolution.width, currentResolution.height, Screen.fullScreenMode, preferredRefreshRate);
 		}
-		if (num)
+		if (flag)
 		{
 			TargetFrameRateChanged?.Invoke();
 		}
@@ -227,7 +227,7 @@
 			m_framesForVulkanCrashWorkaround--;
 			return;
 		}
-		bool num = UpdateTargetFrameRate();
+		bool flag = UpdateTargetFrameRate();
 		int limitedFrameRate = GetLimitedFrameRate(m_targetFrameRate);
 		if (m_setVSyncEnabled)
 		{
@@ -236,12 +236,12 @@
 				m_actualFrameRateLimit = -1;
 				Application.targetFrameRate = -1;
 			}
-			int num2 = Mathf.RoundToInt((float)Screen.currentResolution.refreshRateRatio.value);
-			int num3 = Mathf.Max(1, num2 / limitedFrameRate);
-			if (m_actualVSyncCount != num3)
-			{
-				m_actualVSyncCount = num3;
-				QualitySettings.vSyncCount = num3;
+			int num = Mathf.RoundToInt((float)Screen.currentResolution.refreshRateRatio.value);
+			int num2 = Mathf.Max(1, num / limitedFrameRate);
+			if (m_actualVSyncCount != num2)
+			{
+				m_actualVSyncCount = num2;
+				QualitySettings.vSyncCount = num2;
 			}
 		}
 		else
@@ -257,7 +257,7 @@
 				QualitySettings.vSyncCount = 0;
 			}
 		}
-		if (num)
+		if (flag)
 		{
 			TargetFrameRateChanged?.Invoke();
 		}
```

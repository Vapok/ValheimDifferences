# `StartupMessages.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/StartupMessages.cs
+++ b/StartupMessages.cs
@@ -52,7 +52,7 @@
 		if (GetGPUVendor() == GPUVendor.AMD && SystemInfo.operatingSystemFamily == OperatingSystemFamily.Windows && SystemInfo.graphicsDeviceType == GraphicsDeviceType.Vulkan)
 		{
 			m_shownMessages++;
-			UnifiedPopup.Push(new WarningPopup("$menu_vulkancrashwarning_header", "$menu_vulkancrashwarning_text", delegate
+			UnifiedPopup.Push(new WarningPopup("$menu_vulkancrashwarning_header", "$menu_vulkancrashwarning_text", () =>
 			{
 				UnifiedPopup.Pop();
 				m_shownMessages--;
```

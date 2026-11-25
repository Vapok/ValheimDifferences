# `GraphicsSettingsManager.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `GetLightLimit() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/GraphicsSettingsManager.cs
+++ b/GraphicsSettingsManager.cs
@@ -602,6 +602,7 @@
 	{
 		return level switch
 		{
+			-1 => 0, 
 			0 => 2, 
 			1 => 4, 
 			_ => 8, 
```

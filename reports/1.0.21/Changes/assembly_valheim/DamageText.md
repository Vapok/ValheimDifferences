# `DamageText.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `UpdateWorldTexts() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/DamageText.cs
+++ b/DamageText.cs
@@ -63,6 +63,10 @@
 	{
 		WorldTextInstance worldTextInstance = null;
 		Camera mainCamera = Utils.GetMainCamera();
+		if (mainCamera == null)
+		{
+			return;
+		}
 		foreach (WorldTextInstance worldText in m_worldTexts)
 		{
 			worldText.m_timer += dt;
```

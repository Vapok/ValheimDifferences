# `Chat.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `UpdateNpcTexts() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Chat.cs
+++ b/Chat.cs
@@ -599,6 +599,10 @@
 	{
 		NpcText npcText = null;
 		Camera mainCamera = Utils.GetMainCamera();
+		if (mainCamera == null)
+		{
+			return;
+		}
 		foreach (NpcText npcText2 in m_npcTexts)
 		{
 			if (!npcText2.m_go)
```

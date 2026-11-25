# `Console.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Awake() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Console.cs
+++ b/Console.cs
@@ -20,7 +20,7 @@
 		LoadQuickSelect();
 		base.Awake();
 		m_instance = this;
-		AddString("Valheim " + Version.GetVersionString() + " (network version " + 41u + ")");
+		AddString("Valheim " + Version.GetVersionString() + " (network version " + 42u + ")");
 		AddString("");
 		AddString("type \"help\" - for commands");
 		AddString("");
```

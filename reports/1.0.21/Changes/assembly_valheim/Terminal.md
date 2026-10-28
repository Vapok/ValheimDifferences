# `Terminal.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `InitTerminal() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Terminal.cs
+++ b/Terminal.cs
@@ -970,7 +970,7 @@
 			args.Context?.AddString("Reseting tutorials");
 			Player.ResetSeenTutorials();
 		});
-		new ConsoleCommand("timescale", "[target] [fadetime, default: 1, max: 3] sets timescale", (ConsoleEventArgs args) =>
+		new ConsoleCommand("timescale", "[target] [fadetime, default: 1, max: 5] sets timescale", (ConsoleEventArgs args) =>
 		{
 			if (args.TryParameterFloat(1, out var value))
 			{
```

# `TriggerPersistentEventOnDestroy.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/TriggerPersistentEventOnDestroy.cs
+++ b/TriggerPersistentEventOnDestroy.cs
@@ -41,7 +41,7 @@
 			MessageHud.instance.MessageAll(MessageHud.MessageType.Center, Localization.instance.Localize(_centralTextOnTriggered));
 			if (_stopEvent)
 			{
-				PersistentEventSystem.instance.StopEvent(_eventInternalName, base.transform.position);
+				PersistentEventSystem.instance.StopEvent(_eventInternalName, transform.position);
 			}
 			else
 			{
```

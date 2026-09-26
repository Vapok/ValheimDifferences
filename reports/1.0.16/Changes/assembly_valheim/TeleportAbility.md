# `TeleportAbility.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/TeleportAbility.cs
+++ b/TeleportAbility.cs
@@ -24,7 +24,7 @@
 				m_owner.transform.rotation = gameObject.transform.rotation;
 				if (m_message.Length > 0)
 				{
-					Player.MessageAllInRange(base.transform.position, 100f, MessageHud.MessageType.Center, m_message);
+					Player.MessageAllInRange(transform.position, 100f, MessageHud.MessageType.Center, m_message);
 				}
 			}
 		}
```

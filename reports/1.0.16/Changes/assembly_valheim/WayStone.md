# `WayStone.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/WayStone.cs
+++ b/WayStone.cs
@@ -40,7 +40,7 @@
 		{
 			character.Message(MessageHud.MessageType.Center, m_activateMessage);
 			m_activeObject.SetActive(value: true);
-			m_activeEffect.Create(base.gameObject.transform.position, base.gameObject.transform.rotation);
+			m_activeEffect.Create(gameObject.transform.position, gameObject.transform.rotation);
 		}
 		return true;
 	}
@@ -54,7 +54,7 @@
 	{
 		if (m_activeObject.activeSelf && Game.instance != null)
 		{
-			Vector3 forward = GetSpawnPoint() - base.transform.position;
+			Vector3 forward = GetSpawnPoint() - transform.position;
 			forward.y = 0f;
 			forward.Normalize();
 			m_activeObject.transform.rotation = Quaternion.LookRotation(forward);
```

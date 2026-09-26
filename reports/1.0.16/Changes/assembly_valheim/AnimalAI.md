# `AnimalAI.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/AnimalAI.cs
+++ b/AnimalAI.cs
@@ -41,7 +41,7 @@
 		m_updateTargetTimer -= dt;
 		if (m_updateTargetTimer <= 0f)
 		{
-			m_updateTargetTimer = (Character.IsCharacterInRange(base.transform.position, 32f) ? 2f : 10f);
+			m_updateTargetTimer = (Character.IsCharacterInRange(transform.position, 32f) ? 2f : 10f);
 			Character character = FindEnemy();
 			if ((bool)character)
 			{
@@ -54,9 +54,9 @@
 		}
 		if ((bool)m_target)
 		{
-			bool num = CanSenseTarget(m_target);
+			bool flag = CanSenseTarget(m_target);
 			SetTargetInfo(m_target.GetZDOID());
-			if (num)
+			if (flag)
 			{
 				SetAlerted(alert: true);
 			}
```

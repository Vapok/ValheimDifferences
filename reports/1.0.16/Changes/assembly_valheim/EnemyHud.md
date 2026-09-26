# `EnemyHud.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+21/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/EnemyHud.cs
+++ b/EnemyHud.cs
@@ -127,7 +127,19 @@
 	{
 		if (!m_huds.TryGetValue(c, out var value))
 		{
-			GameObject original = (isMount ? m_baseHudMount : (c.IsPlayer() ? m_baseHudPlayer : ((!c.IsBoss()) ? m_baseHud : m_baseHudBoss)));
+			GameObject original;
+			if (isMount)
+			{
+				original = m_baseHudMount;
+			}
+			else if (c.IsPlayer())
+			{
+				original = m_baseHudPlayer;
+			}
+			else
+			{
+				original = ((!c.IsBoss()) ? m_baseHud : m_baseHudBoss);
+			}
 			value = new HudData();
 			value.m_character = c;
 			value.m_ai = c.GetComponent<BaseAI>();
@@ -234,7 +246,14 @@
 			if (!value.m_character.IsBoss() && value.m_gui.activeSelf)
 			{
 				Vector3 zero = Vector3.zero;
-				zero = (value.m_character.IsPlayer() ? (value.m_character.GetHeadPoint() + Vector3.up * 0.3f) : ((!value.m_isMount) ? value.m_character.GetTopPoint() : (player.transform.position - player.transform.up * 0.5f)));
+				if (value.m_character.IsPlayer())
+				{
+					zero = value.m_character.GetHeadPoint() + Vector3.up * 0.3f;
+				}
+				else
+				{
+					zero = ((!value.m_isMount) ? value.m_character.GetTopPoint() : (player.transform.position - player.transform.up * 0.5f));
+				}
 				Vector3 position = mainCamera.WorldToScreenPointScaled(zero);
 				if (position.x < 0f || position.x > (float)Screen.width || position.y < 0f || position.y > (float)Screen.height || position.z > 0f)
 				{
```

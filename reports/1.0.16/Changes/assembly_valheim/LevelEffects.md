# `LevelEffects.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/LevelEffects.cs
+++ b/LevelEffects.cs
@@ -56,7 +56,7 @@
 			return;
 		}
 		LevelSetup levelSetup = m_levelSetups[level - 2];
-		base.transform.localScale = new Vector3(levelSetup.m_scale, levelSetup.m_scale, levelSetup.m_scale);
+		transform.localScale = new Vector3(levelSetup.m_scale, levelSetup.m_scale, levelSetup.m_scale);
 		if ((bool)m_mainRender && (bool)m_character)
 		{
 			string key = Utils.GetPrefabName(m_character.gameObject) + level;
```

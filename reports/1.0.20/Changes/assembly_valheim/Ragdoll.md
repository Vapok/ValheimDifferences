# `Ragdoll.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `SpawnLoot() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Ragdoll.cs
+++ b/Ragdoll.cs
@@ -118,7 +118,7 @@
 		m_nview.GetZDO().Set(ZDOVars.s_saturation, saturation);
 		m_nview.GetZDO().Set(ZDOVars.s_value, value);
 		m_nview.GetZDO().Set(ZDOVars.s_level, level);
-		m_nview.GetZDO().Set(ZDOVars.s_cheated, cheated);
+		m_nview.GetZDO().SetCheated(cheated);
 		if ((bool)m_mainModel)
 		{
 			m_mainModel.material.SetFloat("_Hue", hue);
@@ -160,7 +160,7 @@
 		{
 			return;
 		}
-		bool cheated = zDO.GetBool(ZDOVars.s_cheated);
+		bool cheated = zDO.IsCheated();
 		List<KeyValuePair<GameObject, int>> list = new List<KeyValuePair<GameObject, int>>();
 		for (int i = 0; i < num; i++)
 		{
```

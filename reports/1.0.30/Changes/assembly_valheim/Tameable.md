# `Tameable.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `UnsummonMaxInstances() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Tameable.cs
+++ b/Tameable.cs
@@ -677,7 +677,7 @@
 		List<BaseAI> list = new List<BaseAI>();
 		foreach (Character item in allCharacters)
 		{
-			if (!(item.m_name == m_character.m_name))
+			if (!(item.m_name == m_character.m_name) && !m_character.m_summonNameBlockers.Contains(item.m_name))
 			{
 				continue;
 			}
@@ -689,12 +689,12 @@
 				if (zDO != null)
 				{
 					text2 = zDO.GetString(ZDOVars.s_follow);
-					goto IL_00b7;
+					goto IL_00d6;
 				}
 			}
 			text2 = "";
-			goto IL_00b7;
-			IL_00b7:
+			goto IL_00d6;
+			IL_00d6:
 			if (text2 == text)
 			{
 				MonsterAI component3 = item.GetComponent<MonsterAI>();
@@ -705,6 +705,7 @@
 			}
 		}
 		list.Sort((BaseAI a, BaseAI b) => b.GetTimeSinceSpawned().CompareTo(a.GetTimeSinceSpawned()));
+		ZLog.DevLog(string.Format("Summon Name: {0}, Summons: {1} Max: {2}, Name Blockers:\n{3}\nAll characters:\n {4}", m_character.m_name, list.Count, maxInstances, string.Join(",\n", m_character.m_summonNameBlockers), string.Join(",\n", allCharacters)));
 		int num = list.Count - maxInstances;
 		for (int num2 = 0; num2 < num; num2++)
 		{
```

# `Humanoid.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Humanoid.cs
+++ b/Humanoid.cs
@@ -712,7 +712,7 @@
 					outofRangeWeapons.Add(item);
 					continue;
 				}
-				if (item.m_shared.m_aiPrioritizedIfAngleCheckValid && m_baseAI.IsLookingAt(targetCreature.transform.position, item.m_shared.m_aiAttackMaxAngle, item.m_shared.m_aiInvertAngleCheck))
+				if ((bool)targetCreature && item.m_shared.m_aiPrioritizedIfAngleCheckValid && m_baseAI.IsLookingAt(targetCreature.transform.position, item.m_shared.m_aiAttackMaxAngle, item.m_shared.m_aiInvertAngleCheck))
 				{
 					EquipItem(item);
 					return;
```

# `Smelter.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Spawn() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Smelter.cs
+++ b/Smelter.cs
@@ -551,7 +551,7 @@
 			m_produceEffects.Create(transform.position, transform.rotation);
 			ItemDrop component = UnityEngine.Object.Instantiate(itemConversion.m_to.gameObject, m_outputPoint.position, m_outputPoint.rotation).GetComponent<ItemDrop>();
 			component.m_itemData.m_stack = stack;
-			bool flag = m_nview.GetZDO().GetBool(ZDOVars.s_cheatedQueued) || m_nview.GetZDO().GetBool(ZDOVars.s_cheated);
+			bool flag = m_nview.GetZDO().GetBool(ZDOVars.s_cheatedQueued) || m_nview.GetZDO().IsCheated();
 			flag &= !PlayerProfile.s_bypassCheatChecks;
 			ItemDrop.OnCreateNew(component, flag);
 		}
```

# `Fermenter.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `DelayedTap() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Fermenter.cs
+++ b/Fermenter.cs
@@ -336,7 +336,7 @@
 			{
 				Vector3 position = m_outputPoint.position + Vector3.up * num;
 				ItemDrop item = UnityEngine.Object.Instantiate(itemConversion.m_to, position, Quaternion.identity);
-				bool cheated = (m_delayedTapItemCheated || m_nview.GetZDO().GetBool(ZDOVars.s_cheated)) && !PlayerProfile.s_bypassCheatChecks;
+				bool cheated = (m_delayedTapItemCheated || m_nview.GetZDO().IsCheated()) && !PlayerProfile.s_bypassCheatChecks;
 				ItemDrop.OnCreateNew(item, cheated);
 			}
 		}
```

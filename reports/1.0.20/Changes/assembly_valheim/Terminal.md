# `Terminal.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Terminal.cs
+++ b/Terminal.cs
@@ -1506,7 +1506,7 @@
 								}
 								component.LoadFields();
 							}
-							component.GetZDO().Set(ZDOVars.s_cheated, !PlayerProfile.s_bypassCheatChecks);
+							component.GetZDO().SetCheated(!PlayerProfile.s_bypassCheatChecks);
 						}
 						ItemDrop component2 = gameObject.GetComponent<ItemDrop>();
 						ItemDrop.OnCreateNew(gameObject, !PlayerProfile.s_bypassCheatChecks);
```

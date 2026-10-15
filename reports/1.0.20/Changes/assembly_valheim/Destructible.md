# `Destructible.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Destructible.cs
+++ b/Destructible.cs
@@ -198,7 +198,7 @@
 			flag = player.GetInventory().CheatedDamagingItemEquipped() && !PlayerProfile.s_bypassCheatChecks;
 			if (flag)
 			{
-				m_nview.GetZDO().Set(ZDOVars.s_cheated, value: true);
+				m_nview.GetZDO().SetCheated(isCheated: true);
 			}
 		}
 		if ((bool)m_spawnWhenDestroyed)
@@ -210,7 +210,7 @@
 				component.SetLocalScale(transform.localScale);
 				if (flag)
 				{
-					component.GetZDO().Set(ZDOVars.s_cheated, value: true);
+					component.GetZDO().SetCheated(isCheated: true);
 				}
 			}
 			gameObject.GetComponent<Gibber>()?.Setup(hitPoint, hitDir);
```

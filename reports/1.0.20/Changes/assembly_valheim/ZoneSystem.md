# `ZoneSystem.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZoneSystem.cs
+++ b/ZoneSystem.cs
@@ -2491,7 +2491,7 @@
 				}
 				if (cheated)
 				{
-					gameObject2.GetComponent<ZNetView>().GetZDO().Set(ZDOVars.s_cheated, value: true);
+					gameObject2.GetComponent<ZNetView>().GetZDO().SetCheated(isCheated: true);
 				}
 				if (mode == SpawnMode.Ghost)
 				{
```

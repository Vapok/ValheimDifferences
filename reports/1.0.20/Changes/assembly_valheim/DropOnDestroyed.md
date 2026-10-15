# `DropOnDestroyed.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `OnDestroyed() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/DropOnDestroyed.cs
+++ b/DropOnDestroyed.cs
@@ -34,7 +34,7 @@
 		{
 			position.y = groundHeight + 0.1f;
 		}
-		bool cheated = GetComponent<ZNetView>().GetZDO().GetBool(ZDOVars.s_cheated) && !PlayerProfile.s_bypassCheatChecks;
+		bool cheated = GetComponent<ZNetView>().GetZDO().IsCheated() && !PlayerProfile.s_bypassCheatChecks;
 		List<GameObject> dropList = m_dropWhenDestroyed.GetDropList();
 		for (int i = 0; i < dropList.Count; i++)
 		{
```

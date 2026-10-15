# `ZPlayFabMatchmaking.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `ListServers() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/ZPlayFabMatchmaking.cs
+++ b/ZPlayFabMatchmaking.cs
@@ -879,7 +879,7 @@
 		{
 			nameFilter = string.Empty;
 		}
-		text = ((nameFilter.Length != 0) ? (text + CreateNameSearchFilter(nameFilter)) : (text + string.Format(" and {0} eq {1}", "number_key13", 40u)));
+		text = ((nameFilter.Length != 0) ? (text + CreateNameSearchFilter(nameFilter)) : (text + string.Format(" and {0} eq {1}", "number_key13", 41u)));
 		bool flag = PlatformManager.DistributionPlatform.PrivilegeProvider.CheckPrivilege(Privilege.CrossPlatformMultiplayer).IsGranted();
 		List<string> list = new List<string>(2);
 		list.Add(CreateSearchFilter(text, flag));
```

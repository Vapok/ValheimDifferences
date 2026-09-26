# `UserManagement/PlayerListManagement.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UserManagement/PlayerListManagement.cs
+++ b/UserManagement/PlayerListManagement.cs
@@ -49,8 +49,8 @@
 		if (id.IsValid)
 		{
 			PlatformUserID value = id;
-			PlatformUserID? obj = PlatformManager.DistributionPlatform?.LocalUser.PlatformUserID;
-			return value != obj;
+			PlatformUserID? platformUserID = PlatformManager.DistributionPlatform?.LocalUser.PlatformUserID;
+			return value != platformUserID;
 		}
 		return false;
 	}
```

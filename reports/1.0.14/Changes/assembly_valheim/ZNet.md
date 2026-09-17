# `ZNet.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZNet.cs
+++ b/ZNet.cs
@@ -1340,11 +1340,10 @@
 		if (IsServer())
 		{
 			RPC_Save(null);
-		}
-		else
-		{
-			GetServerRPC()?.Invoke("Save");
-		}
+			return;
+		}
+		Game.instance.SavePlayerProfile(setLogoutPoint: true);
+		GetServerRPC()?.Invoke("Save");
 	}
 
 	private void RPC_Save(ZRpc rpc)
```

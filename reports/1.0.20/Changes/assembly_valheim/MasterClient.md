# `MasterClient.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MasterClient.cs
+++ b/MasterClient.cs
@@ -85,7 +85,7 @@
 		bool flag2 = (bool)ZNet.instance && !ZNet.instance.IsServer();
 		zPackage.Write(flag2 ? duration : 0f);
 		zPackage.Write(Version.CurrentVersion.ToString());
-		zPackage.Write(40u);
+		zPackage.Write(41u);
 		bool flag3 = (bool)ZNet.instance && ZNet.instance.IsServer();
 		zPackage.Write(flag3);
 		if (flag3)
```

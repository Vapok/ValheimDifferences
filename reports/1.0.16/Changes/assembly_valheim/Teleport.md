# `Teleport.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Teleport.cs
+++ b/Teleport.cs
@@ -58,7 +58,7 @@
 
 	private Vector3 GetTeleportPoint()
 	{
-		return base.transform.position + base.transform.forward - base.transform.up;
+		return transform.position + transform.forward - transform.up;
 	}
 
 	public bool UseItem(Humanoid user, ItemDrop.ItemData item)
```

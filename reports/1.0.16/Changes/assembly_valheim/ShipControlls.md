# `ShipControlls.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ShipControlls.cs
+++ b/ShipControlls.cs
@@ -70,7 +70,7 @@
 
 	public Vector3 GetPosition()
 	{
-		return base.transform.position;
+		return transform.position;
 	}
 
 	public void ApplyControlls(Vector3 moveDir, Vector3 lookDir, bool run, bool autoRun, bool block)
```

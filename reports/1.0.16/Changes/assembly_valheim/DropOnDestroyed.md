# `DropOnDestroyed.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/DropOnDestroyed.cs
+++ b/DropOnDestroyed.cs
@@ -28,8 +28,8 @@
 
 	private void OnDestroyed()
 	{
-		float groundHeight = ZoneSystem.instance.GetGroundHeight(base.transform.position);
-		Vector3 position = base.transform.position;
+		float groundHeight = ZoneSystem.instance.GetGroundHeight(transform.position);
+		Vector3 position = transform.position;
 		if (position.y < groundHeight)
 		{
 			position.y = groundHeight + 0.1f;
```

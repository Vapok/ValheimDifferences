# `SnapToGround.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SnapToGround.cs
+++ b/SnapToGround.cs
@@ -29,10 +29,10 @@
 	{
 		if (!(ZoneSystem.instance == null))
 		{
-			float groundHeight = ZoneSystem.instance.GetGroundHeight(base.transform.position);
-			Vector3 position = base.transform.position;
+			float groundHeight = ZoneSystem.instance.GetGroundHeight(transform.position);
+			Vector3 position = transform.position;
 			position.y = groundHeight + m_offset;
-			base.transform.position = position;
+			transform.position = position;
 			ZNetView component = GetComponent<ZNetView>();
 			if (component != null && component.IsOwner())
 			{
```

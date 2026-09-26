# `RoomConnection.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/RoomConnection.cs
+++ b/RoomConnection.cs
@@ -24,7 +24,7 @@
 		{
 			Gizmos.color = new Color(1f, 1f, 0f, 1f);
 		}
-		Gizmos.matrix = Matrix4x4.TRS(base.transform.position, base.transform.rotation, new Vector3(1f, 1f, 1f));
+		Gizmos.matrix = Matrix4x4.TRS(transform.position, transform.rotation, new Vector3(1f, 1f, 1f));
 		Gizmos.DrawCube(Vector3.zero, new Vector3(2f, 0.02f, 0.2f));
 		Gizmos.DrawCube(new Vector3(0f, 0f, 0.35f), new Vector3(0.2f, 0.02f, 0.5f));
 		Gizmos.matrix = Matrix4x4.identity;
@@ -32,6 +32,6 @@
 
 	public bool TestContact(RoomConnection other)
 	{
-		return Vector3.Distance(base.transform.position, other.transform.position) < 0.1f;
+		return Vector3.Distance(transform.position, other.transform.position) < 0.1f;
 	}
 }
```

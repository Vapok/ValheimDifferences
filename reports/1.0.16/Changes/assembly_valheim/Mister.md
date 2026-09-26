# `Mister.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Mister.cs
+++ b/Mister.cs
@@ -66,7 +66,7 @@
 
 	public bool IsCompletelyInsideOtherMister(float thickness)
 	{
-		Vector3 position = base.transform.position;
+		Vector3 position = transform.position;
 		foreach (Mister instance in m_instances)
 		{
 			if (!(instance == this) && Vector3.Distance(position, instance.transform.position) + m_radius + thickness < instance.m_radius && position.y + m_height < instance.transform.position.y + instance.m_height)
@@ -79,9 +79,9 @@
 
 	public bool Inside(Vector3 p, float radius)
 	{
-		if (Vector3.Distance(p, base.transform.position) < radius)
+		if (Vector3.Distance(p, transform.position) < radius)
 		{
-			return p.y - radius < base.transform.position.y + m_height;
+			return p.y - radius < transform.position.y + m_height;
 		}
 		return false;
 	}
```

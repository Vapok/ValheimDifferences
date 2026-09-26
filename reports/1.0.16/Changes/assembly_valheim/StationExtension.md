# `StationExtension.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/StationExtension.cs
+++ b/StationExtension.cs
@@ -92,7 +92,7 @@
 	{
 		foreach (StationExtension allExtension in m_allExtensions)
 		{
-			if (!(allExtension == this) && Vector3.Distance(allExtension.transform.position, base.transform.position) < radius)
+			if (!(allExtension == this) && Vector3.Distance(allExtension.transform.position, transform.position) < radius)
 			{
 				return true;
 			}
@@ -119,7 +119,7 @@
 
 	private void PokeEffect(float timeout = 1f)
 	{
-		CraftingStation craftingStation = FindClosestStationInRange(base.transform.position);
+		CraftingStation craftingStation = FindClosestStationInRange(transform.position);
 		if ((bool)craftingStation)
 		{
 			StartConnectionEffect(craftingStation, timeout);
@@ -158,7 +158,7 @@
 
 	private Vector3 GetConnectionPoint()
 	{
-		return base.transform.TransformPoint(m_connectionOffset);
+		return transform.TransformPoint(m_connectionOffset);
 	}
 
 	private void OnDrawGizmos()
```

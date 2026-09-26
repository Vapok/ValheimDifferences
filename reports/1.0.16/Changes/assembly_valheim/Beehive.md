# `Beehive.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Beehive.cs
+++ b/Beehive.cs
@@ -73,7 +73,7 @@
 
 	public string GetHoverText()
 	{
-		if (!PrivateArea.CheckAccess(base.transform.position, 0f, flash: false))
+		if (!PrivateArea.CheckAccess(transform.position, 0f, flash: false))
 		{
 			return Localization.instance.Localize(m_name + "\n$piece_noaccess");
 		}
@@ -96,7 +96,7 @@
 		{
 			return false;
 		}
-		if (!PrivateArea.CheckAccess(base.transform.position))
+		if (!PrivateArea.CheckAccess(transform.position))
 		{
 			return true;
 		}
@@ -222,7 +222,7 @@
 
 	private bool CheckBiome()
 	{
-		return (Heightmap.FindBiome(base.transform.position) & m_biome) != 0;
+		return (Heightmap.FindBiome(transform.position) & m_biome) != 0;
 	}
 
 	public float GetHoverOffset()
```

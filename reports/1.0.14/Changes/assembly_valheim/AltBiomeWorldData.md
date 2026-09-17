# `AltBiomeWorldData.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/AltBiomeWorldData.cs
+++ b/AltBiomeWorldData.cs
@@ -71,12 +71,8 @@
 
 	public static void VerifyBiomeData(World world)
 	{
-		TryLoadCache(world);
-		if (world.m_biomeData == null || Version.World.DeepNorth != world.m_worldVersion)
-		{
-			GenerateBiomePoints(world);
-			world.m_biomeData.SaveCache();
-		}
+		RemoveCache(world.m_name);
+		GenerateBiomePoints(world);
 		world.m_biomeData.GenerateSectors();
 	}
 
```

# `AltBiomeWorldData.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+41/-41` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/AltBiomeWorldData.cs
+++ b/AltBiomeWorldData.cs
@@ -383,72 +383,72 @@
 			return biome;
 		}
 		int num = 0;
-		if ((biome & Heightmap.Biome.Meadows) != Heightmap.Biome.None)
-		{
-			num++;
-		}
-		if ((biome & Heightmap.Biome.Swamp) != Heightmap.Biome.None)
-		{
-			num++;
-		}
-		if ((biome & Heightmap.Biome.Mountain) != Heightmap.Biome.None)
-		{
-			num++;
-		}
-		if ((biome & Heightmap.Biome.BlackForest) != Heightmap.Biome.None)
-		{
-			num++;
-		}
-		if ((biome & Heightmap.Biome.Plains) != Heightmap.Biome.None)
-		{
-			num++;
-		}
-		if ((biome & Heightmap.Biome.AshLands) != Heightmap.Biome.None)
-		{
-			num++;
-		}
-		if ((biome & Heightmap.Biome.DeepNorth) != Heightmap.Biome.None)
-		{
-			num++;
-		}
-		if ((biome & Heightmap.Biome.Ocean) != Heightmap.Biome.None)
-		{
-			num++;
-		}
-		if ((biome & Heightmap.Biome.Mistlands) != Heightmap.Biome.None)
+		if ((biome & Heightmap.Biome.Meadows) != 0)
+		{
+			num++;
+		}
+		if ((biome & Heightmap.Biome.Swamp) != 0)
+		{
+			num++;
+		}
+		if ((biome & Heightmap.Biome.Mountain) != 0)
+		{
+			num++;
+		}
+		if ((biome & Heightmap.Biome.BlackForest) != 0)
+		{
+			num++;
+		}
+		if ((biome & Heightmap.Biome.Plains) != 0)
+		{
+			num++;
+		}
+		if ((biome & Heightmap.Biome.AshLands) != 0)
+		{
+			num++;
+		}
+		if ((biome & Heightmap.Biome.DeepNorth) != 0)
+		{
+			num++;
+		}
+		if ((biome & Heightmap.Biome.Ocean) != 0)
+		{
+			num++;
+		}
+		if ((biome & Heightmap.Biome.Mistlands) != 0)
 		{
 			num++;
 		}
 		int num2 = UnityEngine.Random.Range(0, num - 1);
-		if ((biome & Heightmap.Biome.Meadows) != Heightmap.Biome.None && num2-- == 0)
+		if ((biome & Heightmap.Biome.Meadows) != 0 && num2-- == 0)
 		{
 			return Heightmap.Biome.Meadows;
 		}
-		if ((biome & Heightmap.Biome.Swamp) != Heightmap.Biome.None && num2-- == 0)
+		if ((biome & Heightmap.Biome.Swamp) != 0 && num2-- == 0)
 		{
 			return Heightmap.Biome.Swamp;
 		}
-		if ((biome & Heightmap.Biome.Mountain) != Heightmap.Biome.None && num2-- == 0)
+		if ((biome & Heightmap.Biome.Mountain) != 0 && num2-- == 0)
 		{
 			return Heightmap.Biome.Mountain;
 		}
-		if ((biome & Heightmap.Biome.BlackForest) != Heightmap.Biome.None && num2-- == 0)
+		if ((biome & Heightmap.Biome.BlackForest) != 0 && num2-- == 0)
 		{
 			return Heightmap.Biome.BlackForest;
 		}
-		if ((biome & Heightmap.Biome.Plains) != Heightmap.Biome.None && num2-- == 0)
+		if ((biome & Heightmap.Biome.Plains) != 0 && num2-- == 0)
 		{
 			return Heightmap.Biome.BlackForest;
 		}
-		if ((biome & Heightmap.Biome.AshLands) != Heightmap.Biome.None && num2-- == 0)
+		if ((biome & Heightmap.Biome.AshLands) != 0 && num2-- == 0)
 		{
 			return Heightmap.Biome.AshLands;
 		}
-		if ((biome & Heightmap.Biome.DeepNorth) != Heightmap.Biome.None && num2-- == 0)
+		if ((biome & Heightmap.Biome.DeepNorth) != 0 && num2-- == 0)
 		{
 			return Heightmap.Biome.DeepNorth;
 		}
-		if ((biome & Heightmap.Biome.Meadows) != Heightmap.Biome.None && num2-- == 0)
+		if ((biome & Heightmap.Biome.Meadows) != 0 && num2-- == 0)
 		{
 			return Heightmap.Biome.Ocean;
 		}
```

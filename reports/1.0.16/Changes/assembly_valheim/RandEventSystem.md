# `RandEventSystem.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/RandEventSystem.cs
+++ b/RandEventSystem.cs
@@ -465,7 +465,7 @@
 
 	private static bool RetrievePlayerEventData(Dictionary<string, string> playerData, Vector3 position, out PlayerEventData eventData)
 	{
-		eventData = default(PlayerEventData);
+		eventData = default;
 		if (!playerData.TryGetValue("possibleEvents", out var value))
 		{
 			return false;
@@ -490,7 +490,7 @@
 		{
 			return true;
 		}
-		if ((WorldGenerator.instance.GetBiome(point) & ev.m_biome) != Heightmap.Biome.None)
+		if ((WorldGenerator.instance.GetBiome(point) & ev.m_biome) != 0)
 		{
 			return true;
 		}
@@ -704,7 +704,7 @@
 		}
 		string value = reader.ReadString();
 		float time = reader.ReadSingle();
-		Vector3 pos = default(Vector3);
+		Vector3 pos = default;
 		pos.x = reader.ReadSingle();
 		pos.y = reader.ReadSingle();
 		pos.z = reader.ReadSingle();
```

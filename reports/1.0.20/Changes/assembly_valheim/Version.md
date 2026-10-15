# `Version.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+18/-14` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `IsPlayerVersionCompatible() [Method Body Modified]`
- `IsWorldVersionCompatible() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Version.cs
+++ b/Version.cs
@@ -25,7 +25,8 @@
 		Celebration = 43,
 		AbandonedDN = 44,
 		Chunked = 45,
-		DeepNorth = 46
+		DeepNorth = 46,
+		CheatCleanSlate = 47
 	}
 
 	public enum World
@@ -61,7 +62,8 @@
 		DeepNorthNoChunk = 38,
 		DeepNorthNoChunk2 = 39,
 		ChunkedSave = 40,
-		DeepNorth = 41
+		DeepNorth = 41,
+		CheatCleanSlate = 42
 	}
 
 	public enum BiomeData
@@ -80,7 +82,8 @@
 		Stable = PickedUp,
 		AbandonedDN = 107,
 		Smaller = 108,
-		ChunksNCheats = 109
+		ChunksNCheats = 109,
+		NewCheats = 110
 	}
 
 	public enum PlayerData
@@ -114,7 +117,8 @@
 		BogWitch = 29,
 		AbandonedDN = 31,
 		ChunkedSaves = 32,
-		ChunkedNorth = 33
+		ChunkedNorth = 33,
+		PostLaunch = 34
 	}
 
 	public enum Map
@@ -139,19 +143,19 @@
 		Original = 1
 	}
 
-	public const uint c_networkVersion = 40u;
+	public const uint c_networkVersion = 41u;
 
 	public const int c_WorldGenVersion = 2;
 
-	public const Player c_PlayerVersion = Player.DeepNorth;
-
-	public const World c_WorldVersion = World.DeepNorth;
+	public const Player c_PlayerVersion = Player.CheatCleanSlate;
+
+	public const World c_WorldVersion = World.CheatCleanSlate;
 
 	public const BiomeData c_biomeDataVersion = BiomeData.Data;
 
-	public const Item c_ItemDataVersion = Item.ChunksNCheats;
-
-	public const PlayerData c_PlayerDataVersion = PlayerData.ChunkedNorth;
+	public const Item c_ItemDataVersion = Item.NewCheats;
+
+	public const PlayerData c_PlayerDataVersion = PlayerData.PostLaunch;
 
 	public const Map c_MapVersion = Map.PinsAuthor;
 
@@ -165,7 +169,7 @@
 
 	public static readonly GameVersion FirstVersionWithModifiers = new GameVersion(0, 217, 8);
 
-	public static GameVersion CurrentVersion { get; } = new GameVersion(1, 0, 17);
+	public static GameVersion CurrentVersion { get; } = new GameVersion(1, 0, 20);
 
 	public static string GetVersionString(bool includeMercurialHash = false)
 	{
@@ -188,7 +192,7 @@
 
 	public static bool IsWorldVersionCompatible(World version)
 	{
-		if (version <= World.DeepNorth)
+		if (version <= World.CheatCleanSlate)
 		{
 			return version >= World.OldestForwardCompatible;
 		}
@@ -197,7 +201,7 @@
 
 	public static bool IsPlayerVersionCompatible(Player version)
 	{
-		if (version <= Player.DeepNorth)
+		if (version <= Player.CheatCleanSlate)
 		{
 			return version >= Player.OldestForwardCompatible;
 		}
```

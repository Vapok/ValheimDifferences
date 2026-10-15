# `Minimap.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Minimap.cs
+++ b/Minimap.cs
@@ -764,7 +764,7 @@
 
 	private bool TryLoadMinimapTextureData(int worldSeed)
 	{
-		if (string.IsNullOrEmpty(m_cachedMinimapMaskTexturePath) || !File.Exists(m_cachedMinimapMaskTexturePath) || !File.Exists(m_cachedMinimapBiomeTexturePath) || !File.Exists(m_cachedMinimapHeightTexturePath) || !File.Exists(m_cachedMinimapMetaPath) || Version.World.DeepNorth != ZNet.World.m_worldVersion)
+		if (string.IsNullOrEmpty(m_cachedMinimapMaskTexturePath) || !File.Exists(m_cachedMinimapMaskTexturePath) || !File.Exists(m_cachedMinimapBiomeTexturePath) || !File.Exists(m_cachedMinimapHeightTexturePath) || !File.Exists(m_cachedMinimapMetaPath) || Version.World.CheatCleanSlate != ZNet.World.m_worldVersion)
 		{
 			return false;
 		}
```

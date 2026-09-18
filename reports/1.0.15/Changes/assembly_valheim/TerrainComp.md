# `TerrainComp.cs` Diff (`1.0.14` $\rightarrow$ `1.0.15`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-9` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/TerrainComp.cs
+++ b/TerrainComp.cs
@@ -58,14 +58,12 @@
 		if ((bool)terrainComp)
 		{
 			ZLog.LogWarning("Found another terrain compiler in this area, removing it");
-			if (m_nview.IsValid() && !m_nview.HasOwner())
-			{
-				m_nview.ClaimOwnership();
-			}
-			if (m_nview.IsOwner())
-			{
-				ZNetScene.instance.Destroy(terrainComp.gameObject);
-			}
+			if (terrainComp.m_nview.IsValid() && !terrainComp.m_nview.HasOwner())
+			{
+				terrainComp.m_nview.ClaimOwnership();
+			}
+			ZNetScene.instance.Destroy(terrainComp.gameObject);
+			s_instances.Remove(terrainComp);
 		}
 		s_instances.Add(this);
 		m_nview.Register<ZPackage>("RPC_ApplyOperation", RPC_ApplyOperation);
@@ -680,7 +678,6 @@
 						terrainComp.m_modifiedPaint[num13] = true;
 						terrainComp.m_paintMask[num13] = color2;
 						bool paintOnly = settings.m_paintCleared && !settings.m_level && !settings.m_raise && !settings.m_smooth;
-						terrainComp.Save(paintOnly);
 						terrainComp.m_hmap.Poke(1, paintOnly);
 					}
 					return true;
```

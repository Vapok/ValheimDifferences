# `Hud.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Hud.cs
+++ b/Hud.cs
@@ -1284,7 +1284,7 @@
 		{
 			m_lastPieceCategory = category;
 			UpdatePieceBuildStatusAll(buildPieces, player);
-			m_selectItemCategoryEffect.Create(base.transform.position, Quaternion.identity);
+			m_selectItemCategoryEffect.Create(transform.position, Quaternion.identity);
 		}
 	}
 
@@ -1367,7 +1367,7 @@
 		if (selectedGrid.x != -1)
 		{
 			Player.m_localPlayer.SetSelectedPiece(selectedGrid);
-			m_selectItemEffect.Create(base.transform.position, Quaternion.identity);
+			m_selectItemEffect.Create(transform.position, Quaternion.identity);
 		}
 	}
 
```

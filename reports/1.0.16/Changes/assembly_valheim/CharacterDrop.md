# `CharacterDrop.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CharacterDrop.cs
+++ b/CharacterDrop.cs
@@ -62,7 +62,7 @@
 		if (m_dropsEnabled)
 		{
 			List<KeyValuePair<GameObject, int>> drops = GenerateDropList();
-			Vector3 centerPos = m_character.GetCenterPoint() + base.transform.TransformVector(m_spawnOffset);
+			Vector3 centerPos = m_character.GetCenterPoint() + transform.TransformVector(m_spawnOffset);
 			DropItems(drops, centerPos, 0.5f, m_cheated);
 		}
 	}
```

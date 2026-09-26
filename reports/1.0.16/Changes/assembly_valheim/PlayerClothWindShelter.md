# `PlayerClothWindShelter.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/PlayerClothWindShelter.cs
+++ b/PlayerClothWindShelter.cs
@@ -14,11 +14,11 @@
 		m_cloth = GetComponent<MagicaCloth>();
 		if ((object)m_cloth == null)
 		{
-			ZLog.LogError("PlayerClothWindShelter: MagicaCloth component not found on gameobject " + base.gameObject.name + " - check prefab authoring!");
+			ZLog.LogError("PlayerClothWindShelter: MagicaCloth component not found on gameobject " + gameObject.name + " - check prefab authoring!");
 			return;
 		}
 		m_baseWindInfluence = m_cloth.SerializeData.wind.influence;
-		base.enabled = false;
+		enabled = false;
 	}
 
 	public void SetPlayer(Player p)
@@ -26,7 +26,7 @@
 		if (!(m_player != null))
 		{
 			m_player = p;
-			base.enabled = true;
+			enabled = true;
 		}
 	}
 
```

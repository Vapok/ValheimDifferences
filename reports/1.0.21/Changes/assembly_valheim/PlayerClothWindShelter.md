# `PlayerClothWindShelter.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Awake() [Method Body Modified]`
- `SetPlayer() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/PlayerClothWindShelter.cs
+++ b/PlayerClothWindShelter.cs
@@ -14,11 +14,13 @@
 		m_cloth = GetComponent<MagicaCloth>();
 		if ((object)m_cloth == null)
 		{
-			ZLog.LogError("PlayerClothWindShelter: MagicaCloth component not found on gameobject " + gameObject.name + " - check prefab authoring!");
-			return;
+			ZLog.LogError("PlayerClothWindShelter: MagicaCloth component not found on gameobject [" + gameObject.name + "], root object [" + gameObject.transform.root.gameObject.name + "] - check prefab authoring!");
 		}
-		m_baseWindInfluence = m_cloth.SerializeData.wind.influence;
-		enabled = false;
+		else
+		{
+			m_baseWindInfluence = m_cloth.SerializeData.wind.influence;
+			enabled = false;
+		}
 	}
 
 	public void SetPlayer(Player p)
```

# `CookingStation.cs` Diff (`1.0.30` $\rightarrow$ `1.0.31`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `SpawnItem() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/CookingStation.cs
+++ b/CookingStation.cs
@@ -562,6 +562,10 @@
 				component.m_itemData.m_crafterName = Player.m_localPlayer.GetPlayerName();
 			}
 		}
+		else if (!m_recordCrafter)
+		{
+			Game.instance.GetPlayerProfile().IncrementStatItemCraft(component.m_itemData.m_shared.m_name);
+		}
 		gameObject.GetComponent<Rigidbody>().linearVelocity = vector2 * m_spawnForce;
 		m_pickEffector.Create(vector, Quaternion.identity);
 	}
```

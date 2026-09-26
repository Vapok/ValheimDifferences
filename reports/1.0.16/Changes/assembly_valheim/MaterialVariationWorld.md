# `MaterialVariationWorld.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MaterialVariationWorld.cs
+++ b/MaterialVariationWorld.cs
@@ -9,7 +9,7 @@
 
 	private void Update()
 	{
-		Location zoneLocation = Location.GetZoneLocation(base.transform.position);
+		Location zoneLocation = Location.GetZoneLocation(transform.position);
 		if (!zoneLocation)
 		{
 			return;
@@ -34,13 +34,13 @@
 				}
 			}
 		}
-		base.enabled = false;
+		enabled = false;
 		void change(MaterialVariationSettings mvs)
 		{
 			foreach (MeshRenderer mr in mrs)
 			{
 				mr.materials = mvs.m_materials;
-				Terminal.Log($"Replaced material on {base.gameObject.name} for dungeon {mvs.m_dungeonThemeCondition} or {mvs.m_biomeCondition}");
+				Terminal.Log($"Replaced material on {gameObject.name} for dungeon {mvs.m_dungeonThemeCondition} or {mvs.m_biomeCondition}");
 			}
 		}
 	}
```

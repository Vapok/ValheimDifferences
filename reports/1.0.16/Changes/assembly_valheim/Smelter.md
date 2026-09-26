# `Smelter.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Smelter.cs
+++ b/Smelter.cs
@@ -138,7 +138,7 @@
 			float num = ((m_nview.GetZDO() == null) ? 0f : m_nview.GetZDO().GetFloat(ZDOVars.s_fuel));
 			for (int i = 0; i < (int)num; i++)
 			{
-				Vector3 position = base.transform.position + Vector3.up + UnityEngine.Random.insideUnitSphere * 0.3f;
+				Vector3 position = transform.position + Vector3.up + UnityEngine.Random.insideUnitSphere * 0.3f;
 				Quaternion rotation = Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f);
 				ItemDrop.OnCreateNew(UnityEngine.Object.Instantiate(m_fuelItem.gameObject, position, rotation));
 			}
@@ -150,7 +150,7 @@
 			ItemConversion itemConversion = GetItemConversion(queuedOre);
 			if (itemConversion != null)
 			{
-				Vector3 position2 = base.transform.position + Vector3.up + UnityEngine.Random.insideUnitSphere * 0.3f;
+				Vector3 position2 = transform.position + Vector3.up + UnityEngine.Random.insideUnitSphere * 0.3f;
 				Quaternion rotation2 = Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f);
 				ItemDrop.OnCreateNew(UnityEngine.Object.Instantiate(itemConversion.m_from.gameObject, position2, rotation2));
 			}
@@ -284,7 +284,7 @@
 				return;
 			}
 			QueueOre(name, cheated);
-			m_oreAddedEffects.Create(base.transform.position, base.transform.rotation);
+			m_oreAddedEffects.Create(transform.position, transform.rotation);
 			ZLog.Log("Added ore " + name);
 		}
 	}
@@ -367,7 +367,7 @@
 		{
 			float fuel = GetFuel();
 			SetFuel(fuel + 1f);
-			m_fuelAddedEffects.Create(base.transform.position, base.transform.rotation, base.transform);
+			m_fuelAddedEffects.Create(transform.position, transform.rotation, transform);
 		}
 	}
 
@@ -548,7 +548,7 @@
 		ItemConversion itemConversion = GetItemConversion(ore);
 		if (itemConversion != null && itemConversion.m_to != null)
 		{
-			m_produceEffects.Create(base.transform.position, base.transform.rotation);
+			m_produceEffects.Create(transform.position, transform.rotation);
 			ItemDrop component = UnityEngine.Object.Instantiate(itemConversion.m_to.gameObject, m_outputPoint.position, m_outputPoint.rotation).GetComponent<ItemDrop>();
 			component.m_itemData.m_stack = stack;
 			bool flag = m_nview.GetZDO().GetBool(ZDOVars.s_cheatedQueued) || m_nview.GetZDO().GetBool(ZDOVars.s_cheated);
```

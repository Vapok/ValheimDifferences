# `LocationProxy.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/LocationProxy.cs
+++ b/LocationProxy.cs
@@ -62,12 +62,12 @@
 			}
 			return false;
 		}
-		m_instance = ZoneSystem.instance.SpawnProxyLocation(num, seed, base.transform.position, base.transform.rotation);
+		m_instance = ZoneSystem.instance.SpawnProxyLocation(num, seed, transform.position, transform.rotation);
 		if (m_instance == null)
 		{
 			return false;
 		}
-		m_instance.transform.SetParent(base.transform, worldPositionStays: true);
+		m_instance.transform.SetParent(transform, worldPositionStays: true);
 		m_nview.LoadFields();
 		m_locationNeedsSpawn = false;
 		if (m_zdoSetToBeLoadingInZone != null)
```

# `Vegvisir.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Vegvisir.cs
+++ b/Vegvisir.cs
@@ -51,7 +51,7 @@
 		}
 		foreach (VegvisrLocation location in m_locations)
 		{
-			Game.instance.DiscoverClosestLocation(location.m_locationName, base.transform.position, location.m_pinName, (int)location.m_pinType, location.m_showMap, location.m_discoverAll);
+			Game.instance.DiscoverClosestLocation(location.m_locationName, transform.position, location.m_pinName, (int)location.m_pinType, location.m_showMap, location.m_discoverAll);
 			Gogan.LogEvent("Game", "Vegvisir", location.m_locationName, 0L);
 		}
 		if (!string.IsNullOrEmpty(m_setsGlobalKey))
```

# `CookingStation.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CookingStation.cs
+++ b/CookingStation.cs
@@ -181,7 +181,7 @@
 		if (m_fuelItem != null)
 		{
 			float fuel = GetFuel();
-			bool cheated = m_nview.GetZDO().GetBool(ZDOVars.s_cheated) && !PlayerProfile.s_bypassCheatChecks;
+			bool cheated = m_nview.GetZDO().IsCheated() && !PlayerProfile.s_bypassCheatChecks;
 			for (int i = 0; i < (int)fuel; i++)
 			{
 				drop(m_fuelItem, cheated);
@@ -224,7 +224,7 @@
 			Vector3 position = transform.position + Vector3.up + UnityEngine.Random.insideUnitSphere * 0.3f;
 			Quaternion rotation = Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f);
 			GameObject go = UnityEngine.Object.Instantiate(item.gameObject, position, rotation);
-			flag |= m_nview.GetZDO().GetBool(ZDOVars.s_cheated);
+			flag |= m_nview.GetZDO().IsCheated();
 			ItemDrop.OnCreateNew(go, flag && !PlayerProfile.s_bypassCheatChecks);
 		}
 	}
```

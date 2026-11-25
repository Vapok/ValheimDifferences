# `Player.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `GetItemUpgradeChance() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Player.cs
+++ b/Player.cs
@@ -7591,7 +7591,7 @@
 	{
 		if (!m_itemUpgradeSeeds.TryGetValue(hash, out var value))
 		{
-			value = GetPlayerName().GetStableHashCode() + hash;
+			value = Game.instance.GetPlayerProfile().m_dateCreated.GetHashCode() + hash;
 		}
 		UnityEngine.Random.InitState(value);
 		if (Terminal.m_showTests && Terminal.m_testList.ContainsKey("upgrader"))
```

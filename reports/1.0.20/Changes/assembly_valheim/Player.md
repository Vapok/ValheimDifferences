# `Player.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+49/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `public float GetItemUpgradeChance(int hash)`

---

## 📝 Code Diff

```diff
--- a/Player.cs
+++ b/Player.cs
@@ -528,6 +528,8 @@
 	private Collider[] m_colliders = new Collider[100];
 
 	private RaycastHit[] m_raycastHits = new RaycastHit[100];
+
+	private Dictionary<int, int> m_itemUpgradeSeeds = new Dictionary<int, int>();
 
 	private int m_baseValue;
 
@@ -3144,7 +3146,7 @@
 		}
 		if (cheated)
 		{
-			gameObject.GetComponent<ZNetView>()?.GetZDO().Set(ZDOVars.s_cheated, value: true);
+			gameObject.GetComponent<ZNetView>()?.GetZDO().SetCheated(isCheated: true);
 		}
 		AddNoise(50f);
 		if (m_clusterStatCheck-- <= 0)
@@ -4676,7 +4678,7 @@
 
 	public void Save(ZPackage pkg)
 	{
-		pkg.Write(33);
+		pkg.Write(34);
 		pkg.Write(GetMaxHealth());
 		pkg.Write(GetHealth());
 		pkg.Write(GetMaxStamina());
@@ -4754,6 +4756,18 @@
 		else
 		{
 			pkg.Write(new byte[0]);
+		}
+		pkg.Write(CharacterDrop.s_pseudoCounter.Count);
+		foreach (KeyValuePair<int, int> item3 in CharacterDrop.s_pseudoCounter)
+		{
+			pkg.Write(item3.Key);
+			pkg.Write(item3.Value);
+		}
+		pkg.Write(m_itemUpgradeSeeds.Count);
+		foreach (KeyValuePair<int, int> itemUpgradeSeed in m_itemUpgradeSeeds)
+		{
+			pkg.Write(itemUpgradeSeed.Key);
+			pkg.Write(itemUpgradeSeed.Value);
 		}
 	}
 
@@ -4988,6 +5002,23 @@
 		{
 			byte[] data = pkg.ReadByteArray();
 			Hud.instance?.m_buildUi.LoadFromBinary(data);
+		}
+		if (playerData >= Version.PlayerData.PostLaunch)
+		{
+			int num20 = pkg.ReadInt();
+			for (int num21 = 0; num21 < num20; num21++)
+			{
+				int key4 = pkg.ReadInt();
+				int value4 = pkg.ReadInt();
+				CharacterDrop.s_pseudoCounter[key4] = value4;
+			}
+			num20 = pkg.ReadInt();
+			for (int num22 = 0; num22 < num20; num22++)
+			{
+				int key5 = pkg.ReadInt();
+				int value5 = pkg.ReadInt();
+				m_itemUpgradeSeeds[key5] = value5;
+			}
 		}
 		m_isLoading = false;
 		UpdateAvailablePiecesList();
@@ -7546,4 +7577,20 @@
 	{
 		return m_knownMaterial.Contains(name);
 	}
+
+	public float GetItemUpgradeChance(int hash)
+	{
+		if (!m_itemUpgradeSeeds.TryGetValue(hash, out var value))
+		{
+			value = GetPlayerName().GetStableHashCode() + hash;
+		}
+		UnityEngine.Random.InitState(value);
+		if (Terminal.m_showTests && Terminal.m_testList.ContainsKey("upgrader"))
+		{
+			ZLog.Log($"Upgrader seed: {value} for hash {hash}");
+		}
+		float value2 = UnityEngine.Random.value;
+		m_itemUpgradeSeeds[hash] = UnityEngine.Random.Range(0, 99999999);
+		return value2;
+	}
 }
```

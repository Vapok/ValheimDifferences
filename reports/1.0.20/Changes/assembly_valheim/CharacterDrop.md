# `CharacterDrop.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+32/-25` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CharacterDrop.cs
+++ b/CharacterDrop.cs
@@ -21,6 +21,8 @@
 
 		public bool m_levelMultiplier = true;
 
+		public bool m_levelMultiplierNotAmount;
+
 		public bool m_dontScale;
 	}
 
@@ -38,7 +40,7 @@
 
 	public bool m_cheated;
 
-	public static Dictionary<string, Tuple<float, int>> s_pseudoCounter = new Dictionary<string, Tuple<float, int>>();
+	public static Dictionary<int, int> s_pseudoCounter = new Dictionary<int, int>();
 
 	private static List<int> s_pseudoHistory = new List<int>();
 
@@ -88,72 +90,77 @@
 			bool flag2 = flag && Terminal.m_showTests && Terminal.m_testList.ContainsKey("pseudo");
 			if (flag2)
 			{
-				num4 = 500;
+				num4 = 1000;
 				s_pseudoHistory.Clear();
 			}
+			int num5 = drop.m_prefab.name.GetStableHashCode() + (int)(num2 * 1000f);
 			for (int i = 0; i < num4; i++)
 			{
 				bool flag3 = false;
 				if (flag)
 				{
-					int num5 = 0;
-					if (s_pseudoCounter.TryGetValue(drop.m_prefab.name, out var value) && value.Item1 == num2)
+					int num6 = 0;
+					if (s_pseudoCounter.TryGetValue(num5, out var value))
 					{
-						num5 = value.Item2 - 1;
+						num6 = value - 1;
 					}
 					else
 					{
-						num5 = UnityEngine.Random.Range(0, (int)(1f / num2 * 2f));
-						s_pseudoCounter[drop.m_prefab.name] = new Tuple<float, int>(num2, num5);
+						num6 = UnityEngine.Random.Range(0, (int)(1f / num2 * 2f));
+						s_pseudoCounter[num5] = num6;
 					}
-					if (num5 <= 0)
+					if (num6 <= 0)
 					{
 						flag3 = true;
-						int num6 = UnityEngine.Random.Range(0, (int)(1f / num2 * 2f + 1f));
-						s_pseudoCounter[drop.m_prefab.name] = new Tuple<float, int>(num2, num6);
+						int num7 = UnityEngine.Random.Range(0, (int)(1f / num2 * 2f) + 2);
+						s_pseudoCounter[num5] = num7;
 						if (flag2)
 						{
-							s_pseudoHistory.Add(num6);
-							if (Terminal.m_testList.ContainsKey("pseudo2"))
-							{
-								ZLog.Log($"Pseudo drop success. Next drop will be in {num6} tries for {drop.m_prefab.name}");
-							}
+							s_pseudoHistory.Add(num7);
+						}
+						if (Terminal.m_showTests && Terminal.m_testList.ContainsKey("pseudo2"))
+						{
+							ZLog.Log($"Pseudo drop success for {drop.m_prefab.name} with chance {num2:0.00} (hash: {num5}). Next drop will be in {num7} tries for {drop.m_prefab.name}");
 						}
 					}
 					else
 					{
-						s_pseudoCounter[drop.m_prefab.name] = new Tuple<float, int>(num2, num5);
+						s_pseudoCounter[num5] = num6;
+						if (Terminal.m_showTests && Terminal.m_testList.ContainsKey("pseudo2"))
+						{
+							ZLog.Log($"Pseudo drop fail for {drop.m_prefab.name} with chance {num2:0.00} (hash: {num5}). Next drop will be in {num6} tries for {drop.m_prefab.name}");
+						}
 					}
 				}
 				if (!(flag & flag3) && (flag || !(UnityEngine.Random.value <= num2)))
 				{
 					continue;
 				}
-				int num7 = (drop.m_dontScale ? UnityEngine.Random.Range(drop.m_amountMin, drop.m_amountMax) : Game.instance.ScaleDrops(drop.m_prefab, drop.m_amountMin, drop.m_amountMax));
-				if (drop.m_levelMultiplier)
+				int num8 = (drop.m_dontScale ? UnityEngine.Random.Range(drop.m_amountMin, drop.m_amountMax) : Game.instance.ScaleDrops(drop.m_prefab, drop.m_amountMin, drop.m_amountMax));
+				if (drop.m_levelMultiplier && !drop.m_levelMultiplierNotAmount)
 				{
-					num7 *= num;
+					num8 *= num;
 				}
 				if (drop.m_onePerPlayer)
 				{
-					num7 = ZNet.instance.GetNrOfPlayers();
+					num8 = ZNet.instance.GetNrOfPlayers();
 				}
-				if (num7 > 100)
+				if (num8 > 100)
 				{
-					num7 = 100;
+					num8 = 100;
 				}
-				if (num7 > 0)
+				if (num8 > 0)
 				{
 					num3++;
 					if (i == 0)
 					{
-						list.Add(new KeyValuePair<GameObject, int>(drop.m_prefab, num7));
+						list.Add(new KeyValuePair<GameObject, int>(drop.m_prefab, num8));
 					}
 				}
 			}
 			if (flag2)
 			{
-				ZLog.Log(string.Format("Pseudo drop test: {0} of {1} tests dropped from base rate: {2} ({3}% deviation). Spread min: {4} max: {5} average: {6} {7}", ((float)num3 / (float)num4).ToString("0.000"), num4, num2, ((float)num3 / (float)num4 / num2 * 100f).ToString("0.0"), (s_pseudoHistory.Count != 0) ? s_pseudoHistory.Min() : 0, (s_pseudoHistory.Count != 0) ? s_pseudoHistory.Max() : 0, (s_pseudoHistory.Count == 0) ? ((object)0) : s_pseudoHistory.Average().ToString("0.00"), drop.m_prefab.name));
+				ZLog.Log(string.Format("Pseudo drop test: {0} of {1} tests dropped from base rate: {2} ({3}% deviation). Spread min: {4} max: {5} average: {6} {7}", ((float)num3 / (float)num4).ToString("0.000"), num4, num2, ((float)num3 / (float)num4 / num2 * 100f - 100f).ToString("0.0"), (s_pseudoHistory.Count != 0) ? s_pseudoHistory.Min() : 0, (s_pseudoHistory.Count != 0) ? s_pseudoHistory.Max() : 0, (s_pseudoHistory.Count == 0) ? ((object)0) : s_pseudoHistory.Average().ToString("0.00"), drop.m_prefab.name));
 			}
 		}
 		return list;
```

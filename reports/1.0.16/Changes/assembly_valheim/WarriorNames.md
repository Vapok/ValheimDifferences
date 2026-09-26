# `WarriorNames.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/WarriorNames.cs
+++ b/WarriorNames.cs
@@ -50,10 +50,10 @@
 		{
 			femaleSuffixes = m_suffixes.Where((string x) => x.EndsWith("_f")).ToArray();
 		}
-		bool num = m_nview.GetZDO().GetInt(ZDOVars.s_modelIndex) == 0;
+		bool flag = m_nview.GetZDO().GetInt(ZDOVars.s_modelIndex) == 0;
 		string text;
 		string text2;
-		if (num)
+		if (flag)
 		{
 			text = ((malePrefixes.Length != 0) ? malePrefixes[Random.Range(0, malePrefixes.Length)] : "");
 			text2 = ((maleSuffixes.Length != 0) ? maleSuffixes[Random.Range(0, maleSuffixes.Length)] : "");
@@ -69,7 +69,7 @@
 			value = Localization.instance.Localize(text) + " ";
 		}
 		string text3 = "";
-		text3 = ((!num) ? (text3 + m_femaleNames[Random.Range(0, m_femaleNames.Length)]) : (text3 + m_maleNames[Random.Range(0, m_maleNames.Length)]));
+		text3 = ((!flag) ? (text3 + m_femaleNames[Random.Range(0, m_femaleNames.Length)]) : (text3 + m_maleNames[Random.Range(0, m_maleNames.Length)]));
 		if ((!string.IsNullOrWhiteSpace(text) && Random.value < m_suffixChance) || Mathf.Approximately(m_suffixChance, 1f))
 		{
 			string text4 = Localization.instance.Localize(text2);
@@ -78,14 +78,14 @@
 				Debug.LogError("Failed to localize string " + text2);
 				return;
 			}
-			int num2 = text4.IndexOf('{');
-			int num3 = text4.IndexOf('}');
-			if (num2 == -1 || num3 == -1)
+			int num = text4.IndexOf('{');
+			int num2 = text4.IndexOf('}');
+			if (num == -1 || num2 == -1)
 			{
 				Debug.LogError("Failed to find interpolation expression characters in " + text4);
 				return;
 			}
-			value = text4.Replace(text4.Substring(num2, num3 - num2 + 1), text3);
+			value = text4.Replace(text4.Substring(num, num2 - num + 1), text3);
 		}
 		if (!string.IsNullOrEmpty(value))
 		{
```

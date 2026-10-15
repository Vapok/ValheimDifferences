# `ZPlayFabLobbySearch.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZPlayFabLobbySearch.cs
+++ b/ZPlayFabLobbySearch.cs
@@ -317,7 +317,7 @@
 			{
 				num = 0u;
 			}
-			if (num != 40 || !searchData.TryGetValue("string_key14", out var value) || !StringUtils.TryDecodeStringAsIDictionary<Dictionary<string, string>>(value, out var decodedDictionary) || !ServerOptionsGUI.TryConvertCompactKVPToModifierKeys(decodedDictionary, out var result4))
+			if (num != 41 || !searchData.TryGetValue("string_key14", out var value) || !StringUtils.TryDecodeStringAsIDictionary<Dictionary<string, string>>(value, out var decodedDictionary) || !ServerOptionsGUI.TryConvertCompactKVPToModifierKeys(decodedDictionary, out var result4))
 			{
 				result4 = new string[0];
 			}
```

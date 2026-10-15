# `ZSteamMatchmaking.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `DecodeTags() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/ZSteamMatchmaking.cs
+++ b/ZSteamMatchmaking.cs
@@ -843,7 +843,7 @@
 				value = tagsString;
 				networkVersion = 0u;
 			}
-			if (networkVersion != 40 || !decodedDictionary.TryGetValue("m", out var value3) || !StringUtils.TryDecodeStringAsIDictionary<Dictionary<string, string>>(value3, out var decodedDictionary2) || !ServerOptionsGUI.TryConvertCompactKVPToModifierKeys(decodedDictionary2, out modifiers))
+			if (networkVersion != 41 || !decodedDictionary.TryGetValue("m", out var value3) || !StringUtils.TryDecodeStringAsIDictionary<Dictionary<string, string>>(value3, out var decodedDictionary2) || !ServerOptionsGUI.TryConvertCompactKVPToModifierKeys(decodedDictionary2, out modifiers))
 			{
 				modifiers = new string[0];
 			}
```

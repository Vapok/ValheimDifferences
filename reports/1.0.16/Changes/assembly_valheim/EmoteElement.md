# `Valheim.UI/EmoteElement.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/EmoteElement.cs
+++ b/Valheim.UI/EmoteElement.cs
@@ -6,19 +6,19 @@
 	{
 		if (mapping.Emote == Emotes.Count)
 		{
-			base.Name = "";
-			base.Interact = null;
+			Name = "";
+			Interact = null;
 		}
 		else
 		{
-			base.Name = ((!string.IsNullOrEmpty(mapping.LocaString)) ? Localization.instance.Localize("$" + mapping.LocaString) : mapping.Emote.ToString());
-			base.Interact = delegate
+			Name = ((!string.IsNullOrEmpty(mapping.LocaString)) ? Localization.instance.Localize("$" + mapping.LocaString) : mapping.Emote.ToString());
+			Interact = () =>
 			{
 				Emote.DoEmote(mapping.Emote);
 				return true;
 			};
 		}
-		base.CloseOnInteract = () => true;
+		CloseOnInteract = () => true;
 		m_icon.gameObject.SetActive(mapping.Sprite != null);
 		m_icon.sprite = mapping.Sprite;
 	}
```

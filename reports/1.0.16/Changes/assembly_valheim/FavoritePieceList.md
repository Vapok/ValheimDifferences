# `FavoritePieceList.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/FavoritePieceList.cs
+++ b/FavoritePieceList.cs
@@ -55,7 +55,7 @@
 
 	public void OpenNewFavoriteTagPopup()
 	{
-		UnifiedPopup.Push(new TextEntryPopup("$hud_addfavoritecategory_popupheader", "$hud_addfavoritecategory_popuptext", "$hud_category", UnifiedPopup.Pop, ValidateTagName, delegate(string favoriteTagName)
+		UnifiedPopup.Push(new TextEntryPopup("$hud_addfavoritecategory_popupheader", "$hud_addfavoritecategory_popuptext", "$hud_category", UnifiedPopup.Pop, ValidateTagName, (string favoriteTagName) =>
 		{
 			if (ValidateTagName(favoriteTagName))
 			{
```

# `Minimap.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `OnMapDblClick() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Minimap.cs
+++ b/Minimap.cs
@@ -2423,7 +2423,8 @@
 
 	public void OnMapDblClick()
 	{
-		if (m_selectedType != PinType.Death)
+		PinType selectedType = m_selectedType;
+		if (selectedType != PinType.Boss && selectedType != PinType.Death)
 		{
 			if (ZInput.IsTouchActive())
 			{
```

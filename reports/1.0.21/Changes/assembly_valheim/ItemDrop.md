# `ItemDrop.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `OnValidate() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/ItemDrop.cs
+++ b/ItemDrop.cs
@@ -1269,7 +1269,7 @@
 	{
 		if (m_itemData.m_shared.m_icons.Length < m_itemData.m_shared.m_variants)
 		{
-			Debug.LogError("Can't have more item variants than item icons! Please add another icon to increase the variant count!");
+			Debug.LogError("Can't have more item variants than item icons! Please add another icon to gameobject [" + gameObject.name + "] increase the variant count!");
 			m_itemData.m_shared.m_variants = m_itemData.m_shared.m_icons.Length;
 		}
 	}
```

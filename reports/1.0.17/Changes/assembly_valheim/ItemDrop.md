# `ItemDrop.cs` Diff (`1.0.16` $\rightarrow$ `1.0.17`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+27/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `private void OnValidate()`
- `public void ResetVariantIfInvalid()`

---

## 📝 Code Diff

```diff
--- a/ItemDrop.cs
+++ b/ItemDrop.cs
@@ -797,6 +797,14 @@
 
 		public Sprite GetIcon()
 		{
+			if (m_variant >= m_shared.m_icons.Length)
+			{
+				if (m_shared.m_icons.Length == 0)
+				{
+					return null;
+				}
+				return m_shared.m_icons[0];
+			}
 			return m_shared.m_icons[m_variant];
 		}
 
@@ -1254,6 +1262,15 @@
 
 	private static int s_itemMask = 0;
 
+	private void OnValidate()
+	{
+		if (m_itemData.m_shared.m_icons.Length < m_itemData.m_shared.m_variants)
+		{
+			Debug.LogError("Can't have more item variants than item icons! Please add another icon to increase the variant count!");
+			m_itemData.m_shared.m_variants = m_itemData.m_shared.m_icons.Length;
+		}
+	}
+
 	private void Awake()
 	{
 		if (!string.IsNullOrEmpty(name))
@@ -1314,8 +1331,18 @@
 
 	private void Start()
 	{
+		ResetVariantIfInvalid();
 		Save();
 		gameObject.GetComponentInChildren<IEquipmentVisual>()?.Setup(m_itemData.m_variant);
+	}
+
+	public void ResetVariantIfInvalid()
+	{
+		if (m_itemData.m_variant > 0 && m_itemData.m_variant >= m_itemData.m_shared.m_variants)
+		{
+			ZLog.LogError($"Variant index {m_itemData.m_variant} does not exist for item {m_itemData.m_shared.m_name}, which has {m_itemData.m_shared.m_variants} variants. Resetting to variant 0!");
+			m_itemData.m_variant = 0;
+		}
 	}
 
 	public static void OnCreateNew(GameObject go, bool cheated = false)
```

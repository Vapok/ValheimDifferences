# `ItemDrop.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+8/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `EnsureValid() [Method Body Modified]`
- `ResetVariantIfInvalid() [Method Body Modified]`
- `ResetVariantIfInvalid() [Method Removed]`
- `Start() [Method Body Modified]`
- `public void EnsureValid()`
- `public void ResetVariantIfInvalid()`

---

## 📝 Code Diff

```diff
--- a/ItemDrop.cs
+++ b/ItemDrop.cs
@@ -548,7 +548,10 @@
 			if (itemVersion >= Version.Item.ChunksNCheats || itemVersion == Version.Item.AbandonedDN)
 			{
 				byte b2 = pkg.ReadByte();
-				itemData.m_cheated = (b2 & 1) != 0;
+				if (itemVersion >= Version.Item.NewCheats)
+				{
+					itemData.m_cheated = (b2 & 1) != 0;
+				}
 			}
 			return result;
 		}
@@ -1331,18 +1334,19 @@
 
 	private void Start()
 	{
-		ResetVariantIfInvalid();
+		EnsureValid();
 		Save();
 		gameObject.GetComponentInChildren<IEquipmentVisual>()?.Setup(m_itemData.m_variant);
 	}
 
-	public void ResetVariantIfInvalid()
+	public void EnsureValid()
 	{
 		if (m_itemData.m_variant > 0 && m_itemData.m_variant >= m_itemData.m_shared.m_variants)
 		{
 			ZLog.LogError($"Variant index {m_itemData.m_variant} does not exist for item {m_itemData.m_shared.m_name}, which has {m_itemData.m_shared.m_variants} variants. Resetting to variant 0!");
 			m_itemData.m_variant = 0;
 		}
+		m_itemData.m_cheated = m_itemData.m_cheated || m_itemData.HasCheatedProperties();
 	}
 
 	public static void OnCreateNew(GameObject go, bool cheated = false)
@@ -1817,7 +1821,7 @@
 		}
 		int hash = ((index >= 0) ? (index + "_itemData").GetStableHashCode() : ZDOVars.s_itemData);
 		ZPackage zPackage = new ZPackage();
-		zPackage.Write((byte)109);
+		zPackage.Write((byte)110);
 		itemData.Save(zPackage);
 		zdo.Set(hash, zPackage.GetArray());
 	}
```

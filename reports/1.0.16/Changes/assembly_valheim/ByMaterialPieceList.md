# `ByMaterialPieceList.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+15/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `private struct RequirementTagData(Piece.Requirement requirement)`

---

## 📝 Code Diff

```diff
--- a/ByMaterialPieceList.cs
+++ b/ByMaterialPieceList.cs
@@ -17,17 +17,26 @@
 		}
 	}
 
-	private struct RequirementTagData(Piece.Requirement requirement)
+	private struct RequirementTagData
 	{
-		public readonly Piece.Requirement m_requirement = requirement;
+		public readonly Piece.Requirement m_requirement;
 
-		public readonly string m_netObjectName = requirement.m_resItem.gameObject.name;
+		public readonly string m_netObjectName;
 
-		public readonly int m_netObjectHash = m_netObjectName.GetStableHashCode();
+		public readonly int m_netObjectHash;
 
-		public readonly string m_displayName = requirement.m_resItem.m_itemData.m_shared.m_name;
+		public readonly string m_displayName;
 
-		public readonly string m_displayNameLocalized = Localization.instance.Localize(m_displayName);
+		public readonly string m_displayNameLocalized;
+
+		public RequirementTagData(Piece.Requirement requirement)
+		{
+			m_requirement = requirement;
+			m_netObjectName = requirement.m_resItem.gameObject.name;
+			m_netObjectHash = m_netObjectName.GetStableHashCode();
+			m_displayName = requirement.m_resItem.m_itemData.m_shared.m_name;
+			m_displayNameLocalized = Localization.instance.Localize(m_displayName);
+		}
 	}
 
 	private readonly string m_displayName;
```

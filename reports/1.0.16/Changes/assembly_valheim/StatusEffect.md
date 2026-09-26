# `StatusEffect.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/StatusEffect.cs
+++ b/StatusEffect.cs
@@ -356,7 +356,7 @@
 	{
 		if (m_nameHash == 0)
 		{
-			m_nameHash = base.name.GetStableHashCode();
+			m_nameHash = name.GetStableHashCode();
 		}
 		return m_nameHash;
 	}
```

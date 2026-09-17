# `SEMan.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SEMan.cs
+++ b/SEMan.cs
@@ -137,6 +137,10 @@
 	public StatusEffect AddStatusEffect(int nameHash, bool resetTime = false, int itemLevel = 0, float skillLevel = 0f, short variant = -1)
 	{
 		if (nameHash == 0)
+		{
+			return null;
+		}
+		if (!m_nview.IsValid())
 		{
 			return null;
 		}
```

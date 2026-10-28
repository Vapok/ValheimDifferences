# `Feast.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `GetHoverText() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Feast.cs
+++ b/Feast.cs
@@ -131,6 +131,10 @@
 
 	public string GetHoverText()
 	{
+		if (m_foodItem == null)
+		{
+			return "";
+		}
 		int stack = GetStack();
 		if (stack <= 0)
 		{
```

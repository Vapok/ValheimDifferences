# `Valheim.UI/EmptyElement.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/EmptyElement.cs
+++ b/Valheim.UI/EmptyElement.cs
@@ -4,7 +4,7 @@
 {
 	public void Init()
 	{
-		base.Name = "Empty";
-		base.Interact = () => false;
+		Name = "Empty";
+		Interact = () => false;
 	}
 }
```

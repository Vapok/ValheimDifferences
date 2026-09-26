# `ItemStyle.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ItemStyle.cs
+++ b/ItemStyle.cs
@@ -4,6 +4,6 @@
 {
 	public void Setup(int style)
 	{
-		MaterialMan.instance.SetValue(base.gameObject, ShaderProps._Style, style);
+		MaterialMan.instance.SetValue(gameObject, ShaderProps._Style, style);
 	}
 }
```

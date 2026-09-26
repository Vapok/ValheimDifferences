# `Valheim.UI/BackElement.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/BackElement.cs
+++ b/Valheim.UI/BackElement.cs
@@ -4,8 +4,8 @@
 {
 	public void Init(RadialBase radial)
 	{
-		base.Name = "Back";
-		base.Interact = delegate
+		Name = "Back";
+		Interact = () =>
 		{
 			radial.Back();
 			return true;
```

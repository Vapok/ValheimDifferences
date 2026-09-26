# `ShieldDomeImageEffect.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ShieldDomeImageEffect.cs
+++ b/ShieldDomeImageEffect.cs
@@ -230,7 +230,7 @@
 	{
 		if ((bool)this)
 		{
-			base.enabled = domes > 0;
+			enabled = domes > 0;
 		}
 	}
 
```

# `SmokeRenderer.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SmokeRenderer.cs
+++ b/SmokeRenderer.cs
@@ -37,7 +37,7 @@
 		}
 		else
 		{
-			UnityEngine.Object.Destroy(base.gameObject);
+			UnityEngine.Object.Destroy(gameObject);
 		}
 	}
 
```

# `GlobalGraphicsConfiguration.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/GlobalGraphicsConfiguration.cs
+++ b/GlobalGraphicsConfiguration.cs
@@ -31,6 +31,6 @@
 			}
 		}
 		ZLog.LogWarning("Couldn't find any graphics configurations for the specified platform!");
-		return default(SoftReference<GraphicsConfiguration>);
+		return default;
 	}
 }
```

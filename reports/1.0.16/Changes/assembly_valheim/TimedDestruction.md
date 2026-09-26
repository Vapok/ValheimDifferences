# `TimedDestruction.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/TimedDestruction.cs
+++ b/TimedDestruction.cs
@@ -42,13 +42,13 @@
 				}
 				if (m_nview.IsOwner())
 				{
-					ZNetScene.instance.Destroy(base.gameObject);
+					ZNetScene.instance.Destroy(gameObject);
 				}
 			}
 		}
 		else
 		{
-			Object.Destroy(base.gameObject);
+			Object.Destroy(gameObject);
 		}
 	}
 }
```

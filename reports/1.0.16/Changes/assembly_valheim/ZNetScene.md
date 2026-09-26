# `ZNetScene.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZNetScene.cs
+++ b/ZNetScene.cs
@@ -66,7 +66,7 @@
 			}
 		}
 		m_instances.Clear();
-		base.enabled = false;
+		enabled = false;
 	}
 
 	public void AddInstance(ZDO zdo, ZNetView nview)
```

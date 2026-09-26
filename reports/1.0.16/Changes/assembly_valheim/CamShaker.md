# `CamShaker.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CamShaker.cs
+++ b/CamShaker.cs
@@ -72,6 +72,6 @@
 				return;
 			}
 		}
-		GameCamera.instance.AddShake(base.transform.position, m_range, m_strength, m_continous);
+		GameCamera.instance.AddShake(transform.position, m_range, m_strength, m_continous);
 	}
 }
```

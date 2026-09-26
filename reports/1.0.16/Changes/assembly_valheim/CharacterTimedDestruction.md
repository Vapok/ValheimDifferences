# `CharacterTimedDestruction.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CharacterTimedDestruction.cs
+++ b/CharacterTimedDestruction.cs
@@ -41,7 +41,7 @@
 				{
 					m_damage = 99999f
 				},
-				m_point = base.transform.position
+				m_point = transform.position
 			}, showDamageText: false, triggerEffects: true);
 		}
 	}
```

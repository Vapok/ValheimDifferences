# `ConditionalObject.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ConditionalObject.cs
+++ b/ConditionalObject.cs
@@ -105,7 +105,7 @@
 					ActivateSpring();
 				}
 				m_enableObject.SetActive(value: true);
-				m_showEffects.Create(base.transform.position, base.transform.rotation, base.transform);
+				m_showEffects.Create(transform.position, transform.rotation, transform);
 				if (!string.IsNullOrEmpty(m_animatorBool))
 				{
 					Animator componentInChildren = m_enableObject.GetComponentInChildren<Animator>();
@@ -115,7 +115,7 @@
 					}
 					else
 					{
-						ZLog.LogError("Object '" + base.name + "' trying to set animation trigger '" + m_animatorBool + "' but no animator was found!");
+						ZLog.LogError("Object '" + name + "' trying to set animation trigger '" + m_animatorBool + "' but no animator was found!");
 					}
 				}
 			}
```

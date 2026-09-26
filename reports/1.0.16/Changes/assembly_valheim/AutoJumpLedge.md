# `AutoJumpLedge.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/AutoJumpLedge.cs
+++ b/AutoJumpLedge.cs
@@ -13,7 +13,7 @@
 		Character component = collider.GetComponent<Character>();
 		if ((bool)component)
 		{
-			component.OnAutoJump(base.transform.forward, m_upVel, m_forwardVel);
+			component.OnAutoJump(transform.forward, m_upVel, m_forwardVel);
 		}
 	}
 }
```

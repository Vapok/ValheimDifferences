# `Dynamics/SecondOrderDynamicsBase.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Dynamics/SecondOrderDynamicsBase.cs
+++ b/Dynamics/SecondOrderDynamicsBase.cs
@@ -23,7 +23,7 @@
 		k3 = r * z / (MathF.PI * 2f * f);
 		_previousInput = x0;
 		_currentValue = x0;
-		_velocity = default(T);
+		_velocity = default;
 	}
 
 	protected SecondOrderDynamicsBase(T x0)
```

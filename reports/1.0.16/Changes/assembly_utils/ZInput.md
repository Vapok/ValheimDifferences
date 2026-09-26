# `ZInput.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZInput.cs
+++ b/ZInput.cs
@@ -1790,9 +1790,9 @@
 		}
 		if (allowSwitchInputSource && s_inputSwitchingMode.HasFlag(InputSource.AllowedInputMask))
 		{
-			bool num = m_inputSource != inputSource;
+			bool flag = m_inputSource != inputSource;
 			m_inputSource = inputSource;
-			if (num && instance != null)
+			if (flag && instance != null)
 			{
 				OnInputLayoutChanged?.Invoke();
 			}
@@ -1950,12 +1950,12 @@
 	{
 		if (m_instance == null)
 		{
-			return default(T);
+			return default;
 		}
 		if (!m_instance.m_values.TryGetValue(name, out var value))
 		{
 			Debug.LogError("No ValueDef with name " + name + " found.");
-			return default(T);
+			return default;
 		}
 		T valueRaw = value.GetValueRaw<T>();
 		if (!(valueRaw is float value2))
@@ -2337,14 +2337,14 @@
 		}
 		action.Disable();
 		InputActionRebindingExtensions.RebindingOperation rebindingOperation = action.PerformInteractiveRebinding().OnPotentialMatch(CancelOnAbortInput).OnApplyBinding(ApplyRebind);
-		if (value.Name.Contains("Tab"))
+		if (value.Name.Contains("Tab") || value.Name.Contains("Console"))
 		{
 			rebindingOperation.WithControlsExcluding("Mouse");
 		}
-		rebindingOperation.Start().OnComplete(delegate(InputActionRebindingExtensions.RebindingOperation op)
+		rebindingOperation.Start().OnComplete((InputActionRebindingExtensions.RebindingOperation op) =>
 		{
 			OnRebindComplete(op, action);
-		}).OnCancel(delegate(InputActionRebindingExtensions.RebindingOperation op)
+		}).OnCancel((InputActionRebindingExtensions.RebindingOperation op) =>
 		{
 			OnRebindComplete(op, action);
 		});
```

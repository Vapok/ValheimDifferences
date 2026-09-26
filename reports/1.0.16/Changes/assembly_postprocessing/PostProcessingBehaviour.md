# `UnityEngine.PostProcessing/PostProcessingBehaviour.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/PostProcessingBehaviour.cs
+++ b/UnityEngine.PostProcessing/PostProcessingBehaviour.cs
@@ -97,7 +97,7 @@
 		{
 			m_ComponentStates.Add(component, value: false);
 		}
-		base.useGUILayout = false;
+		useGUILayout = false;
 	}
 
 	private void OnPreCull()
```

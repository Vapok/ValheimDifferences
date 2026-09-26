# `Tracker.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Tracker.cs
+++ b/Tracker.cs
@@ -10,7 +10,7 @@
 		if ((bool)component && component.IsOwner())
 		{
 			m_active = true;
-			ZNet.instance.SetReferencePosition(base.transform.position);
+			ZNet.instance.SetReferencePosition(transform.position);
 		}
 	}
 
@@ -28,7 +28,7 @@
 	{
 		if (m_active)
 		{
-			ZNet.instance.SetReferencePosition(base.transform.position);
+			ZNet.instance.SetReferencePosition(transform.position);
 		}
 	}
 }
```

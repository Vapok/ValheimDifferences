# `CancelableTaskPopup.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CancelableTaskPopup.cs
+++ b/CancelableTaskPopup.cs
@@ -21,6 +21,6 @@
 			bodyText.text = textRetrievalFunc();
 			yield return null;
 		}
-		base.ShouldClose = true;
+		ShouldClose = true;
 	}
 }
```

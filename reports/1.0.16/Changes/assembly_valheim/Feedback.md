# `Feedback.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Feedback.cs
+++ b/Feedback.cs
@@ -60,7 +60,7 @@
 
 	public void OnBack()
 	{
-		Object.Destroy(base.gameObject);
+		Object.Destroy(gameObject);
 	}
 
 	public void OnSend()
@@ -69,7 +69,7 @@
 		{
 			string category = GetCategory();
 			Gogan.LogEvent("Feedback_" + category, m_subject.text, m_text.text, 0L);
-			Object.Destroy(base.gameObject);
+			Object.Destroy(gameObject);
 		}
 	}
 
```

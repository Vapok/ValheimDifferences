# `Uirotate.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_guiutils.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Uirotate.cs
+++ b/Uirotate.cs
@@ -6,6 +6,6 @@
 
 	private void Update()
 	{
-		base.transform.Rotate(0f, 0f, Time.deltaTime * m_speed);
+		transform.Rotate(0f, 0f, Time.deltaTime * m_speed);
 	}
 }
```

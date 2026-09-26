# `SplitDialog.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SplitDialog.cs
+++ b/SplitDialog.cs
@@ -31,7 +31,7 @@
 	[SerializeField]
 	private TMP_Text m_splitIconName;
 
-	public bool IsActive => base.gameObject.activeSelf;
+	public bool IsActive => gameObject.activeSelf;
 
 	public float SliderValue
 	{
@@ -114,6 +114,6 @@
 
 	public void SetActive(bool active)
 	{
-		base.gameObject.SetActive(active);
+		gameObject.SetActive(active);
 	}
 }
```

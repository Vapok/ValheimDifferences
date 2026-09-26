# `KeyButton.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/KeyButton.cs
+++ b/KeyButton.cs
@@ -88,7 +88,7 @@
 
 	public string GetName()
 	{
-		return base.gameObject.GetComponentInChildren<TMP_Text>().text;
+		return gameObject.GetComponentInChildren<TMP_Text>().text;
 	}
 
 	private void OnClick()
```

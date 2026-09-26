# `Growup.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Growup.cs
+++ b/Growup.cs
@@ -38,7 +38,7 @@
 			return;
 		}
 		Character component = GetComponent<Character>();
-		Character component2 = UnityEngine.Object.Instantiate(GetPrefab(), base.transform.position, base.transform.rotation).GetComponent<Character>();
+		Character component2 = UnityEngine.Object.Instantiate(GetPrefab(), transform.position, transform.rotation).GetComponent<Character>();
 		if ((bool)component && (bool)component2)
 		{
 			if (m_inheritTame)
```

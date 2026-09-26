# `Valheim.UI/RadialArray.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/RadialArray.cs
+++ b/Valheim.UI/RadialArray.cs
@@ -42,7 +42,7 @@
 		{
 			return GetArray[index];
 		}
-		return default(T);
+		return default;
 	}
 
 	public List<T> GetVisibleElementsAt(float cursorPos, int fadeCount, int showCount, bool doubleSided = true)
```

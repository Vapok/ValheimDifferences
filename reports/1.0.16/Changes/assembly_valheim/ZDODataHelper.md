# `ZDODataHelper.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZDODataHelper.cs
+++ b/ZDODataHelper.cs
@@ -13,7 +13,7 @@
 		int key;
 		if (data.Count > 100)
 		{
-			string[] obj = new string[5]
+			string[] array = new string[5]
 			{
 				"Writing a lot of data <",
 				typeof(TType)?.ToString(),
@@ -22,18 +22,18 @@
 				null
 			};
 			key = data.Count;
-			obj[3] = key.ToString();
-			obj[4] = " items, is not optimal. Perhaps use a byte array or two instead?";
-			Debug.LogWarning(string.Concat(obj));
+			array[3] = key.ToString();
+			array[4] = " items, is not optimal. Perhaps use a byte array or two instead?";
+			Debug.LogWarning(string.Concat(array));
 		}
 		pkg.WriteNumItems(data.Count);
 		foreach (KeyValuePair<int, TType> datum in data)
 		{
 			datum.Deconstruct(out key, out var value);
 			int data2 = key;
-			TType obj2 = value;
+			TType obj = value;
 			pkg.Write(data2);
-			writeFunc(obj2);
+			writeFunc(obj);
 		}
 	}
 
```

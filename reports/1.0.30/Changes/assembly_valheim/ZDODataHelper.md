# `ZDODataHelper.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+9/-9` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `ReadFromDisk() [Method Body Modified]`
- `WriteData() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/ZDODataHelper.cs
+++ b/ZDODataHelper.cs
@@ -53,17 +53,17 @@
 		}
 	}
 
-	public static void WriteData<TType>(ZPackage pkg, List<KeyValuePair<int, TType>> data, Action<TType> writeFunc)
+	public static void WriteData<TType>(ZPackage pkg, FastIterableKeyValues<int, TType> data, Action<ZPackage, TType> writeFunc)
 	{
-		if (data.Count == 0)
+		if (data.Count != 0)
 		{
-			return;
-		}
-		pkg.WriteNumItems(data.Count);
-		foreach (var (data2, obj) in data)
-		{
-			pkg.Write(data2);
-			writeFunc(obj);
+			pkg.WriteNumItems(data.Count);
+			for (int i = 0; i < data.Count; i++)
+			{
+				KeyValuePair<int, TType> keyValuePair = data[i];
+				pkg.Write(keyValuePair.Key);
+				writeFunc(pkg, keyValuePair.Value);
+			}
 		}
 	}
 
```

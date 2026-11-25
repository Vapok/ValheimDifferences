# `ZDOHelper.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+43/-23` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `GetAllZDOIDsWithHash() [Method Body Modified]`
- `GetValuesOrEmpty() [Method Body Modified]`
- `GetValuesOrEmptyFilterSession() [Method Body Modified]`
- `InitAndReserve() [Method Body Modified]`
- `InitAndSet() [Method Body Modified]`
- `Update() [Method Body Modified]`
- `Update() [Method Removed]`
- `UpdateIfExists() [Method Body Modified]`
- `UpdateIfExists() [Method Removed]`
- `public static bool InitAndSet(this Dictionary<ZDOID, BinarySearchDictionary<int, byte[]>> container, ZDOID zid, int hash, byte[] value)`

---

## 📝 Code Diff

```diff
--- a/ZDOHelper.cs
+++ b/ZDOHelper.cs
@@ -120,24 +120,44 @@
 		return num;
 	}
 
-	public static bool InitAndSet<TType>(this Dictionary<ZDOID, BinarySearchDictionary<int, TType>> container, ZDOID zid, int hash, TType value)
+	public static bool InitAndSet<TType>(this Dictionary<ZDOID, BinarySearchDictionary<int, TType>> container, ZDOID zid, int hash, TType value) where TType : IEquatable<TType>
 	{
 		container.Init(zid);
-		return container[zid].SetValue(hash, value);
-	}
-
-	public static bool Update<TType>(this Dictionary<ZDOID, BinarySearchDictionary<int, TType>> container, ZDOID zid, int hash, TType value)
-	{
-		return container[zid].SetValue(hash, value);
-	}
-
-	public static bool UpdateIfExists<TType>(this Dictionary<ZDOID, BinarySearchDictionary<int, TType>> container, ZDOID zid, int hash, TType value)
-	{
-		if (container.ContainsKey(zid))
-		{
-			return container[zid].SetValue(hash, value);
-		}
-		return false;
+		BinarySearchDictionary<int, TType> binarySearchDictionary = container[zid];
+		int index = binarySearchDictionary.BinaryFindKeyIndex(hash, out var exactMatch);
+		if (exactMatch)
+		{
+			if (binarySearchDictionary.GetValueByIndex(index).Equals(value))
+			{
+				return false;
+			}
+			binarySearchDictionary.SetValueByIndex(index, value);
+		}
+		else
+		{
+			binarySearchDictionary.Add(hash, value);
+		}
+		return true;
+	}
+
+	public static bool InitAndSet(this Dictionary<ZDOID, BinarySearchDictionary<int, byte[]>> container, ZDOID zid, int hash, byte[] value)
+	{
+		container.Init(zid);
+		BinarySearchDictionary<int, byte[]> binarySearchDictionary = container[zid];
+		int index = binarySearchDictionary.BinaryFindKeyIndex(hash, out var exactMatch);
+		if (exactMatch)
+		{
+			if (binarySearchDictionary.GetValueByIndex(index).Equals(value))
+			{
+				return false;
+			}
+			binarySearchDictionary.SetValueByIndex(index, value);
+		}
+		else
+		{
+			binarySearchDictionary.Add(hash, value);
+		}
+		return true;
 	}
 
 	public static void InitAndReserve<TType>(this Dictionary<ZDOID, BinarySearchDictionary<int, TType>> container, ZDOID zid, int size)
@@ -163,13 +183,13 @@
 		return list;
 	}
 
-	public static List<KeyValuePair<int, TType>> GetValuesOrEmpty<TType>(this Dictionary<ZDOID, BinarySearchDictionary<int, TType>> container, ZDOID zid)
-	{
-		if (!container.ContainsKey(zid))
-		{
-			return Array.Empty<KeyValuePair<int, TType>>().ToList();
-		}
-		return container[zid].ToList();
+	public static FastIterableKeyValues<int, TType> GetValuesOrEmpty<TType>(this Dictionary<ZDOID, BinarySearchDictionary<int, TType>> container, ZDOID zid)
+	{
+		if (!container.TryGetValue(zid, out var value))
+		{
+			return default;
+		}
+		return value.GetFastIterableKeyValues();
 	}
 
 	public static void GetValuesOrEmptyFilterSession<TType>(this Dictionary<ZDOID, BinarySearchDictionary<int, TType>> container, HashSet<int> sessionOnly, ref List<KeyValuePair<int, TType>> listOut, ZDOID zid)
```

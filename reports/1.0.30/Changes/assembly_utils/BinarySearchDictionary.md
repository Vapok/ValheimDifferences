# `BinarySearchDictionary.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+16/-25` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `BinaryFindKeyIndex() [Method Body Modified]`
- `Compare() [Method Body Modified]`
- `GetFastIterableKeyValues() [Method Body Modified]`
- `GetValueByIndex() [Method Body Modified]`
- `GetValueOrDefault() [Method Body Modified]`
- `GuaranteeCapacity() [Method Body Modified]`
- `SetValue() [Method Body Modified]`
- `SetValue() [Method Removed]`
- `SetValueByIndex() [Method Body Modified]`
- `private int BinaryFindKeyIndex(TKey key, out bool exactMatch)`
- `public FastIterableKeyValues<TKey, TValue> GetFastIterableKeyValues()`
- `public TValue GetValueByIndex(int index)`
- `public bool SetValue(TKey key, TValue value)`
- `public int BinaryFindKeyIndex(TKey key, out bool exactMatch)`
- `public void SetValueByIndex(int index, TValue value)`

---

## 📝 Code Diff

```diff
--- a/BinarySearchDictionary.cs
+++ b/BinarySearchDictionary.cs
@@ -235,30 +235,6 @@
 		return defaultValue;
 	}
 
-	public bool SetValue(TKey key, TValue value)
-	{
-		int num = BinaryFindKeyIndex(key, out var exactMatch);
-		if (exactMatch)
-		{
-			if (m_values[num].Equals(value))
-			{
-				return false;
-			}
-			m_values[num] = value;
-			return true;
-		}
-		GuaranteeCapacity();
-		if (m_length - num > 0)
-		{
-			Array.Copy(m_keys, num, m_keys, num + 1, m_length - num);
-			Array.Copy(m_values, num, m_values, num + 1, m_length - num);
-		}
-		m_keys[num] = key;
-		m_values[num] = value;
-		m_length++;
-		return true;
-	}
-
 	IEnumerator IEnumerable.GetEnumerator()
 	{
 		return GetEnumerator();
@@ -287,7 +263,7 @@
 		}
 	}
 
-	private int BinaryFindKeyIndex(TKey key, out bool exactMatch)
+	public int BinaryFindKeyIndex(TKey key, out bool exactMatch)
 	{
 		if (m_length <= 0)
 		{
@@ -329,4 +305,19 @@
 	{
 		return EqualityComparer<T>.Default.Equals(lhs, rhs);
 	}
+
+	public FastIterableKeyValues<TKey, TValue> GetFastIterableKeyValues()
+	{
+		return new FastIterableKeyValues<TKey, TValue>(m_keys, m_values, m_length);
+	}
+
+	public TValue GetValueByIndex(int index)
+	{
+		return m_values[index];
+	}
+
+	public void SetValueByIndex(int index, TValue value)
+	{
+		m_values[index] = value;
+	}
 }
```

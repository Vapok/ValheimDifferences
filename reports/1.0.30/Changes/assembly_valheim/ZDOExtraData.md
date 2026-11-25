# `ZDOExtraData.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `GetConnectionType() [Method Body Modified]`
- `GetData() [Method Body Modified]`
- `Update() [Method Body Modified]`
- `Update() [Method Removed]`
- `public static bool Update(ZDOID zid, int hash, Vector3 value)`
- `public static void GetData(ZDOID zid, out FastIterableKeyValues<int, float> floats, out FastIterableKeyValues<int, Vector3> vec3s, out FastIterableKeyValues<int, Quaternion> quats, out FastIterableKeyValues<int, int> ints, out FastIterableKeyValues<int, long> longs, out FastIterableKeyValues<int, string> strings, out FastIterableKeyValues<int, byte[]> byteArray, out ZDOConnection connectionData)`
- `public static void GetData(ZDOID zid, out List<KeyValuePair<int, float>> floats, out List<KeyValuePair<int, Vector3>> vec3s, out List<KeyValuePair<int, Quaternion>> quats, out List<KeyValuePair<int, int>> ints, out List<KeyValuePair<int, long>> longs, out List<KeyValuePair<int, string>> strings, out List<KeyValuePair<int, byte[]>> byteArray, out ZDOConnection connectionData)`

---

## 📝 Code Diff

```diff
--- a/ZDOExtraData.cs
+++ b/ZDOExtraData.cs
@@ -196,11 +196,6 @@
 		return s_vec3.InitAndSet(zid, hash, value);
 	}
 
-	public static bool Update(ZDOID zid, int hash, Vector3 value)
-	{
-		return s_vec3.Update(zid, hash, value);
-	}
-
 	public static bool Set(ZDOID zid, int hash, Quaternion value)
 	{
 		return s_quats.InitAndSet(zid, hash, value);
@@ -379,7 +374,7 @@
 		return s_connections.GetValueOrDefaultPiktiv(zid, null)?.m_type ?? ConnectionType.None;
 	}
 
-	public static void GetData(ZDOID zid, out List<KeyValuePair<int, float>> floats, out List<KeyValuePair<int, Vector3>> vec3s, out List<KeyValuePair<int, Quaternion>> quats, out List<KeyValuePair<int, int>> ints, out List<KeyValuePair<int, long>> longs, out List<KeyValuePair<int, string>> strings, out List<KeyValuePair<int, byte[]>> byteArray, out ZDOConnection connectionData)
+	public static void GetData(ZDOID zid, out FastIterableKeyValues<int, float> floats, out FastIterableKeyValues<int, Vector3> vec3s, out FastIterableKeyValues<int, Quaternion> quats, out FastIterableKeyValues<int, int> ints, out FastIterableKeyValues<int, long> longs, out FastIterableKeyValues<int, string> strings, out FastIterableKeyValues<int, byte[]> byteArray, out ZDOConnection connectionData)
 	{
 		floats = s_floats.GetValuesOrEmpty(zid);
 		vec3s = s_vec3.GetValuesOrEmpty(zid);
```

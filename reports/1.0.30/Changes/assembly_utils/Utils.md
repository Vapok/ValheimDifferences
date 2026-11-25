# `Utils.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+16/-13` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `CloseToZero() [Method Body Modified]`
- `QuantizeHalfDegrees() [Method Body Modified]`
- `ReadQuaternion() [Method Body Modified]`
- `SmallPosition() [Method Body Modified]`
- `public static uint QuantizeHalfDegrees(float degrees)`

---

## 📝 Code Diff

```diff
--- a/Utils.cs
+++ b/Utils.cs
@@ -1135,21 +1135,24 @@
 		return Quaternion.Euler(bw.ReadVector3());
 	}
 
+	public static uint QuantizeHalfDegrees(float degrees)
+	{
+		int num = (int)Mathf.Round(degrees * 2f);
+		num %= 720;
+		if (num < 0)
+		{
+			num += 720;
+		}
+		return (uint)num;
+	}
+
 	public static bool CloseToZero(this Vector3 v)
 	{
-		if ((int)Abs(v.x * 2f) >= 1)
-		{
-			return false;
-		}
-		if ((int)Abs(v.y * 2f) >= 1)
-		{
-			return false;
-		}
-		if ((int)Abs(v.z * 2f) >= 1)
-		{
-			return false;
-		}
-		return true;
+		if (QuantizeHalfDegrees(v.x) == 0 && QuantizeHalfDegrees(v.y) == 0)
+		{
+			return QuantizeHalfDegrees(v.z) == 0;
+		}
+		return false;
 	}
 
 	public static (bool, Vector2s) SmallPosition(this Vector3 v)
```

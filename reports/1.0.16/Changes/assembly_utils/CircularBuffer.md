# `CircularBuffer/CircularBuffer.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CircularBuffer/CircularBuffer.cs
+++ b/CircularBuffer/CircularBuffer.cs
@@ -126,14 +126,14 @@
 	{
 		ThrowIfEmpty("Cannot take elements from an empty buffer.");
 		Decrement(ref _end);
-		_buffer[_end] = default(T);
+		_buffer[_end] = default;
 		_size--;
 	}
 
 	public void PopFront()
 	{
 		ThrowIfEmpty("Cannot take elements from an empty buffer.");
-		_buffer[_start] = default(T);
+		_buffer[_start] = default;
 		Increment(ref _start);
 		_size--;
 	}
```

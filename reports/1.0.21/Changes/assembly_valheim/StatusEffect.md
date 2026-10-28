# `StatusEffect.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `GetDuration() [Method Body Modified]`
- `GetRemaningTime() [Method Body Modified]`
- `SetDuration() [Method Body Modified]`
- `public void SetDuration(float time)`

---

## 📝 Code Diff

```diff
--- a/StatusEffect.cs
+++ b/StatusEffect.cs
@@ -201,6 +201,11 @@
 		return m_time;
 	}
 
+	public void SetDuration(float time)
+	{
+		m_time = time;
+	}
+
 	public float GetRemaningTime()
 	{
 		return m_ttl - m_time;
```

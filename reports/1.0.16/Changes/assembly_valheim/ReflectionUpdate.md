# `ReflectionUpdate.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ReflectionUpdate.cs
+++ b/ReflectionUpdate.cs
@@ -28,6 +28,11 @@
 	{
 		m_instance = this;
 		m_current = m_probe1;
+		if (Application.isConsolePlatform)
+		{
+			m_probe1.hdr = false;
+			m_probe2.hdr = false;
+		}
 	}
 
 	private void OnDestroy()
```

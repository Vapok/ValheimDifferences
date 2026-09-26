# `GamepadRumble.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/GamepadRumble.cs
+++ b/GamepadRumble.cs
@@ -57,10 +57,10 @@
 	{
 		if (m_instance != null && m_instance != this)
 		{
-			Object.Destroy(base.gameObject);
+			Object.Destroy(gameObject);
 			return;
 		}
-		Object.DontDestroyOnLoad(base.gameObject);
+		Object.DontDestroyOnLoad(gameObject);
 		m_instance = this;
 		m_activeVibrations = new List<AudioSourceVibration>();
 		m_binaryVibration = GetComponent<BinaryVibration>();
```

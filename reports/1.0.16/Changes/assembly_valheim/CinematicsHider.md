# `CinematicsHider.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CinematicsHider.cs
+++ b/CinematicsHider.cs
@@ -4,11 +4,11 @@
 {
 	private void Start()
 	{
-		CinematicsManager.m_hiders.Add(base.gameObject);
+		CinematicsManager.m_hiders.Add(gameObject);
 	}
 
 	private void OnDestroy()
 	{
-		CinematicsManager.m_hiders.Remove(base.gameObject);
+		CinematicsManager.m_hiders.Remove(gameObject);
 	}
 }
```

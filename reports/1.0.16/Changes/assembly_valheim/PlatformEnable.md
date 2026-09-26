# `PlatformEnable.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/PlatformEnable.cs
+++ b/PlatformEnable.cs
@@ -6,6 +6,6 @@
 
 	private void Awake()
 	{
-		base.gameObject.SetActive(m_enabledPlatforms.HasFlag(Version.GetPlatform()));
+		gameObject.SetActive(m_enabledPlatforms.HasFlag(Version.GetPlatform()));
 	}
 }
```

# `SnowDestruction.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SnowDestruction.cs
+++ b/SnowDestruction.cs
@@ -16,7 +16,7 @@
 
 	public void DestroySnow()
 	{
-		m_destructionEffect.Create(base.transform.position, base.transform.rotation);
+		m_destructionEffect.Create(transform.position, transform.rotation);
 		ZNetView component = GetComponent<ZNetView>();
 		if ((object)component != null)
 		{
@@ -24,7 +24,7 @@
 		}
 		else
 		{
-			Object.Destroy(base.gameObject);
+			Object.Destroy(gameObject);
 		}
 	}
 }
```

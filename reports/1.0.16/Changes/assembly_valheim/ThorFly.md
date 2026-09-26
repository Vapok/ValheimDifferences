# `ThorFly.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ThorFly.cs
+++ b/ThorFly.cs
@@ -14,11 +14,11 @@
 
 	private void Update()
 	{
-		base.transform.position = base.transform.position + base.transform.forward * m_speed * Time.deltaTime;
+		transform.position += transform.forward * m_speed * Time.deltaTime;
 		m_timer += Time.deltaTime;
 		if (m_timer > m_ttl)
 		{
-			Object.Destroy(base.gameObject);
+			Object.Destroy(gameObject);
 		}
 	}
 }
```

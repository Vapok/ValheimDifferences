# `MovementTest.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MovementTest.cs
+++ b/MovementTest.cs
@@ -15,7 +15,7 @@
 	private void Start()
 	{
 		m_body = GetComponent<Rigidbody>();
-		m_center = base.transform.position;
+		m_center = transform.position;
 	}
 
 	private void FixedUpdate()
```

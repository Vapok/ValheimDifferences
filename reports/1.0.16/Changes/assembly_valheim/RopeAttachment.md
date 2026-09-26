# `RopeAttachment.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/RopeAttachment.cs
+++ b/RopeAttachment.cs
@@ -59,10 +59,10 @@
 
 	private void FixedUpdate()
 	{
-		if ((bool)m_puller && Vector3.Distance(m_puller.transform.position, base.transform.position) > m_pullDistance)
+		if ((bool)m_puller && Vector3.Distance(m_puller.transform.position, transform.position) > m_pullDistance)
 		{
-			Vector3 position = ((m_puller.transform.position - base.transform.position).normalized * m_maxPullVel - m_boatBody.GetPointVelocity(base.transform.position)) * m_pullForce;
-			m_boatBody.AddForceAtPosition(base.transform.position, position);
+			Vector3 position = ((m_puller.transform.position - transform.position).normalized * m_maxPullVel - m_boatBody.GetPointVelocity(transform.position)) * m_pullForce;
+			m_boatBody.AddForceAtPosition(transform.position, position);
 		}
 	}
 
```

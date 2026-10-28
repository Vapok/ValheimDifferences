# `Character.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `ApplySlippery() [Method Body Modified]`
- `UpdateWalking() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Character.cs
+++ b/Character.cs
@@ -1286,7 +1286,7 @@
 
 	private void ApplySlippery(Vector3 move, ref Vector3 currentVel, Vector3 bodyVel, bool isRunning)
 	{
-		if (!(m_lastGroundCollider == null) && !(m_lastGroundCollider.material == null) && !(m_lastGroundCollider.material.dynamicFriction > 0f) && !m_iceShoes && (s_slipperyStuffMask & m_lastGroundCollider.gameObject.layer) != 0)
+		if (!(m_lastGroundCollider == null) && !(m_lastGroundCollider.material == null) && !(m_lastGroundCollider.material.dynamicFriction > 0f) && !m_iceShoes && (s_slipperyStuffMask & (1 << m_lastGroundCollider.gameObject.layer)) != 0)
 		{
 			float num;
 			if (m_skating)
@@ -1611,7 +1611,7 @@
 		Vector3 vector = m_moveDir;
 		bool flag = IsCrouching();
 		m_running = CheckRun(vector, dt);
-		m_slipping = m_lastGroundCollider != null && m_lastGroundCollider.material != null && m_lastGroundCollider.material.dynamicFriction <= 0f && (s_slipperyStuffMask & m_lastGroundCollider.gameObject.layer) != 0;
+		m_slipping = m_lastGroundCollider != null && m_lastGroundCollider.material != null && m_lastGroundCollider.material.dynamicFriction <= 0f && (s_slipperyStuffMask & (1 << m_lastGroundCollider.gameObject.layer)) != 0;
 		Vector3 vector2 = (transform.position - m_lastPos) / dt;
 		float magnitude = vector2.magnitude;
 		vector2.y = 0f;
```

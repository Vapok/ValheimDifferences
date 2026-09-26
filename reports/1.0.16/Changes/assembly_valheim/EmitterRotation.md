# `EmitterRotation.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/EmitterRotation.cs
+++ b/EmitterRotation.cs
@@ -12,7 +12,7 @@
 
 	private void Start()
 	{
-		m_lastPos = base.transform.position;
+		m_lastPos = transform.position;
 		m_ps = GetComponentInChildren<ParticleSystem>();
 	}
 
@@ -20,7 +20,7 @@
 	{
 		if (m_ps.emission.enabled)
 		{
-			Vector3 position = base.transform.position;
+			Vector3 position = transform.position;
 			Vector3 vector = position - m_lastPos;
 			m_lastPos = position;
 			float t = Mathf.Clamp01(vector.magnitude / Time.deltaTime / m_maxSpeed);
@@ -31,7 +31,7 @@
 			Quaternion a = Quaternion.LookRotation(Vector3.up);
 			Quaternion b = Quaternion.LookRotation(vector);
 			Quaternion to = Quaternion.Lerp(a, b, t);
-			base.transform.rotation = Quaternion.RotateTowards(base.transform.rotation, to, Time.deltaTime * m_rotSpeed);
+			transform.rotation = Quaternion.RotateTowards(transform.rotation, to, Time.deltaTime * m_rotSpeed);
 		}
 	}
 }
```

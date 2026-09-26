# `Cinder.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Cinder.cs
+++ b/Cinder.cs
@@ -36,9 +36,9 @@
 		}
 		if (m_nview.IsValid() && m_nview.IsOwner())
 		{
-			Vector3 position = base.transform.position;
+			Vector3 position = transform.position;
 			position -= EnvMan.instance.GetWindForce() * m_windStrength * 10f;
-			base.transform.position = position;
+			transform.position = position;
 		}
 	}
 
@@ -51,9 +51,9 @@
 			m_vel += Vector3.down * (m_gravity * fixedDeltaTime);
 			float num = Mathf.Pow(m_vel.magnitude, 2f) * m_drag * Time.fixedDeltaTime;
 			m_vel += num * -m_vel.normalized;
-			Vector3 position = base.transform.position;
+			Vector3 position = transform.position;
 			Vector3 vector = position + m_vel * fixedDeltaTime;
-			base.transform.position = vector;
+			transform.position = vector;
 			if (Physics.Raycast(position, m_vel.normalized, out var hitInfo, Vector3.Distance(position, vector), m_raymask))
 			{
 				OnHit(hitInfo.collider, hitInfo.point, hitInfo.normal);
@@ -71,7 +71,7 @@
 			gameObject.GetComponent<CinderSpawner>()?.Setup(GetSpread(), collider.gameObject);
 		}
 		m_haveHit = true;
-		base.transform.position = point;
+		transform.position = point;
 		InvokeRepeating("DestroyNow", 0.25f, 1f);
 	}
 
```

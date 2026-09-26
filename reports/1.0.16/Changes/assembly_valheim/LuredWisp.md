# `LuredWisp.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/LuredWisp.cs
+++ b/LuredWisp.cs
@@ -37,7 +37,7 @@
 	{
 		m_wisps.Add(this);
 		m_nview = GetComponent<ZNetView>();
-		m_targetPoint = base.transform.position;
+		m_targetPoint = transform.position;
 		m_time = Random.Range(0, 1000);
 		InvokeRepeating("UpdateTarget", Random.Range(0f, 2f), 2f);
 	}
@@ -51,11 +51,11 @@
 	{
 		if (m_nview.IsValid() && m_nview.IsOwner() && !(m_despawnTimer > 0f))
 		{
-			WispSpawner bestSpawner = WispSpawner.GetBestSpawner(base.transform.position, m_maxLureDistance);
+			WispSpawner bestSpawner = WispSpawner.GetBestSpawner(transform.position, m_maxLureDistance);
 			if (bestSpawner == null || (m_despawnInDaylight && EnvMan.IsDaylight()))
 			{
 				m_despawnTimer = 3f;
-				m_targetPoint = base.transform.position + Quaternion.Euler(-20f, Random.Range(0, 360), 0f) * Vector3.forward * 100f;
+				m_targetPoint = transform.position + Quaternion.Euler(-20f, Random.Range(0, 360), 0f) * Vector3.forward * 100f;
 			}
 			else
 			{
@@ -80,7 +80,7 @@
 			m_despawnTimer -= dt;
 			if (m_despawnTimer <= 0f)
 			{
-				m_despawnEffects.Create(base.transform.position, base.transform.rotation);
+				m_despawnEffects.Create(transform.position, transform.rotation);
 				m_nview.Destroy();
 				return;
 			}
@@ -88,14 +88,14 @@
 		m_time += dt;
 		float num = m_time * m_noiseSpeed;
 		targetPos += new Vector3(Mathf.Sin(num * 4f), Mathf.Sin(num * 2f) * m_noiseDistanceYScale, Mathf.Cos(num * 5f)) * m_noiseDistance;
-		Vector3 normalized = (targetPos - base.transform.position).normalized;
+		Vector3 normalized = (targetPos - transform.position).normalized;
 		m_ballVel += normalized * m_acceleration * dt;
 		if (m_ballVel.magnitude > m_maxSpeed)
 		{
 			m_ballVel = m_ballVel.normalized * m_maxSpeed;
 		}
 		m_ballVel -= m_ballVel * m_friction;
-		base.transform.position = base.transform.position + m_ballVel * dt;
+		transform.position += m_ballVel * dt;
 	}
 
 	public static int GetWispsInArea(Vector3 p, float r)
```

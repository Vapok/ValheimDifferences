# `MeteorSmash.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MeteorSmash.cs
+++ b/MeteorSmash.cs
@@ -33,13 +33,13 @@
 	{
 		Vector3 vector = Vector3.RotateTowards(Vector3.forward, Vector3.up, MathF.PI / 180f * m_spawnAngle, 0f);
 		vector = (Quaternion.Euler(0f, UnityEngine.Random.value * 360f, 0f) * vector).normalized * m_spawnDistance;
-		m_startPos = base.transform.position + vector;
+		m_startPos = transform.position + vector;
 		m_originalScale = m_meteorObject.transform.localScale;
 		m_meteorObject.SetActive(value: true);
 		m_landingEffect.SetActive(value: false);
-		m_meteorObject.transform.position = Vector3.Lerp(m_startPos, base.transform.position, m_speedCurve.Evaluate(0f));
+		m_meteorObject.transform.position = Vector3.Lerp(m_startPos, transform.position, m_speedCurve.Evaluate(0f));
 		m_meteorObject.transform.localScale = Vector3.Lerp(Vector3.zero, m_originalScale, m_scaleCurve.Evaluate(0f));
-		m_meteorObject.transform.LookAt(base.transform.position);
+		m_meteorObject.transform.LookAt(transform.position);
 	}
 
 	private void Update()
@@ -48,7 +48,7 @@
 		{
 			m_timer += Time.deltaTime;
 			float time = m_timer / m_timeToLand;
-			m_meteorObject.transform.position = Vector3.Lerp(m_startPos, base.transform.position, m_speedCurve.Evaluate(time));
+			m_meteorObject.transform.position = Vector3.Lerp(m_startPos, transform.position, m_speedCurve.Evaluate(time));
 			m_meteorObject.transform.localScale = Vector3.Lerp(Vector3.zero, m_originalScale, m_scaleCurve.Evaluate(time));
 			if (!(m_timer < m_timeToLand) || m_crashed)
 			{
```

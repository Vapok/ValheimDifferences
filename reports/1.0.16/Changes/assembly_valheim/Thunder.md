# `Thunder.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Thunder.cs
+++ b/Thunder.cs
@@ -88,7 +88,7 @@
 	private void SpawnThor()
 	{
 		float num = UnityEngine.Random.value * (MathF.PI * 2f);
-		Vector3 vector = base.transform.position + new Vector3(Mathf.Sin(num), 0f, Mathf.Cos(num)) * m_thorSpawnDistance;
+		Vector3 vector = transform.position + new Vector3(Mathf.Sin(num), 0f, Mathf.Cos(num)) * m_thorSpawnDistance;
 		vector.y += UnityEngine.Random.Range(m_thorSpawnAltitudeMin, m_thorSpawnAltitudeMax);
 		float groundHeight = ZoneSystem.instance.GetGroundHeight(vector);
 		if (vector.y < groundHeight)
@@ -96,7 +96,7 @@
 			vector.y = groundHeight + 50f;
 		}
 		float f = num + 180f + (float)UnityEngine.Random.Range(-45, 45);
-		Vector3 vector2 = base.transform.position + new Vector3(Mathf.Sin(f), 0f, Mathf.Cos(f)) * m_thorSpawnDistance;
+		Vector3 vector2 = transform.position + new Vector3(Mathf.Sin(f), 0f, Mathf.Cos(f)) * m_thorSpawnDistance;
 		vector2.y += UnityEngine.Random.Range(m_thorSpawnAltitudeMin, m_thorSpawnAltitudeMax);
 		float groundHeight2 = ZoneSystem.instance.GetGroundHeight(vector2);
 		if (vector.y < groundHeight2)
@@ -111,9 +111,9 @@
 	{
 		float f = UnityEngine.Random.value * (MathF.PI * 2f);
 		float num = UnityEngine.Random.Range(m_flashDistanceMin, m_flashDistanceMax);
-		m_flashPos = base.transform.position + new Vector3(Mathf.Sin(f), 0f, Mathf.Cos(f)) * num;
+		m_flashPos = transform.position + new Vector3(Mathf.Sin(f), 0f, Mathf.Cos(f)) * num;
 		m_flashPos.y += m_flashAltitude;
-		Quaternion rotation = Quaternion.LookRotation((base.transform.position - m_flashPos).normalized);
+		Quaternion rotation = Quaternion.LookRotation((transform.position - m_flashPos).normalized);
 		GameObject[] array = m_flashEffect.Create(m_flashPos, Quaternion.identity);
 		for (int i = 0; i < array.Length; i++)
 		{
```

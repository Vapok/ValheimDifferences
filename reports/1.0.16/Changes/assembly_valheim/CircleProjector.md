# `CircleProjector.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+13/-13` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CircleProjector.cs
+++ b/CircleProjector.cs
@@ -40,31 +40,31 @@
 		for (int i = 0; i < m_nrOfSegments; i++)
 		{
 			float f = MathF.PI / 180f * m_start + (float)i * num + num2;
-			Vector3 vector = base.transform.position + new Vector3(Mathf.Sin(f) * m_radius, 0f, Mathf.Cos(f) * m_radius);
-			GameObject obj = m_segments[i];
+			Vector3 vector = transform.position + new Vector3(Mathf.Sin(f) * m_radius, 0f, Mathf.Cos(f) * m_radius);
+			GameObject gameObject = m_segments[i];
 			if (Physics.Raycast(vector + Vector3.up * 500f, Vector3.down, out var hitInfo, 1000f, m_mask.value))
 			{
 				vector.y = hitInfo.point.y;
 			}
-			obj.transform.position = vector;
+			gameObject.transform.position = vector;
 		}
 		for (int j = 0; j < m_nrOfSegments; j++)
 		{
-			GameObject gameObject = m_segments[j];
-			GameObject gameObject2;
+			GameObject gameObject2 = m_segments[j];
 			GameObject gameObject3;
+			GameObject gameObject4;
 			if (flag)
 			{
-				gameObject2 = ((j == 0) ? m_segments[m_nrOfSegments - 1] : m_segments[j - 1]);
-				gameObject3 = ((j == m_nrOfSegments - 1) ? m_segments[0] : m_segments[j + 1]);
+				gameObject3 = ((j == 0) ? m_segments[m_nrOfSegments - 1] : m_segments[j - 1]);
+				gameObject4 = ((j == m_nrOfSegments - 1) ? m_segments[0] : m_segments[j + 1]);
 			}
 			else
 			{
-				gameObject2 = ((j == 0) ? gameObject : m_segments[j - 1]);
-				gameObject3 = ((j == m_nrOfSegments - 1) ? gameObject : m_segments[j + 1]);
+				gameObject3 = ((j == 0) ? gameObject2 : m_segments[j - 1]);
+				gameObject4 = ((j == m_nrOfSegments - 1) ? gameObject2 : m_segments[j + 1]);
 			}
-			Vector3 normalized = (gameObject3.transform.position - gameObject2.transform.position).normalized;
-			gameObject.transform.rotation = Quaternion.LookRotation(normalized, Vector3.up);
+			Vector3 normalized = (gameObject4.transform.position - gameObject3.transform.position).normalized;
+			gameObject2.transform.rotation = Quaternion.LookRotation(normalized, Vector3.up);
 		}
 		for (int k = m_nrOfSegments; k < m_segments.Count; k++)
 		{
@@ -90,7 +90,7 @@
 		m_segments.Clear();
 		for (int i = 0; i < m_nrOfSegments; i++)
 		{
-			GameObject item = UnityEngine.Object.Instantiate(m_prefab, base.transform.position, Quaternion.identity, base.transform);
+			GameObject item = UnityEngine.Object.Instantiate(m_prefab, transform.position, Quaternion.identity, transform);
 			m_segments.Add(item);
 		}
 		m_calcStart = m_start;
@@ -108,7 +108,7 @@
 		{
 			for (int j = 0; j < num2; j++)
 			{
-				GameObject gameObject = UnityEngine.Object.Instantiate(m_prefab, base.transform.position, Quaternion.Euler(0f, y, 0f), base.transform);
+				GameObject gameObject = UnityEngine.Object.Instantiate(m_prefab, transform.position, Quaternion.Euler(0f, y, 0f), transform);
 				gameObject.transform.position += gameObject.transform.forward * m_radius * ((float)(j + 1) / (float)(num2 + 1));
 				m_segments.Add(gameObject);
 			}
```

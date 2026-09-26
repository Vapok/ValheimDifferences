# `SE_Demister.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+9/-9` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SE_Demister.cs
+++ b/SE_Demister.cs
@@ -64,20 +64,20 @@
 			return;
 		}
 		_ = m_character;
-		bool num = IsUnderRoof();
+		bool flag = IsUnderRoof();
 		Vector3 position2 = m_character.transform.position;
 		Vector3 vector = m_ballInstance.transform.position;
-		Vector3 vector2 = (num ? m_offsetInterior : m_offset);
-		float num2 = (num ? m_noiseDistanceInterior : m_noiseDistance);
+		Vector3 vector2 = (flag ? m_offsetInterior : m_offset);
+		float num = (flag ? m_noiseDistanceInterior : m_noiseDistance);
 		Vector3 vector3 = position2 + m_character.transform.TransformVector(vector2);
-		float num3 = Time.time * m_noiseSpeed;
-		vector3 += new Vector3(Mathf.Sin(num3 * 4f), Mathf.Sin(num3 * 2f) * m_noiseDistanceYScale, Mathf.Cos(num3 * 5f)) * num2;
-		float num4 = Vector3.Distance(vector3, vector);
-		if (num4 > m_maxDistance * 2f)
+		float num2 = Time.time * m_noiseSpeed;
+		vector3 += new Vector3(Mathf.Sin(num2 * 4f), Mathf.Sin(num2 * 2f) * m_noiseDistanceYScale, Mathf.Cos(num2 * 5f)) * num;
+		float num3 = Vector3.Distance(vector3, vector);
+		if (num3 > m_maxDistance * 2f)
 		{
 			vector = vector3;
 		}
-		else if (num4 > m_maxDistance)
+		else if (num3 > m_maxDistance)
 		{
 			Vector3 normalized = (vector - vector3).normalized;
 			vector = vector3 + normalized * m_maxDistance;
@@ -88,7 +88,7 @@
 		{
 			m_ballVel = m_ballVel.normalized * m_ballMaxSpeed;
 		}
-		if (!num)
+		if (!flag)
 		{
 			Vector3 velocity = m_character.GetVelocity();
 			m_ballVel += velocity * m_characterVelocityFactor * dt;
```

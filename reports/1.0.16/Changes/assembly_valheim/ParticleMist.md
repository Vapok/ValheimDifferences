# `ParticleMist.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+13/-13` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ParticleMist.cs
+++ b/ParticleMist.cs
@@ -67,7 +67,7 @@
 	{
 		m_instance = this;
 		m_ps = GetComponent<ParticleSystem>();
-		m_lastUpdatePos = base.transform.position;
+		m_lastUpdatePos = transform.position;
 	}
 
 	private void OnDestroy()
@@ -103,9 +103,9 @@
 		m_haveActiveMist = demistersSorted.Count > 0;
 		GetAllForcefields(fields);
 		m_inMistAreaTimer += 0.1f;
-		float value = Vector3.Distance(base.transform.position, m_lastUpdatePos);
+		float value = Vector3.Distance(transform.position, m_lastUpdatePos);
 		m_combinedMovement += Mathf.Clamp(value, 0f, 10f);
-		m_lastUpdatePos = base.transform.position;
+		m_lastUpdatePos = transform.position;
 		FindMaxMistAlltitude(50f, out var minMistHeight, out var _);
 		int num = (int)(m_combinedMovement * (float)m_localEmissionPerUnit);
 		if (num > 0)
@@ -113,11 +113,11 @@
 			m_combinedMovement = Mathf.Max(0f, m_combinedMovement - (float)num / (float)m_localEmissionPerUnit);
 		}
 		int toEmit = (int)((float)m_localEmission * 0.1f) + num;
-		Emit(base.transform.position, 0f, m_localRange, toEmit, fields, null, minMistHeight);
+		Emit(transform.position, 0f, m_localRange, toEmit, fields, null, minMistHeight);
 		foreach (Demister field in fields)
 		{
 			float endRange = field.m_forceField.endRange;
-			float num2 = Mathf.Max(0f, Vector3.Distance(field.transform.position, base.transform.position) - endRange);
+			float num2 = Mathf.Max(0f, Vector3.Distance(field.transform.position, transform.position) - endRange);
 			if (!(num2 > m_maxDistance))
 			{
 				float num3 = MathF.PI * 4f * (endRange * endRange);
@@ -130,7 +130,7 @@
 		}
 		foreach (Mister item in demistersSorted)
 		{
-			if (!item.Inside(base.transform.position, 0f))
+			if (!item.Inside(transform.position, 0f))
 			{
 				MisterEmit(item, demistersSorted, fields, minMistHeight, 0.1f);
 			}
@@ -143,14 +143,14 @@
 		{
 			return;
 		}
-		ParticleSystem.EmitParams emitParams = default(ParticleSystem.EmitParams);
+		ParticleSystem.EmitParams emitParams = default;
 		for (int i = 0; i < toEmit; i++)
 		{
 			Vector3 onUnitSphere = UnityEngine.Random.onUnitSphere;
 			Vector3 vector = center + onUnitSphere * (radius + 0.1f + UnityEngine.Random.Range(0f, thickness));
 			if (!(vector.y < minAlt) && !IsInsideOtherDemister(fields, vector, 0f, pf) && Mister.InsideMister(vector))
 			{
-				float num = Vector3.Distance(base.transform.position, vector);
+				float num = Vector3.Distance(transform.position, vector);
 				if (!(num > m_maxDistance))
 				{
 					emitParams.startSize = Mathf.Lerp(m_minSize, m_maxSize, Utils.LerpStep(m_minDistance, m_maxDistance, num));
@@ -165,7 +165,7 @@
 	{
 		Vector3 position = mister.transform.position;
 		float radius = mister.m_radius;
-		float num = Mathf.Max(0f, Vector3.Distance(mister.transform.position, base.transform.position) - radius);
+		float num = Mathf.Max(0f, Vector3.Distance(mister.transform.position, transform.position) - radius);
 		if (num > m_distantMaxRange || mister.IsCompletelyInsideOtherMister(m_distantThickness))
 		{
 			return;
@@ -174,7 +174,7 @@
 		float num3 = Mathf.Lerp(m_distantEmissionMax, 0f, Utils.LerpStep(0f, m_distantMaxRange, num));
 		int num4 = (int)(num2 * num3 * dt);
 		float num5 = mister.transform.position.y + mister.m_height;
-		ParticleSystem.EmitParams emitParams = default(ParticleSystem.EmitParams);
+		ParticleSystem.EmitParams emitParams = default;
 		for (int i = 0; i < num4; i++)
 		{
 			Vector3 onUnitSphere = UnityEngine.Random.onUnitSphere;
@@ -189,7 +189,7 @@
 			}
 			if (!Mister.IsInsideOtherMister(vector, mister) && !IsInsideOtherDemister(fields, vector, 0f, null))
 			{
-				float num6 = Vector3.Distance(base.transform.position, vector);
+				float num6 = Vector3.Distance(transform.position, vector);
 				if (!(num6 > m_distantMaxRange))
 				{
 					emitParams.startSize = Mathf.Lerp(m_distantMinSize, m_distantMaxSize, Utils.LerpStep(0f, m_distantMaxRange, num6));
@@ -285,7 +285,7 @@
 		sortList.Clear();
 		foreach (Demister item in demisters)
 		{
-			sortList.Add(new KeyValuePair<Demister, float>(item, Vector3.Distance(base.transform.position, item.transform.position)));
+			sortList.Add(new KeyValuePair<Demister, float>(item, Vector3.Distance(transform.position, item.transform.position)));
 		}
 		sortList.Sort((KeyValuePair<Demister, float> a, KeyValuePair<Demister, float> b) => a.Value.CompareTo(b.Value));
 		fields.Clear();
@@ -297,7 +297,7 @@
 
 	private void FindMaxMistAlltitude(float testRange, out float minMistHeight, out float maxMistHeight)
 	{
-		Vector3 position = base.transform.position;
+		Vector3 position = transform.position;
 		float num = 0f;
 		int num2 = 20;
 		minMistHeight = 99999f;
```

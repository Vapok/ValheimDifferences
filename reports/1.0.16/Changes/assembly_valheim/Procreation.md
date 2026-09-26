# `Procreation.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Procreation.cs
+++ b/Procreation.cs
@@ -79,20 +79,20 @@
 			GameObject original = m_offspringPrefab;
 			if ((bool)m_noPartnerOffspring)
 			{
-				int nrOfInstances = SpawnSystem.GetNrOfInstances(m_seperatePartner ? m_seperatePartner : m_myPrefab, base.transform.position, m_partnerCheckRange, eventCreaturesOnly: false, procreationOnly: true);
+				int nrOfInstances = SpawnSystem.GetNrOfInstances(m_seperatePartner ? m_seperatePartner : m_myPrefab, transform.position, m_partnerCheckRange, eventCreaturesOnly: false, procreationOnly: true);
 				if ((!m_seperatePartner && nrOfInstances < 2) || ((bool)m_seperatePartner && nrOfInstances < 1))
 				{
 					original = m_noPartnerOffspring;
 				}
 			}
-			Vector3 vector = base.transform.forward;
+			Vector3 vector = transform.forward;
 			if (m_spawnRandomDirection)
 			{
 				float f = UnityEngine.Random.Range(0f, MathF.PI * 2f);
 				vector = new Vector3(Mathf.Cos(f), 0f, Mathf.Sin(f));
 			}
 			float num = ((m_spawnOffsetMax > 0f) ? UnityEngine.Random.Range(m_spawnOffset, m_spawnOffsetMax) : m_spawnOffset);
-			GameObject gameObject = UnityEngine.Object.Instantiate(original, base.transform.position - vector * num, Quaternion.LookRotation(-base.transform.forward, Vector3.up));
+			GameObject gameObject = UnityEngine.Object.Instantiate(original, transform.position - vector * num, Quaternion.LookRotation(-transform.forward, Vector3.up));
 			Character component = gameObject.GetComponent<Character>();
 			if ((bool)component)
 			{
@@ -111,18 +111,18 @@
 			{
 				return;
 			}
-			int nrOfInstances2 = SpawnSystem.GetNrOfInstances(m_myPrefab, base.transform.position, m_totalCheckRange);
-			int nrOfInstances3 = SpawnSystem.GetNrOfInstances(m_offspringPrefab, base.transform.position, m_totalCheckRange);
+			int nrOfInstances2 = SpawnSystem.GetNrOfInstances(m_myPrefab, transform.position, m_totalCheckRange);
+			int nrOfInstances3 = SpawnSystem.GetNrOfInstances(m_offspringPrefab, transform.position, m_totalCheckRange);
 			if (nrOfInstances2 + nrOfInstances3 >= m_maxCreatures)
 			{
 				return;
 			}
-			int nrOfInstances4 = SpawnSystem.GetNrOfInstances(m_seperatePartner ? m_seperatePartner : m_myPrefab, base.transform.position, m_partnerCheckRange, eventCreaturesOnly: false, procreationOnly: true);
+			int nrOfInstances4 = SpawnSystem.GetNrOfInstances(m_seperatePartner ? m_seperatePartner : m_myPrefab, transform.position, m_partnerCheckRange, eventCreaturesOnly: false, procreationOnly: true);
 			if ((bool)m_noPartnerOffspring || (((bool)m_seperatePartner || nrOfInstances4 >= 2) && (!m_seperatePartner || nrOfInstances4 >= 1)))
 			{
 				if (nrOfInstances4 > 0)
 				{
-					m_loveEffects.Create(base.transform.position, base.transform.rotation);
+					m_loveEffects.Create(transform.position, transform.rotation);
 				}
 				int lovePoints = GetLovePoints();
 				lovePoints++;
```

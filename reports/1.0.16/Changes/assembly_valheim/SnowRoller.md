# `SnowRoller.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+17/-14` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SnowRoller.cs
+++ b/SnowRoller.cs
@@ -39,7 +39,7 @@
 
 	private void Update()
 	{
-		if (m_netView.IsOwner())
+		if (m_netView.IsOwner() && !Game.IsPaused())
 		{
 			UpdateSnowInteraction();
 		}
@@ -47,24 +47,24 @@
 
 	private void UpdateSnowInteraction()
 	{
-		m_lastGroundHeight = base.transform.position;
+		m_lastGroundHeight = transform.position;
 		ZoneSystem.instance.GetGroundData(ref m_lastGroundHeight, out var _, out m_lastBiome, out var _, out m_lastHeightmap);
 		if (m_lastBiome != Heightmap.Biome.DeepNorth || m_deepSnowSlowMax == 0f || !(m_lastHeightmap != null))
 		{
 			return;
 		}
-		float num = m_lastHeightmap.GetCultivationMask(base.transform.position) * m_deepSnowSlowMaxHeight;
+		float num = m_lastHeightmap.GetCultivationMask(transform.position) * m_deepSnowSlowMaxHeight;
 		if (num > m_deepSnowSlowStartHeight)
 		{
-			if ((bool)m_deepSnowWalkObj && Vector3.Distance(m_lastDeepSnowWalkPos, base.transform.position) > m_deepSnowWalkObjDist)
+			if ((bool)m_deepSnowWalkObj && Vector3.Distance(m_lastDeepSnowWalkPos, transform.position) > m_deepSnowWalkObjDist)
 			{
-				Object.Instantiate(m_deepSnowWalkObj, base.transform.position, base.transform.rotation);
-				m_lastDeepSnowWalkPos = base.transform.position;
+				Object.Instantiate(m_deepSnowWalkObj, transform.position, transform.rotation);
+				m_lastDeepSnowWalkPos = transform.position;
 			}
 			float num2 = m_lastGroundHeight.y + num;
-			if (base.transform.position.y < num2)
+			if (transform.position.y < num2)
 			{
-				float num3 = num2 - base.transform.position.y;
+				float num3 = num2 - transform.position.y;
 				num3 -= m_deepSnowSlowStartHeight;
 				num3 /= m_deepSnowSlowMaxHeight - m_deepSnowSlowStartHeight;
 				_ = m_deepSnowSlowMax;
@@ -75,13 +75,16 @@
 
 	private void Grow(float value)
 	{
-		if (base.transform.localScale.x > m_maxSnowballSize)
+		if (!(value <= 0f))
 		{
-			base.transform.localScale = new Vector3(m_maxSnowballSize, m_maxSnowballSize, m_maxSnowballSize);
-			return;
+			if (transform.localScale.x > m_maxSnowballSize)
+			{
+				transform.localScale = new Vector3(m_maxSnowballSize, m_maxSnowballSize, m_maxSnowballSize);
+				return;
+			}
+			float num = m_scaleGain * value;
+			transform.localScale += new Vector3(num, num, num);
+			m_rigidbody.mass += value * m_weightGain;
 		}
-		float num = m_scaleGain * value;
-		base.transform.localScale += new Vector3(num, num, num);
-		m_rigidbody.mass += value * m_weightGain;
 	}
 }
```

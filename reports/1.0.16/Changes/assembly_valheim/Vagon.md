# `Vagon.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+8/-8` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Vagon.cs
+++ b/Vagon.cs
@@ -102,7 +102,7 @@
 		m_nview = GetComponent<ZNetView>();
 		if (m_nview.GetZDO() == null)
 		{
-			base.enabled = false;
+			enabled = false;
 			return;
 		}
 		m_instances.Add(this);
@@ -240,15 +240,15 @@
 		{
 			return;
 		}
-		m_lastGroundHeight = base.transform.position;
+		m_lastGroundHeight = transform.position;
 		ZoneSystem.instance.GetGroundData(ref m_lastGroundHeight, out var _, out m_lastBiome, out var _, out m_lastHeightmap);
 		if (m_lastBiome == Heightmap.Biome.DeepNorth || m_lastBiome == Heightmap.Biome.Mountain)
 		{
 			m_slipperyCollider.material = ((IsAttached() || m_chair.IsInUse()) ? m_slipperyMat : null);
-			if (m_lastBiome == Heightmap.Biome.DeepNorth && m_deepSnowWalkObj != null && m_lastHeightmap != null && m_lastHeightmap.GetCultivationMask(base.transform.position) > m_deepSnowFlattenHeight && (bool)m_deepSnowWalkObj && Vector3.Distance(m_lastDeepSnowWalkPos, base.transform.position) > m_deepSnowWalkObjDist)
-			{
-				UnityEngine.Object.Instantiate(m_deepSnowWalkObj, base.transform.position, base.transform.rotation);
-				m_lastDeepSnowWalkPos = base.transform.position;
+			if (m_lastBiome == Heightmap.Biome.DeepNorth && m_deepSnowWalkObj != null && m_lastHeightmap != null && m_lastHeightmap.GetCultivationMask(transform.position) > m_deepSnowFlattenHeight && (bool)m_deepSnowWalkObj && Vector3.Distance(m_lastDeepSnowWalkPos, transform.position) > m_deepSnowWalkObjDist)
+			{
+				UnityEngine.Object.Instantiate(m_deepSnowWalkObj, transform.position, transform.rotation);
+				m_lastDeepSnowWalkPos = transform.position;
 			}
 		}
 	}
@@ -286,7 +286,7 @@
 
 	private bool CanAttach(GameObject go)
 	{
-		if (base.transform.up.y < 0.1f)
+		if (transform.up.y < 0.1f)
 		{
 			return false;
 		}
@@ -301,7 +301,7 @@
 	private void AttachTo(GameObject go)
 	{
 		DetachAll();
-		m_attachJoin = base.gameObject.AddComponent<ConfigurableJoint>();
+		m_attachJoin = gameObject.AddComponent<ConfigurableJoint>();
 		m_attachJoin.autoConfigureConnectedAnchor = false;
 		m_attachJoin.anchor = m_attachPoint.localPosition;
 		m_attachJoin.connectedAnchor = m_attachOffset;
```

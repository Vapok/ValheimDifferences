# `Location.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+11/-11` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Location.cs
+++ b/Location.cs
@@ -57,15 +57,15 @@
 		if (m_hasInterior)
 		{
 			Vector3 zoneCenter = GetZoneCenter();
-			GameObject obj = Object.Instantiate(position: new Vector3(zoneCenter.x, base.transform.position.y + 5000f, zoneCenter.z), original: m_interiorPrefab, rotation: Quaternion.identity, parent: base.transform);
-			obj.transform.localScale = new Vector3(64f, 500f, 64f);
-			obj.GetComponent<EnvZone>().m_environment = m_interiorEnvironment;
+			GameObject gameObject = Object.Instantiate(position: new Vector3(zoneCenter.x, transform.position.y + 5000f, zoneCenter.z), original: m_interiorPrefab, rotation: Quaternion.identity, parent: transform);
+			gameObject.transform.localScale = new Vector3(64f, 500f, 64f);
+			gameObject.GetComponent<EnvZone>().m_environment = m_interiorEnvironment;
 		}
 	}
 
 	private Vector3 GetZoneCenter()
 	{
-		return ZoneSystem.GetZonePos(ZoneSystem.GetZone(base.transform.position));
+		return ZoneSystem.GetZonePos(ZoneSystem.GetZone(transform.position));
 	}
 
 	private void OnDestroy()
@@ -80,20 +80,20 @@
 	private void OnDrawGizmos()
 	{
 		Gizmos.color = new Color(0.8f, 0.8f, 0.8f, 0.5f);
-		Gizmos.matrix = Matrix4x4.TRS(base.transform.position + new Vector3(0f, -0.01f, 0f), Quaternion.identity, new Vector3(1f, 0.001f, 1f));
+		Gizmos.matrix = Matrix4x4.TRS(transform.position + new Vector3(0f, -0.01f, 0f), Quaternion.identity, new Vector3(1f, 0.001f, 1f));
 		Gizmos.DrawSphere(Vector3.zero, m_exteriorRadius);
-		Utils.DrawGizmoCircle(base.transform.position, m_noBuildRadiusOverride, 32);
+		Utils.DrawGizmoCircle(transform.position, m_noBuildRadiusOverride, 32);
 		Gizmos.matrix = Matrix4x4.identity;
 		if (m_hasInterior)
 		{
-			Utils.DrawGizmoCircle(base.transform.position + new Vector3(0f, 5000f, 0f), m_interiorRadius, 32);
-			Utils.DrawGizmoCircle(base.transform.position, m_interiorRadius, 32);
-			Gizmos.matrix = Matrix4x4.TRS(base.transform.position + new Vector3(0f, 5000f, 0f), Quaternion.identity, new Vector3(1f, 0.001f, 1f));
+			Utils.DrawGizmoCircle(transform.position + new Vector3(0f, 5000f, 0f), m_interiorRadius, 32);
+			Utils.DrawGizmoCircle(transform.position, m_interiorRadius, 32);
+			Gizmos.matrix = Matrix4x4.TRS(transform.position + new Vector3(0f, 5000f, 0f), Quaternion.identity, new Vector3(1f, 0.001f, 1f));
 			Gizmos.DrawSphere(Vector3.zero, m_interiorRadius);
 			Gizmos.matrix = Matrix4x4.identity;
 		}
 		Gizmos.color = new Color(0.8f, 0.8f, 0.8f, 0.1f);
-		Utils.DrawGizmoCircle(base.transform.position, m_exteriorRadius, 32);
+		Utils.DrawGizmoCircle(transform.position, m_exteriorRadius, 32);
 	}
 
 	public float GetMaxRadius()
@@ -108,7 +108,7 @@
 	public bool IsInside(Vector3 point, float radius, bool buildCheck = false)
 	{
 		float num = ((buildCheck && m_noBuildRadiusOverride > 0f) ? m_noBuildRadiusOverride : GetMaxRadius());
-		return Utils.DistanceXZ(base.transform.position, point) < num + radius;
+		return Utils.DistanceXZ(transform.position, point) < num + radius;
 	}
 
 	public static bool IsInsideLocation(Vector3 point, float distance)
```

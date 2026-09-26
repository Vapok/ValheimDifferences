# `Floating.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+11/-11` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Floating.cs
+++ b/Floating.cs
@@ -71,7 +71,7 @@
 		{
 			return null;
 		}
-		return base.transform;
+		return transform;
 	}
 
 	private void TerrainCheck()
@@ -80,18 +80,18 @@
 		{
 			return;
 		}
-		float groundHeight = ZoneSystem.instance.GetGroundHeight(base.transform.position);
-		if (base.transform.position.y - groundHeight < -1f)
-		{
-			Vector3 position = base.transform.position;
+		float groundHeight = ZoneSystem.instance.GetGroundHeight(transform.position);
+		if (transform.position.y - groundHeight < -1f)
+		{
+			Vector3 position = transform.position;
 			position.y = groundHeight + 1f;
-			base.transform.position = position;
+			transform.position = position;
 			Rigidbody component = GetComponent<Rigidbody>();
 			if ((bool)component)
 			{
 				component.linearVelocity = Vector3.zero;
 			}
-			ZLog.Log("Moved up item " + base.gameObject.name);
+			ZLog.Log("Moved up item " + gameObject.name);
 		}
 	}
 
@@ -115,7 +115,7 @@
 			return;
 		}
 		SetSurfaceEffect(enabled: true);
-		Vector3 position = m_collider.ClosestPoint(base.transform.position + Vector3.down * 1000f);
+		Vector3 position = m_collider.ClosestPoint(transform.position + Vector3.down * 1000f);
 		Vector3 worldCenterOfMass = m_body.worldCenterOfMass;
 		float num = Mathf.Clamp01(Mathf.Abs(floatDepth) / m_forceDistance);
 		Vector3 vector = m_force * num * (fixedDeltaTime * 50f) * Vector3.up;
@@ -150,7 +150,7 @@
 		{
 			return;
 		}
-		Vector3 vector = m_collider.ClosestPoint(base.transform.position + Vector3.down * 1000f);
+		Vector3 vector = m_collider.ClosestPoint(transform.position + Vector3.down * 1000f);
 		float num = Mathf.Max(m_waterLevel, m_tarLevel);
 		if (vector.y < num)
 		{
@@ -216,7 +216,7 @@
 	{
 		if (!m_body)
 		{
-			m_body = FloatingTerrain.GetBody(base.gameObject);
+			m_body = FloatingTerrain.GetBody(gameObject);
 		}
 	}
 
@@ -228,7 +228,7 @@
 	private void OnDrawGizmosSelected()
 	{
 		Gizmos.color = Color.blue;
-		Gizmos.DrawWireCube(base.transform.position + Vector3.down * m_waterLevelOffset, new Vector3(1f, 0.05f, 1f));
+		Gizmos.DrawWireCube(transform.position + Vector3.down * m_waterLevelOffset, new Vector3(1f, 0.05f, 1f));
 	}
 
 	public static float GetLiquidLevel(Vector3 p, float waveFactor = 1f, LiquidType type = LiquidType.All)
```

# `MeleeWeaponTrail.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-9` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MeleeWeaponTrail.cs
+++ b/MeleeWeaponTrail.cs
@@ -126,7 +126,7 @@
 
 	private void Start()
 	{
-		m_lastPosition = base.transform.position;
+		m_lastPosition = transform.position;
 		m_trailObject = new GameObject("Trail");
 		m_trailObject.transform.parent = null;
 		m_trailObject.transform.position = Vector3.zero;
@@ -136,7 +136,7 @@
 		m_trailObject.AddComponent(typeof(MeshRenderer));
 		m_trailObject.GetComponent<Renderer>().material = _material;
 		m_trailMesh = new Mesh();
-		m_trailMesh.name = base.name + "TrailMesh";
+		m_trailMesh.name = name + "TrailMesh";
 		m_trailObject.GetComponent<MeshFilter>().mesh = m_trailMesh;
 		for (int i = 0; i < 160; i++)
 		{
@@ -178,7 +178,7 @@
 		if (!_emit && m_points.Count == 0 && _autoDestruct)
 		{
 			UnityEngine.Object.Destroy(m_trailObject);
-			UnityEngine.Object.Destroy(base.gameObject);
+			UnityEngine.Object.Destroy(gameObject);
 		}
 		if (Utils.GetMainCamera() == null)
 		{
@@ -186,7 +186,7 @@
 		}
 		if (_emit)
 		{
-			float sqrMagnitude = (m_lastPosition - base.transform.position).sqrMagnitude;
+			float sqrMagnitude = (m_lastPosition - transform.position).sqrMagnitude;
 			if (sqrMagnitude > m_minVertexDistanceSqr)
 			{
 				bool flag = false;
@@ -216,7 +216,7 @@
 					pooledPoint.basePosition = _base.position;
 					pooledPoint.tipPosition = _tip.position;
 					m_points.Add(pooledPoint);
-					m_lastPosition = base.transform.position;
+					m_lastPosition = transform.position;
 					if (m_points.Count == 1)
 					{
 						m_smoothedPoints.Add(pooledPoint);
@@ -347,8 +347,7 @@
 			Point point = smoothedPoints5[k];
 			float num5 = (num4 - point.endTime) / _lifeTime;
 			Color color = Color.Lerp(Color.white, Color.clear, num5);
-			Color[] colors = _colors;
-			int num6 = ((colors != null) ? colors.Length : 0);
+			int num6 = _colors?.Length ?? 0;
 			if (num6 > 0)
 			{
 				float num7 = num5 * (float)(num6 - 1);
@@ -374,8 +373,7 @@
 				color = Color.Lerp(_colors[(int)num8], _colors[(int)num9], t);
 			}
 			float num10 = 0f;
-			float[] sizes = _sizes;
-			int num11 = ((sizes != null) ? sizes.Length : 0);
+			int num11 = _sizes?.Length ?? 0;
 			if (num11 > 0)
 			{
 				float num12 = num5 * (float)(num11 - 1);
```

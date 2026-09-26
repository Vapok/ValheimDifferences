# `LiquidVolume.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/LiquidVolume.cs
+++ b/LiquidVolume.cs
@@ -109,7 +109,7 @@
 	{
 		m_nview = GetComponent<ZNetView>();
 		m_meshFilter = GetComponent<MeshFilter>();
-		base.transform.rotation = Quaternion.identity;
+		transform.rotation = Quaternion.identity;
 		int num = m_width + 1;
 		int num2 = num * num;
 		m_depths = new List<float>(num2);
@@ -129,7 +129,7 @@
 		{
 			InitializeLevels();
 		}
-		m_maxVertex = new Vector3((float)m_width * m_scale * -0.5f, m_maxDepth, (float)m_width * m_scale * -0.5f) + base.transform.position;
+		m_maxVertex = new Vector3((float)m_width * m_scale * -0.5f, m_maxDepth, (float)m_width * m_scale * -0.5f) + transform.position;
 		m_raycastResults = new NativeArray<RaycastHit>(num * num, Allocator.Persistent);
 		m_raycastCommands = new NativeArray<RaycastCommand>(num * num, Allocator.Persistent);
 		m_raycastHitsArray = new RaycastHit[num * num];
@@ -464,7 +464,7 @@
 		int value = m_groundLayer.value;
 		int num = m_width + 1;
 		float num2 = 0f - m_maxDepth;
-		float y = base.transform.position.y;
+		float y = transform.position.y;
 		float distance = m_maxDepth * 2f;
 		Vector3 down = Vector3.down;
 		int num3 = 0;
@@ -820,7 +820,7 @@
 		float depth = GetDepth(vector.x, vector.y);
 		float height = GetHeight(vector.x, vector.y);
 		depth = ((!((double)depth <= 0.001)) ? (depth + Mathf.Sin(p.x * m_noiseFrequency + Time.time * m_noiseSpeed) * Mathf.Sin(p.z * m_noiseFrequency + Time.time * 0.78521f * m_noiseSpeed) * m_noiseHeight) : (depth - 0.5f));
-		return base.transform.position.y + height + depth;
+		return transform.position.y + height + depth;
 	}
 
 	private float GetDepth(float x, float y)
@@ -867,7 +867,7 @@
 
 	private Vector2 WorldToLocal(Vector3 v)
 	{
-		Vector3 position = base.transform.position;
+		Vector3 position = transform.position;
 		float num = (float)m_width * m_scale * -0.5f;
 		Vector2 result = new Vector2(v.x, v.z);
 		result.x -= position.x + num;
@@ -880,7 +880,7 @@
 	private void OnDrawGizmosSelected()
 	{
 		Gizmos.color = Color.green;
-		Gizmos.DrawWireCube(base.transform.position, new Vector3((float)m_width * m_scale, m_maxDepth * 2f, (float)m_width * m_scale));
+		Gizmos.DrawWireCube(transform.position, new Vector3((float)m_width * m_scale, m_maxDepth * 2f, (float)m_width * m_scale));
 	}
 
 	private void UpdateEffects(float dt)
@@ -892,7 +892,7 @@
 			Vector2Int vector2Int = new Vector2Int(Random.Range(0, m_width), Random.Range(0, m_width));
 			if (!(GetDepth(vector2Int.x, vector2Int.y) < 0.2f))
 			{
-				Vector3 basePos = CalcVertex(vector2Int.x, vector2Int.y, collider: false) + base.transform.position;
+				Vector3 basePos = CalcVertex(vector2Int.x, vector2Int.y, collider: false) + transform.position;
 				m_randomEffectList.Create(basePos, Quaternion.identity);
 			}
 		}
```

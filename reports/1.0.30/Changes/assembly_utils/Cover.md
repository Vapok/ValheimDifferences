# `Cover.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+21/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `CreateCoverRays() [Method Body Modified]`
- `Setup() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Cover.cs
+++ b/Cover.cs
@@ -1,3 +1,4 @@
+using Unity.Collections;
 using UnityEngine;
 
 public class Cover
@@ -10,15 +11,26 @@
 
 	private static RaycastHit[] m_raycastHits = new RaycastHit[128];
 
+	private static NativeArray<RaycastCommand> m_commands;
+
+	private static NativeArray<RaycastHit> m_results;
+
+	private static QueryParameters m_queryParameters;
+
 	public static void GetCoverForPoint(Vector3 startPos, out float coverPercentage, out bool underRoof, float minDistance = 0.5f)
 	{
 		Setup();
 		float num = 0f;
 		underRoof = IsUnderRoof(startPos);
-		Vector3[] coverRays = m_coverRays;
-		foreach (Vector3 vector in coverRays)
+		for (int i = 0; i < m_coverRays.Length; i++)
 		{
-			if (Physics.Raycast(startPos + vector * minDistance, vector, out var _, 30f - minDistance, m_coverRayMask))
+			Vector3 vector = m_coverRays[i];
+			m_commands[i] = new RaycastCommand(startPos + vector * minDistance, vector, m_queryParameters, 30f - minDistance);
+		}
+		RaycastCommand.ScheduleBatch(m_commands, m_results, 1).Complete();
+		for (int j = 0; j < m_results.Length; j++)
+		{
+			if (m_results[j].distance > 0f)
 			{
 				num++;
 			}
@@ -46,6 +58,7 @@
 		if (m_coverRays == null)
 		{
 			m_coverRayMask = LayerMask.GetMask("Default", "static_solid", "Default_small", "piece", "terrain", "vehicle");
+			m_queryParameters = new QueryParameters(m_coverRayMask);
 			CreateCoverRays();
 		}
 	}
@@ -77,5 +90,10 @@
 		{
 			vector.Normalize();
 		}
+		if (!m_commands.IsCreated || m_commands.Length != m_coverRays.Length)
+		{
+			m_commands = new NativeArray<RaycastCommand>(m_coverRays.Length, Allocator.Persistent);
+			m_results = new NativeArray<RaycastHit>(m_coverRays.Length, Allocator.Persistent);
+		}
 	}
 }
```

# `SpawnAbility.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+8/-8` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SpawnAbility.cs
+++ b/SpawnAbility.cs
@@ -137,7 +137,7 @@
 		int num3;
 		for (int i = 0; i < toSpawn; num3 = i + 1, i = num3)
 		{
-			Vector3 targetPosition = base.transform.position;
+			Vector3 targetPosition = transform.position;
 			bool foundSpawnPoint = false;
 			int tries = ((m_targetType != TargetType.RandomPathfindablePosition) ? 1 : 5);
 			for (int k = 0; k < tries; k++)
@@ -153,7 +153,7 @@
 					if (k == tries - 1)
 					{
 						Terminal.LogWarning($"SpawnAbility failed to pathfindable target after {tries} tries, defaulting to transform position.");
-						targetPosition = base.transform.position;
+						targetPosition = transform.position;
 						foundSpawnPoint = true;
 					}
 					else
@@ -171,7 +171,7 @@
 			Vector3 spawnPoint = targetPosition;
 			if (m_targetType != TargetType.RandomPathfindablePosition)
 			{
-				Vector3 vector = (m_spawnAtTarget ? targetPosition : base.transform.position);
+				Vector3 vector = (m_spawnAtTarget ? targetPosition : transform.position);
 				Vector2 vector2 = UnityEngine.Random.insideUnitCircle * m_spawnRadius;
 				if (m_circleSpawn)
 				{
@@ -342,7 +342,7 @@
 			{
 				return false;
 			}
-			Character character2 = BaseAI.FindClosestEnemy(m_owner, base.transform.position, m_maxTargetRange);
+			Character character2 = BaseAI.FindClosestEnemy(m_owner, transform.position, m_maxTargetRange);
 			if (character2 != null)
 			{
 				point = character2.transform.position;
@@ -356,7 +356,7 @@
 			{
 				return false;
 			}
-			Character character = BaseAI.FindRandomEnemy(m_owner, base.transform.position, m_maxTargetRange);
+			Character character = BaseAI.FindRandomEnemy(m_owner, transform.position, m_maxTargetRange);
 			if (character != null)
 			{
 				point = character.transform.position;
@@ -365,7 +365,7 @@
 			return false;
 		}
 		case TargetType.Position:
-			point = base.transform.position;
+			point = transform.position;
 			return true;
 		case TargetType.Caster:
 			if (m_owner == null)
@@ -382,12 +382,12 @@
 			}
 			List<Vector3> list = new List<Vector3>();
 			Vector2 vector = UnityEngine.Random.insideUnitCircle.normalized * UnityEngine.Random.Range(m_spawnRadius / 2f, m_spawnRadius);
-			point = base.transform.position + new Vector3(vector.x, 2f, vector.y);
+			point = transform.position + new Vector3(vector.x, 2f, vector.y);
 			ZoneSystem.instance.GetSolidHeight(point, out var height, 2);
 			point.y = height;
 			if (Pathfinding.instance.GetPath(m_owner.transform.position, point, list, m_targetWhenPathfindingType, requireFullPath: true, cleanup: false, havePath: true))
 			{
-				Terminal.Log($"SpawnAbility found path target, distance: {Vector3.Distance(base.transform.position, list[0])}");
+				Terminal.Log($"SpawnAbility found path target, distance: {Vector3.Distance(transform.position, list[0])}");
 				point = list[list.Count - 1];
 				return true;
 			}
```

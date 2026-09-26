# `CreatureSpawner.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CreatureSpawner.cs
+++ b/CreatureSpawner.cs
@@ -155,7 +155,7 @@
 		}
 		if (!m_checkedLocation)
 		{
-			m_location = Location.GetLocation(base.transform.position);
+			m_location = Location.GetLocation(transform.position);
 			m_checkedLocation = true;
 			if ((bool)m_location && m_location.m_blockSpawnGroups.Contains(m_spawnGroupID))
 			{
@@ -175,18 +175,18 @@
 			return;
 		}
 		_ = m_requireSpawnArea;
-		if (!m_spawnInPlayerBase && (bool)EffectArea.IsPointInsideArea(base.transform.position, EffectArea.Type.PlayerBase))
+		if (!m_spawnInPlayerBase && (bool)EffectArea.IsPointInsideArea(transform.position, EffectArea.Type.PlayerBase))
 		{
 			return;
 		}
 		if (m_triggerNoise > 0f)
 		{
-			if (!Player.IsPlayerInRange(base.transform.position, m_triggerDistance, m_triggerNoise))
+			if (!Player.IsPlayerInRange(transform.position, m_triggerDistance, m_triggerNoise))
 			{
 				return;
 			}
 		}
-		else if (!Player.IsPlayerInRange(base.transform.position, m_triggerDistance))
+		else if (!Player.IsPlayerInRange(transform.position, m_triggerDistance))
 		{
 			return;
 		}
@@ -261,7 +261,7 @@
 		{
 			return null;
 		}
-		Vector3 position = base.transform.position;
+		Vector3 position = transform.position;
 		if (ZoneSystem.instance.FindFloor(position, out var height))
 		{
 			position.y = height;
@@ -343,7 +343,7 @@
 	private void SpawnEffect(GameObject spawnedObject)
 	{
 		Character component = spawnedObject.GetComponent<Character>();
-		Vector3 basePos = (component ? component.GetCenterPoint() : (base.transform.position + Vector3.up * 0.75f));
+		Vector3 basePos = (component ? component.GetCenterPoint() : (transform.position + Vector3.up * 0.75f));
 		m_spawnEffects.Create(basePos, Quaternion.identity);
 	}
 
```

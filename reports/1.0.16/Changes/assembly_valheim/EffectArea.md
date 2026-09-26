# `EffectArea.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/EffectArea.cs
+++ b/EffectArea.cs
@@ -67,7 +67,7 @@
 		}
 		m_collider = GetComponent<Collider>();
 		m_collider.isTrigger = true;
-		if ((m_type & Type.NoMonsters) != Type.None)
+		if ((m_type & Type.NoMonsters) != 0)
 		{
 			noMonsterArea = new KeyValuePair<Bounds, EffectArea>(m_collider.bounds, this);
 			s_noMonsterAreas.Add(noMonsterArea);
@@ -76,7 +76,7 @@
 			noMonsterCloseToArea = new KeyValuePair<Bounds, EffectArea>(bounds, this);
 			s_noMonsterCloseToAreas.Add(noMonsterCloseToArea);
 		}
-		if ((m_type & Type.Burning) != Type.None)
+		if ((m_type & Type.Burning) != 0)
 		{
 			Bounds bounds2 = m_collider.bounds;
 			bounds2.Expand(new Vector3(0.25f, 0.25f, 0.25f));
@@ -151,7 +151,7 @@
 			}
 			if (m_isHeatType)
 			{
-				item.OnNearFire(base.transform.position);
+				item.OnNearFire(transform.position);
 			}
 		}
 	}
@@ -204,7 +204,7 @@
 		for (int i = 0; i < num; i++)
 		{
 			EffectArea component = m_tempColliders[i].GetComponent<EffectArea>();
-			if ((bool)component && (component.m_type & type) != Type.None)
+			if ((bool)component && (component.m_type & type) != 0)
 			{
 				return component;
 			}
@@ -243,7 +243,7 @@
 		for (int i = 0; i < num2; i++)
 		{
 			EffectArea component = m_tempColliders[i].GetComponent<EffectArea>();
-			if ((bool)component && (component.m_type & Type.PlayerBase) != Type.None)
+			if ((bool)component && (component.m_type & Type.PlayerBase) != 0)
 			{
 				num++;
 			}
```

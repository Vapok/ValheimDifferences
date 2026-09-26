# `TriggerSpawnAbility.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/TriggerSpawnAbility.cs
+++ b/TriggerSpawnAbility.cs
@@ -10,7 +10,7 @@
 	public void Setup(Character owner, Vector3 velocity, float hitNoise, HitData hitData, ItemDrop.ItemData item, ItemDrop.ItemData ammo)
 	{
 		m_owner = owner;
-		TriggerSpawner.TriggerAllInRange(base.transform.position, m_range);
+		TriggerSpawner.TriggerAllInRange(transform.position, m_range);
 	}
 
 	public string GetTooltipString(int itemQuality)
```

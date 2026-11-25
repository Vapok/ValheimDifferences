# `ShieldGenerator.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `OnDestroy() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/ShieldGenerator.cs
+++ b/ShieldGenerator.cs
@@ -255,7 +255,7 @@
 
 	private void OnDestroy()
 	{
-		if (!m_isPlacementGhost)
+		if (!m_isPlacementGhost && (bool)m_shieldDomeEffect)
 		{
 			m_shieldDomeEffect.RemoveShield(this);
 			m_instances.Remove(this);
```

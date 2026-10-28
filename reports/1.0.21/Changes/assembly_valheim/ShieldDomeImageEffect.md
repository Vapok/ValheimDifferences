# `ShieldDomeImageEffect.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `RemoveShield() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/ShieldDomeImageEffect.cs
+++ b/ShieldDomeImageEffect.cs
@@ -206,7 +206,11 @@
 
 	public void RemoveShield(ShieldGenerator shield)
 	{
-		if (m_shieldDomeData.Remove(shield))
+		if (m_shieldDomeData == null || (object)shield == null)
+		{
+			ZLog.LogError(string.Format("{0}: Tried to remove a Shield in OnDestroy() but something went wrong! Is shieldDomeData null? {1}. Is shield null? {2}", "ShieldDomeImageEffect", m_shieldDomeData == null, (object)shield == null));
+		}
+		else if (m_shieldDomeData.Remove(shield))
 		{
 			ToggleActiveImageEffect(m_shieldDomeData.Count);
 			updateShieldData();
```

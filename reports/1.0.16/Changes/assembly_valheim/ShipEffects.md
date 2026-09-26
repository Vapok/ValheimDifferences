# `ShipEffects.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ShipEffects.cs
+++ b/ShipEffects.cs
@@ -44,7 +44,7 @@
 		ZNetView componentInParent = GetComponentInParent<ZNetView>();
 		if ((bool)componentInParent && componentInParent.GetZDO() == null)
 		{
-			base.enabled = false;
+			enabled = false;
 			return;
 		}
 		m_body = GetComponentInParent<Rigidbody>();
@@ -90,7 +90,7 @@
 
 	public void CustomLateUpdate(float deltaTime)
 	{
-		if (!Floating.IsUnderWater(base.transform.position, ref m_previousWaterVolume))
+		if (!Floating.IsUnderWater(transform.position, ref m_previousWaterVolume))
 		{
 			m_shadow.gameObject.SetActive(value: false);
 			SetWake(enabled: false, deltaTime);
```

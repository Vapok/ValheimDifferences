# `ImpactEffect.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ImpactEffect.cs
+++ b/ImpactEffect.cs
@@ -134,9 +134,9 @@
 		{
 			m_destroyEffect.Create(point, baseRot);
 			GameObject obj = base.gameObject;
-			if ((bool)base.transform.parent)
+			if ((bool)transform.parent)
 			{
-				Animator componentInParent = base.transform.GetComponentInParent<Animator>();
+				Animator componentInParent = transform.GetComponentInParent<Animator>();
 				if ((bool)componentInParent)
 				{
 					obj = componentInParent.gameObject;
```

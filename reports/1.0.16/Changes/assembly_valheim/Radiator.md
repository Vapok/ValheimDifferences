# `Radiator.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Radiator.cs
+++ b/Radiator.cs
@@ -35,7 +35,7 @@
 			if (m_nview.IsValid() && m_nview.IsOwner())
 			{
 				Vector3 onUnitSphere = Random.onUnitSphere;
-				Vector3 position = base.transform.position;
+				Vector3 position = transform.position;
 				if (onUnitSphere.y < 0f)
 				{
 					onUnitSphere.y = 0f - onUnitSphere.y;
```

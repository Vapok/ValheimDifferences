# `GlobalWind.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/GlobalWind.cs
+++ b/GlobalWind.cs
@@ -55,7 +55,7 @@
 		if (m_alignToWindDirection)
 		{
 			Vector3 windDir = EnvMan.instance.GetWindDir();
-			base.transform.rotation = Quaternion.LookRotation(windDir, Vector3.up);
+			transform.rotation = Quaternion.LookRotation(windDir, Vector3.up);
 		}
 		if ((bool)m_ps)
 		{
```

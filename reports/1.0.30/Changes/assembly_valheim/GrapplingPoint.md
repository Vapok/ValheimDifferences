# `GrapplingPoint.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Break() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/GrapplingPoint.cs
+++ b/GrapplingPoint.cs
@@ -394,7 +394,8 @@
 		{
 			Player.m_localPlayer.m_grappling = 0f;
 		}
-		m_anim?.SetBool(m_secondary ? "repell" : "grappling", value: false);
+		m_anim?.SetBool("repell", value: false);
+		m_anim?.SetBool("grappling", value: false);
 		if ((bool)m_se)
 		{
 			m_se.ResetTime();
```

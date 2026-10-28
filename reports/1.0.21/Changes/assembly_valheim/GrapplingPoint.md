# `GrapplingPoint.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Activate() [Method Body Modified]`
- `Pull() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/GrapplingPoint.cs
+++ b/GrapplingPoint.cs
@@ -132,10 +132,13 @@
 
 	public void Pull()
 	{
-		m_secondary = false;
-		m_anim.SetBool("grappling", value: true);
-		m_rotateCharacter = true;
-		m_time = 0f;
+		if (!(m_nview == null) && m_nview.IsOwner() && !(m_anim == null))
+		{
+			m_secondary = false;
+			m_anim.SetBool("grappling", value: true);
+			m_rotateCharacter = true;
+			m_time = 0f;
+		}
 	}
 
 	public void Activate(Character character)
```

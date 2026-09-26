# `CaptionArrow.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CaptionArrow.cs
+++ b/CaptionArrow.cs
@@ -39,7 +39,7 @@
 		m_timer -= Time.deltaTime;
 		if (m_timer <= 0f)
 		{
-			Object.Destroy(base.gameObject);
+			Object.Destroy(gameObject);
 			return;
 		}
 		m_color.a = m_alpha * Mathf.Clamp01(m_timer / m_fadeTime);
@@ -55,6 +55,6 @@
 		Vector3 normalized = Vector3.ProjectOnPlane(Utils.GetMainCamera().transform.forward, Vector3.up).normalized;
 		Vector3 to = position.DirTo(m_sfxPosition);
 		float num = Vector3.SignedAngle(normalized, to, Vector3.up);
-		base.transform.localEulerAngles = new Vector3(0f, 0f, 0f - num);
+		transform.localEulerAngles = new Vector3(0f, 0f, 0f - num);
 	}
 }
```

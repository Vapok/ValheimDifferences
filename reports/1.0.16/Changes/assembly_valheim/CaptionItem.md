# `CaptionItem.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CaptionItem.cs
+++ b/CaptionItem.cs
@@ -42,16 +42,16 @@
 		TimeSinceSpawn += dt;
 		if (m_timer <= 0f)
 		{
-			UnityEngine.Object.Destroy(base.gameObject);
+			UnityEngine.Object.Destroy(gameObject);
 		}
 		float a = Mathf.Clamp01(TimeSinceSpawn * 2f);
 		float b = Mathf.Clamp01(m_timer * 4f);
 		float num = Mathf.Min(a, b);
-		Vector3 localScale = base.transform.localScale;
+		Vector3 localScale = transform.localScale;
 		localScale.y = num;
 		localScale.x = 1f;
 		localScale.z = 1f;
-		base.transform.localScale = localScale;
+		transform.localScale = localScale;
 		m_text.alpha = num;
 	}
 
```

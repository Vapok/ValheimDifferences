# `Petable.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Petable.cs
+++ b/Petable.cs
@@ -30,7 +30,7 @@
 		if (Time.time - m_lastPetTime > 1f)
 		{
 			m_lastPetTime = Time.time;
-			m_petEffect.Create(m_effectLocation ? m_effectLocation.position : base.transform.position, m_effectLocation ? m_effectLocation.rotation : base.transform.rotation);
+			m_petEffect.Create(m_effectLocation ? m_effectLocation.position : transform.position, m_effectLocation ? m_effectLocation.rotation : transform.rotation);
 			user.Message(MessageHud.MessageType.Center, m_name + " " + m_randomPetTexts[Random.Range(0, m_randomPetTexts.Count)]);
 			return true;
 		}
```

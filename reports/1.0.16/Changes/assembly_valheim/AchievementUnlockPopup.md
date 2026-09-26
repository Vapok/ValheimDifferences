# `AchievementUnlockPopup.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/AchievementUnlockPopup.cs
+++ b/AchievementUnlockPopup.cs
@@ -126,7 +126,7 @@
 			m_root.position = new Vector3(m_root.position.x, y, m_root.position.z);
 			if (m_root.position.y >= m_hiddenSpot.transform.position.y - 1f)
 			{
-				Object.Destroy(base.gameObject);
+				Object.Destroy(gameObject);
 			}
 		}
 	}
```

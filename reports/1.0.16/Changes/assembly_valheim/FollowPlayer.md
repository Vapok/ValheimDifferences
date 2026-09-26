# `FollowPlayer.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+14/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/FollowPlayer.cs
+++ b/FollowPlayer.cs
@@ -21,16 +21,27 @@
 		if (!(Player.m_localPlayer == null) && !(mainCamera == null))
 		{
 			Vector3 zero = Vector3.zero;
-			zero = ((m_follow == Type.Camera || GameCamera.InFreeFly()) ? mainCamera.transform.position : ((m_follow != Type.Average) ? Player.m_localPlayer.transform.position : ((!GameCamera.InFreeFly()) ? ((mainCamera.transform.position + Player.m_localPlayer.transform.position) * 0.5f) : mainCamera.transform.position)));
+			if (m_follow == Type.Camera || GameCamera.InFreeFly())
+			{
+				zero = mainCamera.transform.position;
+			}
+			else if (m_follow != Type.Average)
+			{
+				zero = Player.m_localPlayer.transform.position;
+			}
+			else
+			{
+				zero = ((!GameCamera.InFreeFly()) ? ((mainCamera.transform.position + Player.m_localPlayer.transform.position) * 0.5f) : mainCamera.transform.position);
+			}
 			if (m_lockYPos)
 			{
-				zero.y = base.transform.position.y;
+				zero.y = transform.position.y;
 			}
 			if (zero.y > m_maxYPos)
 			{
 				zero.y = m_maxYPos;
 			}
-			base.transform.position = zero;
+			transform.position = zero;
 		}
 	}
 }
```

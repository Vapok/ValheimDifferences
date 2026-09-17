# `Minimap.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Minimap.cs
+++ b/Minimap.cs
@@ -1149,7 +1149,7 @@
 			}
 			if (!m_nameInput.gameObject.activeSelf)
 			{
-				m_mapOffset.x += ZInput.GetJoyLeftStickX(smooth: true) * dt * 50000f * LargeZoom * m_gamepadMoveSpeed;
+				m_mapOffset.x += ZInput.GetJoyLeftStickX() * dt * 50000f * LargeZoom * m_gamepadMoveSpeed;
 				m_mapOffset.z -= ZInput.GetJoyLeftStickY() * dt * 50000f * LargeZoom * m_gamepadMoveSpeed;
 			}
 			if (m_dragView)
```

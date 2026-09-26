# `UpscaledFrameBuffer.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UpscaledFrameBuffer.cs
+++ b/UpscaledFrameBuffer.cs
@@ -54,7 +54,7 @@
 	private void CreateClearCamera()
 	{
 		GameObject gameObject = new GameObject();
-		gameObject.transform.parent = base.transform;
+		gameObject.transform.parent = transform;
 		m_clearCamera = gameObject.AddComponent<Camera>();
 		m_clearCamera.cullingMask = 0;
 		m_clearCamera.allowHDR = false;
```

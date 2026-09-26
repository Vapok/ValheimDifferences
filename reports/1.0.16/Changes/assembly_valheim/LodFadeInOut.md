# `LodFadeInOut.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/LodFadeInOut.cs
+++ b/LodFadeInOut.cs
@@ -11,7 +11,7 @@
 	private void Awake()
 	{
 		Camera mainCamera = Utils.GetMainCamera();
-		if (!(mainCamera == null) && Vector3.Distance(mainCamera.transform.position, base.transform.position) > 20f)
+		if (!(mainCamera == null) && Vector3.Distance(mainCamera.transform.position, transform.position) > 20f)
 		{
 			m_lodGroup = GetComponent<LODGroup>();
 			if ((bool)m_lodGroup)
```

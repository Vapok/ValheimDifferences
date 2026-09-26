# `Gibber.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Gibber.cs
+++ b/Gibber.cs
@@ -45,7 +45,7 @@
 
 	private void Start()
 	{
-		Vector3 vector = base.transform.position;
+		Vector3 vector = transform.position;
 		Vector3 vector2 = Vector3.zero;
 		if ((bool)m_nview && m_nview.IsValid())
 		{
@@ -81,12 +81,12 @@
 			}
 			if (m_nview.IsOwner())
 			{
-				ZNetScene.instance.Destroy(base.gameObject);
+				ZNetScene.instance.Destroy(gameObject);
 			}
 		}
 		else
 		{
-			UnityEngine.Object.Destroy(base.gameObject);
+			UnityEngine.Object.Destroy(gameObject);
 		}
 	}
 
@@ -121,7 +121,7 @@
 		InvokeRepeating("DestroyAll", m_timeout, 1f);
 		float t = (((double)hitDir.magnitude > 0.01) ? m_impactDirectionMix : 0f);
 		CreateBodies();
-		Rigidbody[] componentsInChildren = base.gameObject.GetComponentsInChildren<Rigidbody>();
+		Rigidbody[] componentsInChildren = gameObject.GetComponentsInChildren<Rigidbody>();
 		if (componentsInChildren.Length == 0)
 		{
 			return;
```

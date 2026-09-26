# `RandomObject.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/RandomObject.cs
+++ b/RandomObject.cs
@@ -67,7 +67,7 @@
 
 	public void Reset()
 	{
-		base.gameObject.SetActive(value: true);
+		gameObject.SetActive(value: true);
 		foreach (ObjectEntry @object in m_objects)
 		{
 			if (@object.m_object != null)
@@ -93,7 +93,7 @@
 		}
 		if (spawnObj == null)
 		{
-			base.gameObject.SetActive(value: false);
+			gameObject.SetActive(value: false);
 			ZNetView[] componentsInChildren = GetComponentsInChildren<ZNetView>(includeInactive: true);
 			for (int i = 0; i < componentsInChildren.Length; i++)
 			{
@@ -102,7 +102,7 @@
 		}
 		if (spawnObj != null && GetComponent<ZNetView>() == null)
 		{
-			base.gameObject.SetActive(value: true);
+			gameObject.SetActive(value: true);
 		}
 	}
 
```

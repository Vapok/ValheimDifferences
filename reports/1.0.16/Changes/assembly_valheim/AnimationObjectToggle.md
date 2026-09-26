# `AnimationObjectToggle.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/AnimationObjectToggle.cs
+++ b/AnimationObjectToggle.cs
@@ -10,7 +10,7 @@
 		transform = ((!(m_parentTransform == null)) ? m_parentTransform.Find(objectName) : base.transform.Find(objectName));
 		if (transform == null)
 		{
-			ZLog.LogError("Animation Event script 'AnimationObjectToggle' on '" + base.gameObject.name + "' is trying to toggle the object '" + objectName + "' but it cannot be found in the " + (m_parentTransform ? ("parentTransform '" + m_parentTransform.name + "' set on the script") : "base transform (since no ParentTransform is set)") + ". Parent object: " + ((base.transform.parent == null) ? "NULL" : base.transform.parent.name));
+			ZLog.LogError("Animation Event script 'AnimationObjectToggle' on '" + gameObject.name + "' is trying to toggle the object '" + objectName + "' but it cannot be found in the " + (m_parentTransform ? ("parentTransform '" + m_parentTransform.name + "' set on the script") : "base transform (since no ParentTransform is set)") + ". Parent object: " + ((base.transform.parent == null) ? "NULL" : base.transform.parent.name));
 		}
 		else
 		{
```

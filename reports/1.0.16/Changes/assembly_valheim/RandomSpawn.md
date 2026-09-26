# `RandomSpawn.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/RandomSpawn.cs
+++ b/RandomSpawn.cs
@@ -61,7 +61,7 @@
 	{
 		if (!doSpawn)
 		{
-			base.gameObject.SetActive(value: false);
+			gameObject.SetActive(value: false);
 			foreach (ZNetView childNetView in m_childNetViews)
 			{
 				childNetView.gameObject.SetActive(value: false);
@@ -69,7 +69,7 @@
 		}
 		else if (m_nview == null)
 		{
-			base.gameObject.SetActive(value: true);
+			gameObject.SetActive(value: true);
 		}
 		if (m_OffObject != null)
 		{
@@ -81,10 +81,10 @@
 	{
 		m_nview = GetComponent<ZNetView>();
 		m_childNetViews = new List<ZNetView>();
-		ZNetView[] componentsInChildren = base.gameObject.GetComponentsInChildren<ZNetView>(includeInactive: true);
+		ZNetView[] componentsInChildren = gameObject.GetComponentsInChildren<ZNetView>(includeInactive: true);
 		foreach (ZNetView zNetView in componentsInChildren)
 		{
-			if (Utils.IsEnabledInheirarcy(zNetView.gameObject, base.gameObject))
+			if (Utils.IsEnabledInheirarcy(zNetView.gameObject, gameObject))
 			{
 				m_childNetViews.Add(zNetView);
 			}
```

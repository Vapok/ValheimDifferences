# `LineConnect.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/LineConnect.cs
+++ b/LineConnect.cs
@@ -91,8 +91,8 @@
 
 	private void SetEndpoint(Vector3 pos)
 	{
-		Vector3 vector = base.transform.InverseTransformPoint(pos);
-		Vector3 vector2 = base.transform.InverseTransformDirection(Vector3.down);
+		Vector3 vector = transform.InverseTransformPoint(pos);
+		Vector3 vector2 = transform.InverseTransformDirection(Vector3.down);
 		if (m_dynamicSlack)
 		{
 			float num = m_nview.GetZDO().GetFloat(m_slackHash, m_slack);
@@ -116,7 +116,7 @@
 		}
 		if (m_dynamicThickness)
 		{
-			float v = Vector3.Distance(base.transform.position, pos);
+			float v = Vector3.Distance(transform.position, pos);
 			float f = Utils.LerpStep(m_minDistance, m_maxDistance, v);
 			f = Mathf.Pow(f, m_thicknessPower);
 			m_lineRenderer.widthMultiplier = Mathf.Lerp(m_maxThickness, m_minThickness, f);
```

# `Pet.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Pet.cs
+++ b/Pet.cs
@@ -68,7 +68,7 @@
 		}
 		foreach (Player item in allPlayers)
 		{
-			float num3 = Utils.DistanceXZ(item.transform.position, base.transform.position);
+			float num3 = Utils.DistanceXZ(item.transform.position, transform.position);
 			if (num > num3)
 			{
 				num = num3;
@@ -154,7 +154,7 @@
 		{
 			return m_deepKnowledge[instance.GetDay() % m_deepKnowledge.Count];
 		}
-		Vector3 position = base.transform.position;
+		Vector3 position = transform.position;
 		string text = EnvMan.instance.GetCurrentEnvironment().m_name;
 		if (position.x * position.x > 106300000f - position.z * position.z)
 		{
```

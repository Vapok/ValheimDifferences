# `EggGrow.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+13/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/EggGrow.cs
+++ b/EggGrow.cs
@@ -66,8 +66,8 @@
 		UpdateEffects(num);
 		if (num > 0f && ZNet.instance.GetTimeSeconds() > (double)(num + m_growTime))
 		{
-			Character component = Object.Instantiate(m_grownPrefab, base.transform.position, base.transform.rotation).GetComponent<Character>();
-			m_hatchEffect.Create(base.transform.position, base.transform.rotation);
+			Character component = Object.Instantiate(m_grownPrefab, transform.position, transform.rotation).GetComponent<Character>();
+			m_hatchEffect.Create(transform.position, transform.rotation);
 			if ((bool)component)
 			{
 				component.SetTamed(m_tamed);
@@ -83,13 +83,13 @@
 		{
 			return false;
 		}
-		if (m_requireNearbyFire && !EffectArea.IsPointInsideArea(base.transform.position, EffectArea.Type.Heat, 0.5f))
+		if (m_requireNearbyFire && !EffectArea.IsPointInsideArea(transform.position, EffectArea.Type.Heat, 0.5f))
 		{
 			return false;
 		}
 		if (m_requireUnderRoof)
 		{
-			Cover.GetCoverForPoint(base.transform.position, out var coverPercentage, out var underRoof, 0.1f);
+			Cover.GetCoverForPoint(transform.position, out var coverPercentage, out var underRoof, 0.1f);
 			if (!underRoof || coverPercentage < m_requireCoverPercentige)
 			{
 				return false;
@@ -121,7 +121,15 @@
 			return m_item.GetHoverText();
 		}
 		bool flag = m_nview.GetZDO().GetFloat(ZDOVars.s_growStart) > 0f;
-		string text = ((m_item.m_itemData.m_stack > 1) ? "$item_chicken_egg_stacked" : (flag ? "$item_chicken_egg_warm" : "$item_chicken_egg_cold"));
+		string text;
+		if (m_item.m_itemData.m_stack > 1)
+		{
+			text = "$item_chicken_egg_stacked";
+		}
+		else
+		{
+			text = (flag ? "$item_chicken_egg_warm" : "$item_chicken_egg_cold");
+		}
 		string hoverText = m_item.GetHoverText();
 		int num = hoverText.IndexOf('\n');
 		if (num > 0)
```

# `Vine.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+37/-34` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `CheckGrowChance() [Method Body Modified]`
- `Grow() [Method Body Modified]`
- `UpdateGrow() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Vine.cs
+++ b/Vine.cs
@@ -246,10 +246,12 @@
 		if (!m_dupeCheck)
 		{
 			m_dupeCheck = true;
-			foreach (Vine s_allVine in s_allVines)
-			{
-				if (s_allVine != this && (bool)s_allVine && !m_pickable.CanBePicked() && Vector3.Distance(s_allVine.transform.position, transform.position) < 0.01f)
+			for (int num = s_allVines.Count - 1; num >= 0; num--)
+			{
+				Vine vine = s_allVines[num];
+				if (vine != this && (bool)vine && !m_pickable.CanBePicked() && Vector3.Distance(vine.transform.position, transform.position) < 0.01f)
 				{
+					s_allVines.Remove(this);
 					ZNetScene.instance.Destroy(gameObject);
 					return false;
 				}
@@ -259,47 +261,47 @@
 		{
 			m_initialGrowItterations = 0;
 		}
-		long num;
-		long num3;
+		long num2;
+		long num4;
 		if (m_initialGrowItterations <= 0)
 		{
-			num = (ZNet.instance ? ZNet.instance.GetTime().Ticks : 0);
+			num2 = (ZNet.instance ? ZNet.instance.GetTime().Ticks : 0);
 			if ((bool)m_nview)
 			{
 				ZDO zDO = m_nview.GetZDO();
 				if (zDO != null)
 				{
-					long num2 = zDO.GetLong(ZDOVars.s_growStart, 0L);
-					num3 = num2;
-					goto IL_0139;
+					long num3 = zDO.GetLong(ZDOVars.s_growStart, 0L);
+					num4 = num3;
+					goto IL_0134;
 				}
 			}
-			num3 = 0L;
-			goto IL_0139;
-		}
-		goto IL_01c3;
-		IL_01c3:
+			num4 = 0L;
+			goto IL_0134;
+		}
+		goto IL_01be;
+		IL_01be:
 		if ((bool)m_nview && m_nview.IsOwner() && m_nview.IsValid())
 		{
 			m_nview.GetZDO().Set(ZDOVars.s_growStart, ZNet.instance.GetTime().Ticks);
 		}
 		m_originOffset = GetOriginOffset();
-		int num4 = 0;
+		int num5 = 0;
 		bool flag = m_rnd.NextDouble() < (double)m_maxGrowEdgeIgnoreChance;
 		if (m_growSides)
 		{
-			float num5 = m_maxGrowWidth + m_originOffset.y * m_extraGrowWidthPerHeight;
-			if (flag || m_originOffset.z + 1f <= num5)
-			{
-				num4 += CheckGrowChance(new Vector3(0f, 0f, 1f), VineType.Left, VineState.ClosedLeft, VineState.BranchLeft, VineState.BranchRight);
+			float num6 = m_maxGrowWidth + m_originOffset.y * m_extraGrowWidthPerHeight;
+			if (flag || m_originOffset.z + 1f <= num6)
+			{
+				num5 += CheckGrowChance(new Vector3(0f, 0f, 1f), VineType.Left, VineState.ClosedLeft, VineState.BranchLeft, VineState.BranchRight);
 			}
 			else
 			{
 				m_vineState |= VineState.ClosedLeft;
 			}
-			if (flag || Mathf.Abs(m_originOffset.z) + 1f <= num5)
-			{
-				num4 += CheckGrowChance(new Vector3(0f, 0f, -1f), VineType.Right, VineState.ClosedRight, VineState.BranchRight, VineState.BranchLeft);
+			if (flag || Mathf.Abs(m_originOffset.z) + 1f <= num6)
+			{
+				num5 += CheckGrowChance(new Vector3(0f, 0f, -1f), VineType.Right, VineState.ClosedRight, VineState.BranchRight, VineState.BranchLeft);
 			}
 			else
 			{
@@ -310,7 +312,7 @@
 		{
 			if (flag || m_originOffset.y + 1f <= m_maxGrowUp)
 			{
-				num4 += CheckGrowChance(new Vector3(0f, 1f, 0f), VineType.Top, VineState.ClosedTop, VineState.BranchTop, VineState.BranchBottom);
+				num5 += CheckGrowChance(new Vector3(0f, 1f, 0f), VineType.Top, VineState.ClosedTop, VineState.BranchTop, VineState.BranchBottom);
 			}
 			else
 			{
@@ -321,7 +323,7 @@
 		{
 			if (flag || m_originOffset.y - 1f >= m_maxGrowDown)
 			{
-				num4 += CheckGrowChance(new Vector3(0f, -1f, 0f), VineType.Bottom, VineState.ClosedBottom, VineState.BranchBottom, VineState.BranchTop);
+				num5 += CheckGrowChance(new Vector3(0f, -1f, 0f), VineType.Bottom, VineState.ClosedBottom, VineState.BranchBottom, VineState.BranchTop);
 			}
 			else
 			{
@@ -329,23 +331,23 @@
 			}
 		}
 		IsDoneGrowing = IsDone();
-		return num4 > 0;
-		IL_0139:
-		long num6 = num3;
-		int num7 = (int)((float)((num - ((m_plantTime > num6) ? m_plantTime : num6)) / 10000000) / (m_growTime + m_growTimePerBranch * (float)GetBranches()));
-		if (num7 < 1)
+		return num5 > 0;
+		IL_0134:
+		long num7 = num4;
+		int num8 = (int)((float)((num2 - ((m_plantTime > num7) ? m_plantTime : num7)) / 10000000) / (m_growTime + m_growTimePerBranch * (float)GetBranches()));
+		if (num8 < 1)
 		{
 			return false;
 		}
-		if (num7 >= 2 && num7 > m_initialGrowItterations)
-		{
-			m_initialGrowItterations = num7 - 1;
+		if (num8 >= 2 && num8 > m_initialGrowItterations)
+		{
+			m_initialGrowItterations = num8 - 1;
 			if (Terminal.m_showTests && Terminal.m_testList.ContainsKey("vine"))
 			{
 				Terminal.Log($"Vine is queuing {m_initialGrowItterations} itterations to catch up!");
 			}
 		}
-		goto IL_01c3;
+		goto IL_01be;
 	}
 
 	private int CheckGrowChance(Vector3 offset, VineType type, VineState closed, VineState branch, VineState branchFrom)
@@ -473,7 +475,8 @@
 		Vine component = UnityEngine.Object.Instantiate(m_vinePrefab, transform.position, transform.rotation).GetComponent<Vine>();
 		component.transform.Translate(offset * m_size, Space.Self);
 		component.SetType(type);
-		component.name = component.name.Substring(0, Mathf.Min(component.name.Length, 15));
+		string text = "(Clone)";
+		component.name = (component.name.EndsWith(text) ? component.name.Substring(0, text.Length) : component.name);
 		component.m_vineState |= growingFrom;
 		component.m_initialGrowItterations = m_initialGrowItterations - 1;
 		component.m_pickable.m_respawnTimeInitMin += m_initialGrowItterations;
```

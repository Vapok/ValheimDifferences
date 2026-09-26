# `DropTable.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+27/-19` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/DropTable.cs
+++ b/DropTable.cs
@@ -122,52 +122,60 @@
 		{
 			dropsTemp.Clear();
 			dropsTemp.AddRange(m_drops);
-			bool num2 = (float)(i + 1) == num;
-			float num3 = Game.m_resourceRate % 1f;
-			if (num3 == 0f)
+			bool flag = (float)(i + 1) == num;
+			float num2 = Game.m_resourceRate % 1f;
+			if (num2 == 0f)
+			{
+				num2 = 1f;
+			}
+			float num3;
+			if (flag)
+			{
+				num3 = ((num2 == 0f) ? 1f : num2);
+			}
+			else
 			{
 				num3 = 1f;
 			}
-			float num4 = ((!num2) ? 1f : ((num3 == 0f) ? 1f : num3));
-			float num5 = 0f;
+			float num4 = 0f;
 			foreach (DropData item in dropsTemp)
 			{
-				num5 += item.m_weight;
+				num4 += item.m_weight;
 				if (item.m_weight <= 0f && dropsTemp.Count > 1)
 				{
 					ZLog.LogWarning($"Droptable item '{item.m_item}' has a weight of 0 and will not be dropped correctly!");
 				}
 			}
-			if (num4 < 1f && amount > dropsTemp.Count)
+			if (num3 < 1f && amount > dropsTemp.Count)
 			{
-				amount = (int)Mathf.Max(1f, Mathf.Round((float)amount * num4));
+				amount = (int)Mathf.Max(1f, Mathf.Round((float)amount * num3));
 			}
 			for (int j = 0; j < amount; j++)
 			{
-				float num6 = UnityEngine.Random.Range(0f, num5);
-				bool flag = false;
-				float num7 = 0f;
+				float num5 = UnityEngine.Random.Range(0f, num4);
+				bool flag2 = false;
+				float num6 = 0f;
 				foreach (DropData item2 in dropsTemp)
 				{
-					num7 += item2.m_weight;
-					if (num6 <= num7)
+					num6 += item2.m_weight;
+					if (num5 <= num6)
 					{
-						flag = true;
-						int num8 = 0;
-						num8 = ((!item2.m_dontScale) ? ((int)Mathf.Max(1f, Mathf.Round(UnityEngine.Random.Range(Mathf.Round((float)item2.m_stackMin * num4), Mathf.Round((float)item2.m_stackMax * num4))))) : ((i == 0) ? UnityEngine.Random.Range(item2.m_stackMin, item2.m_stackMax) : 0));
-						for (int k = 0; k < num8; k++)
+						flag2 = true;
+						int num7 = 0;
+						num7 = ((!item2.m_dontScale) ? ((int)Mathf.Max(1f, Mathf.Round(UnityEngine.Random.Range(Mathf.Round((float)item2.m_stackMin * num3), Mathf.Round((float)item2.m_stackMax * num3))))) : ((i == 0) ? UnityEngine.Random.Range(item2.m_stackMin, item2.m_stackMax) : 0));
+						for (int k = 0; k < num7; k++)
 						{
 							list.Add(item2.m_item);
 						}
 						if (m_oneOfEach)
 						{
 							dropsTemp.Remove(item2);
-							num5 -= item2.m_weight;
+							num4 -= item2.m_weight;
 						}
 						break;
 					}
 				}
-				if (!flag && dropsTemp.Count > 0)
+				if (!flag2 && dropsTemp.Count > 0)
 				{
 					list.Add(dropsTemp[0].m_item);
 				}
```

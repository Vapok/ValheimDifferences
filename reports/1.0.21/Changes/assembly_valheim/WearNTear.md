# `WearNTear.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+32/-30` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `ClearCachedSupport() [Method Body Modified]`
- `UpdateSupport() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/WearNTear.cs
+++ b/WearNTear.cs
@@ -201,6 +201,8 @@
 	private float m_lastMaterialValueTimeCheck;
 
 	private readonly List<Collider> m_supportColliders = new List<Collider>();
+
+	private readonly List<WearNTear> m_supportWearNTear = new List<WearNTear>();
 
 	private readonly List<Vector3> m_supportPositions = new List<Vector3>();
 
@@ -809,6 +811,7 @@
 	{
 		m_supportColliders.Clear();
 		m_supportPositions.Clear();
+		m_supportWearNTear.Clear();
 		m_supportValue.Clear();
 	}
 
@@ -831,25 +834,23 @@
 				{
 					break;
 				}
-				WearNTear componentInParent = collider.GetComponentInParent<WearNTear>();
-				if (componentInParent == null || !componentInParent.m_supports)
+				WearNTear wearNTear = m_supportWearNTear[i];
+				if (wearNTear == null || !wearNTear.m_supports || collider.transform.position != m_supportPositions[i])
 				{
 					break;
 				}
-				if (collider != null && collider.transform.position == m_supportPositions[i])
-				{
-					float support = componentInParent.GetSupport();
-					if (support > num2)
-					{
-						num2 = support;
-					}
-					if (support.Equals(m_supportValue[i]))
-					{
-						num++;
-					}
-				}
-			}
-			if (num == m_supportPositions.Count && num2 > m_support)
+				float support = wearNTear.GetSupport();
+				if (support > num2)
+				{
+					num2 = support;
+				}
+				if (!support.Equals(m_supportValue[i]))
+				{
+					break;
+				}
+				num++;
+			}
+			if (num == m_supportPositions.Count && num2 >= m_support)
 			{
 				return;
 			}
@@ -877,16 +878,16 @@
 					{
 						continue;
 					}
-					WearNTear componentInParent2 = collider2.GetComponentInParent<WearNTear>();
-					if (!(componentInParent2 == null))
+					WearNTear componentInParent = collider2.GetComponentInParent<WearNTear>();
+					if (!(componentInParent == null))
 					{
-						if (componentInParent2.m_nview.IsOwner())
+						if (componentInParent.m_nview.IsOwner())
 						{
-							componentInParent2.ClearCachedSupport();
+							componentInParent.ClearCachedSupport();
 						}
-						else if (componentInParent2.m_nview.IsValid())
+						else if (componentInParent.m_nview.IsValid())
 						{
-							componentInParent2.m_nview.InvokeRPC(componentInParent2.m_nview.GetZDO().GetOwner(), "RPC_ClearCachedSupport");
+							componentInParent.m_nview.InvokeRPC(componentInParent.m_nview.GetZDO().GetOwner(), "RPC_ClearCachedSupport");
 						}
 					}
 				}
@@ -904,8 +905,8 @@
 					flag = true;
 					continue;
 				}
-				WearNTear componentInParent3 = collider3.GetComponentInParent<WearNTear>();
-				if (componentInParent3 == null)
+				WearNTear componentInParent2 = collider3.GetComponentInParent<WearNTear>();
+				if (componentInParent2 == null)
 				{
 					bool flag2 = !m_support.Equals(maxSupport);
 					m_support = maxSupport;
@@ -916,19 +917,19 @@
 					}
 					return;
 				}
-				if (!componentInParent3.m_supports)
+				if (!componentInParent2.m_supports)
 				{
 					continue;
 				}
-				float num5 = Vector3.Distance(cOM, componentInParent3.GetCOM()) + 0.1f;
-				float num6 = Vector3.Distance(cOM, componentInParent3.transform.position) + 0.1f;
+				float num5 = Vector3.Distance(cOM, componentInParent2.GetCOM()) + 0.1f;
+				float num6 = Vector3.Distance(cOM, componentInParent2.transform.position) + 0.1f;
 				if (num6 < num5 && !m_forceCorrectCOMCalculation)
 				{
 					num5 = num6;
 				}
-				float support2 = componentInParent3.GetSupport();
+				float support2 = componentInParent2.GetSupport();
 				num3 = Mathf.Max(num3, support2 - horizontalLoss * num5 * support2);
-				Vector3 vector = FindSupportPoint(cOM, componentInParent3, collider3);
+				Vector3 vector = FindSupportPoint(cOM, componentInParent2, collider3);
 				if (vector.y < cOM.y + 0.05f)
 				{
 					Vector3 normalized = (vector - cOM).normalized;
@@ -943,8 +944,9 @@
 					s_tempSupportPoints.Add(vector);
 					s_tempSupportPointValues.Add(item);
 					m_supportColliders.Add(collider3);
+					m_supportWearNTear.Add(componentInParent2);
 					m_supportPositions.Add(collider3.transform.position);
-					m_supportValue.Add(componentInParent3.GetSupport());
+					m_supportValue.Add(componentInParent2.GetSupport());
 				}
 			}
 		}
```

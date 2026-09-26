# `Vine.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+12/-12` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Vine.cs
+++ b/Vine.cs
@@ -248,9 +248,9 @@
 			m_dupeCheck = true;
 			foreach (Vine s_allVine in s_allVines)
 			{
-				if (s_allVine != this && (bool)s_allVine && !m_pickable.CanBePicked() && Vector3.Distance(s_allVine.transform.position, base.transform.position) < 0.01f)
+				if (s_allVine != this && (bool)s_allVine && !m_pickable.CanBePicked() && Vector3.Distance(s_allVine.transform.position, transform.position) < 0.01f)
 				{
-					ZNetScene.instance.Destroy(base.gameObject);
+					ZNetScene.instance.Destroy(gameObject);
 					return false;
 				}
 			}
@@ -391,7 +391,7 @@
 			}
 		}
 		m_sensorBlockCollider.transform.localPosition = Vector3.zero;
-		m_sensorBlockCollider.transform.Translate(offset * m_size + m_sensorBlockCollider.center, base.transform);
+		m_sensorBlockCollider.transform.Translate(offset * m_size + m_sensorBlockCollider.center, transform);
 		int num = Physics.OverlapBoxNonAlloc(m_sensorBlockCollider.transform.position, m_sensorBlockCollider.size / 2f, s_colliders, m_sensorBlockCollider.transform.rotation, s_solidMask);
 		for (int i = 0; i < num; i++)
 		{
@@ -419,7 +419,7 @@
 			return 0;
 		}
 		m_sensorGrow.transform.localPosition = Vector3.zero;
-		m_sensorGrow.transform.Translate(offset * m_size + m_sensorGrow.center, base.transform);
+		m_sensorGrow.transform.Translate(offset * m_size + m_sensorGrow.center, transform);
 		int num2 = 0;
 		foreach (BoxCollider sensorGrowCollider in m_sensorGrowColliders)
 		{
@@ -444,19 +444,19 @@
 			Destructible component = GetComponent<Destructible>();
 			if ((object)component != null)
 			{
-				component.m_destroyedEffect.Create(base.transform.position, base.transform.rotation);
+				component.m_destroyedEffect.Create(transform.position, transform.rotation);
 			}
 			else
 			{
-				GetComponent<WearNTear>()?.m_destroyedEffect.Create(base.transform.position, base.transform.rotation);
-			}
-			ZNetScene.instance.Destroy(base.gameObject);
+				GetComponent<WearNTear>()?.m_destroyedEffect.Create(transform.position, transform.rotation);
+			}
+			ZNetScene.instance.Destroy(gameObject);
 		}
 	}
 
 	private bool IsSupported()
 	{
-		return Physics.OverlapBoxNonAlloc(base.transform.TransformPoint(m_supportCollider.center), m_supportCollider.size / 2f, s_colliders, m_supportCollider.transform.rotation, s_pieceMask) > 0;
+		return Physics.OverlapBoxNonAlloc(transform.TransformPoint(m_supportCollider.center), m_supportCollider.size / 2f, s_colliders, m_supportCollider.transform.rotation, s_pieceMask) > 0;
 	}
 
 	private int GetBranches()
@@ -470,7 +470,7 @@
 		{
 			SetType(VineType.Full);
 		}
-		Vine component = UnityEngine.Object.Instantiate(m_vinePrefab, base.transform.position, base.transform.rotation).GetComponent<Vine>();
+		Vine component = UnityEngine.Object.Instantiate(m_vinePrefab, transform.position, transform.rotation).GetComponent<Vine>();
 		component.transform.Translate(offset * m_size, Space.Self);
 		component.SetType(type);
 		component.name = component.name.Substring(0, Mathf.Min(component.name.Length, 15));
@@ -559,7 +559,7 @@
 		{
 			Terminal.Log("Vine pickable changed, blocking neighbors");
 		}
-		int num = Physics.OverlapBoxNonAlloc(base.transform.TransformPoint(m_berryBlocker.center), m_berryBlocker.size / 2f, s_colliders, m_berryBlocker.transform.rotation, s_solidMask);
+		int num = Physics.OverlapBoxNonAlloc(transform.TransformPoint(m_berryBlocker.center), m_berryBlocker.size / 2f, s_colliders, m_berryBlocker.transform.rotation, s_solidMask);
 		s_vines.Clear();
 		for (int i = 0; i < num; i++)
 		{
@@ -590,7 +590,7 @@
 		{
 			return true;
 		}
-		int num = Physics.OverlapBoxNonAlloc(base.transform.TransformPoint(m_berryBlocker.center), m_berryBlocker.size / 2f, s_colliders, m_berryBlocker.transform.rotation, s_solidMask);
+		int num = Physics.OverlapBoxNonAlloc(transform.TransformPoint(m_berryBlocker.center), m_berryBlocker.size / 2f, s_colliders, m_berryBlocker.transform.rotation, s_solidMask);
 		int num2 = 0;
 		for (int i = 0; i < num; i++)
 		{
```

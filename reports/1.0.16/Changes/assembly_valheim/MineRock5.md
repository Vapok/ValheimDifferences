# `MineRock5.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+12/-12` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MineRock5.cs
+++ b/MineRock5.cs
@@ -90,7 +90,7 @@
 
 	private void Awake()
 	{
-		Collider[] componentsInChildren = base.gameObject.GetComponentsInChildren<Collider>();
+		Collider[] componentsInChildren = gameObject.GetComponentsInChildren<Collider>();
 		m_hitAreas = new List<HitArea>(componentsInChildren.Length);
 		m_extraRenderers = new List<Renderer>();
 		foreach (Collider collider in componentsInChildren)
@@ -125,8 +125,8 @@
 				array = hitArea2.m_meshRenderer.sharedMaterials;
 			}
 		}
-		m_meshFilter = base.gameObject.AddComponent<MeshFilter>();
-		m_meshRenderer = base.gameObject.AddComponent<MeshRenderer>();
+		m_meshFilter = gameObject.AddComponent<MeshFilter>();
+		m_meshRenderer = gameObject.AddComponent<MeshRenderer>();
 		m_meshRenderer.sharedMaterials = array;
 		m_meshFilter.mesh = new Mesh();
 		m_meshFilter.name = "___MineRock5 m_meshFilter";
@@ -209,7 +209,7 @@
 		m_tempInstancesA.Clear();
 		m_tempInstancesB.Clear();
 		Material material = m_meshRenderer.sharedMaterials[0];
-		Matrix4x4 inverse = base.transform.localToWorldMatrix.inverse;
+		Matrix4x4 inverse = transform.localToWorldMatrix.inverse;
 		for (int i = 0; i < m_hitAreas.Count; i++)
 		{
 			HitArea hitArea = m_hitAreas[i];
@@ -262,7 +262,7 @@
 		Renderer[] array = new Renderer[m_extraRenderers.Count + 1];
 		m_extraRenderers.CopyTo(0, array, 0, m_extraRenderers.Count);
 		array[^1] = m_meshRenderer;
-		LODGroup component = base.gameObject.GetComponent<LODGroup>();
+		LODGroup component = gameObject.GetComponent<LODGroup>();
 		LOD[] lODs = component.GetLODs();
 		lODs[0].renderers = array;
 		component.SetLODs(lODs);
@@ -297,7 +297,7 @@
 			for (int i = 0; i < num2; i++)
 			{
 				Transform parent = m_tempColliders[i].transform.parent;
-				if (parent == base.transform || (parent != null && parent.parent == base.transform))
+				if (parent == transform || (parent != null && parent.parent == transform))
 				{
 					m_tempColliderSet.Add(m_tempColliders[i]);
 				}
@@ -320,7 +320,7 @@
 			}
 			if (num == 0)
 			{
-				ZLog.Log("Minerock hit has no collider or invalid hit area on " + base.gameObject.name);
+				ZLog.Log("Minerock hit has no collider or invalid hit area on " + gameObject.name);
 			}
 		}
 		else
@@ -328,7 +328,7 @@
 			int areaIndex2 = GetAreaIndex(hit.m_hitCollider);
 			if (areaIndex2 < 0)
 			{
-				ZLog.Log("Invalid hit area on " + base.gameObject.name);
+				ZLog.Log("Invalid hit area on " + gameObject.name);
 				return;
 			}
 			m_nview.InvokeRPC("RPC_Damage", hit, areaIndex2);
@@ -351,7 +351,7 @@
 			Character attacker = hit.GetAttacker();
 			if ((object)attacker != null)
 			{
-				PrivateArea.OnObjectDamaged(base.transform.position, attacker, flag);
+				PrivateArea.OnObjectDamaged(transform.position, attacker, flag);
 			}
 		}
 	}
@@ -515,7 +515,7 @@
 		{
 			hitArea.m_supported = false;
 		}
-		Vector3 position = base.transform.position;
+		Vector3 position = transform.position;
 		for (int i = 0; i < 3; i++)
 		{
 			foreach (HitArea hitArea2 in m_hitAreas)
@@ -561,14 +561,14 @@
 					}
 				}
 			}
-			return c.transform.position.y < base.transform.position.y;
+			return c.transform.position.y < transform.position.y;
 		}
 		return true;
 	}
 
 	private void SetupColliders()
 	{
-		Vector3 position = base.transform.position;
+		Vector3 position = transform.position;
 		foreach (HitArea hitArea in m_hitAreas)
 		{
 			hitArea.m_bound.m_rot = Quaternion.identity;
```

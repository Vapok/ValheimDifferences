# `InstanceRenderer.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+0/-41` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `AddInstance() [Method Body Modified]`
- `Clear() [Method Body Modified]`
- `CustomUpdate() [Method Body Modified]`
- `Resize() [Method Body Modified]`
- `SetInstance() [Method Body Modified]`
- `SetInstancesBillboard() [Method Body Modified]`
- `UpdateBounds() [Method Body Modified]`
- `UpdateBounds() [Method Removed]`
- `m_dirtyBounds [Field Removed, was bool]`
- `m_frustumCull [Field Removed, was bool]`
- `private void UpdateBounds()`

---

## 📝 Code Diff

```diff
--- a/InstanceRenderer.cs
+++ b/InstanceRenderer.cs
@@ -10,8 +10,6 @@
 
 	public Vector3 m_scale = Vector3.one;
 
-	public bool m_frustumCull = true;
-
 	public bool m_useLod;
 
 	public bool m_useXZLodDistance = true;
@@ -21,8 +19,6 @@
 	public float m_lodMaxDistance = 20f;
 
 	public ShadowCastingMode m_shadowCasting;
-
-	private bool m_dirtyBounds = true;
 
 	private BoundingSphere m_bounds;
 
@@ -59,17 +55,6 @@
 		{
 			return;
 		}
-		if (m_frustumCull)
-		{
-			if (m_dirtyBounds)
-			{
-				UpdateBounds();
-			}
-			if (!Utils.InsideMainCamera(m_bounds))
-			{
-				return;
-			}
-		}
 		if (m_useLod)
 		{
 			float num = (m_useXZLodDistance ? Utils.DistanceXZ(mainCamera.transform.position, transform.position) : Vector3.Distance(mainCamera.transform.position, transform.position));
@@ -97,26 +82,6 @@
 		}
 	}
 
-	private void UpdateBounds()
-	{
-		m_dirtyBounds = false;
-		Vector3 vector = new Vector3(9999999f, 9999999f, 9999999f);
-		Vector3 vector2 = new Vector3(-9999999f, -9999999f, -9999999f);
-		float magnitude = m_mesh.bounds.extents.magnitude;
-		for (int i = 0; i < m_instanceCount; i++)
-		{
-			Matrix4x4 matrix4x = m_instances[i];
-			Vector3 vector3 = new Vector3(matrix4x[0, 3], matrix4x[1, 3], matrix4x[2, 3]);
-			Vector3 lossyScale = matrix4x.lossyScale;
-			float num = Mathf.Max(Mathf.Max(lossyScale.x, lossyScale.y), lossyScale.z);
-			Vector3 vector4 = new Vector3(num * magnitude, num * magnitude, num * magnitude);
-			vector2 = Vector3.Max(vector2, vector3 + vector4);
-			vector = Vector3.Min(vector, vector3 - vector4);
-		}
-		m_bounds.position = (vector2 + vector) * 0.5f;
-		m_bounds.radius = Vector3.Distance(vector2, m_bounds.position);
-	}
-
 	public void AddInstance(Vector3 pos, Quaternion rot, float scale)
 	{
 		Matrix4x4 m = Matrix4x4.TRS(pos, rot, m_scale * scale);
@@ -135,27 +100,23 @@
 		{
 			m_instances[m_instanceCount] = m;
 			m_instanceCount++;
-			m_dirtyBounds = true;
 		}
 	}
 
 	public void Clear()
 	{
 		m_instanceCount = 0;
-		m_dirtyBounds = true;
 	}
 
 	public void SetInstance(int index, Vector3 pos, Quaternion rot, float scale)
 	{
 		Matrix4x4 matrix4x = Matrix4x4.TRS(pos, rot, m_scale * scale);
 		m_instances[index] = matrix4x;
-		m_dirtyBounds = true;
 	}
 
 	private void Resize(int instances)
 	{
 		m_instanceCount = instances;
-		m_dirtyBounds = true;
 	}
 
 	public void SetInstances(List<Transform> transforms, bool faceCamera = false)
@@ -166,7 +127,6 @@
 			Transform transform = transforms[i];
 			m_instances[i] = Matrix4x4.TRS(transform.position, transform.rotation, transform.lossyScale);
 		}
-		m_dirtyBounds = true;
 	}
 
 	public void SetInstancesBillboard(List<Vector4> points)
@@ -184,7 +144,6 @@
 				Quaternion q = Quaternion.LookRotation(forward);
 				m_instances[i] = Matrix4x4.TRS(pos, q, w * m_scale);
 			}
-			m_dirtyBounds = true;
 		}
 	}
 
```

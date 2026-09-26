# `InstanceRenderer.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/InstanceRenderer.cs
+++ b/InstanceRenderer.cs
@@ -72,7 +72,7 @@
 		}
 		if (m_useLod)
 		{
-			float num = (m_useXZLodDistance ? Utils.DistanceXZ(mainCamera.transform.position, base.transform.position) : Vector3.Distance(mainCamera.transform.position, base.transform.position));
+			float num = (m_useXZLodDistance ? Utils.DistanceXZ(mainCamera.transform.position, transform.position) : Vector3.Distance(mainCamera.transform.position, transform.position));
 			int num2 = (int)((1f - Utils.LerpStep(m_lodMinDistance, m_lodMaxDistance, num)) * (float)m_instanceCount);
 			float maxDelta = deltaTime * (float)m_instanceCount;
 			m_lodCount = Mathf.MoveTowards(m_lodCount, num2, maxDelta);
```

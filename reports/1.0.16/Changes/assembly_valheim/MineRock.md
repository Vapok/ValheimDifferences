# `MineRock.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MineRock.cs
+++ b/MineRock.cs
@@ -35,7 +35,7 @@
 
 	private void Start()
 	{
-		m_hitAreas = ((m_areaRoot != null) ? m_areaRoot.GetComponentsInChildren<Collider>() : base.gameObject.GetComponentsInChildren<Collider>());
+		m_hitAreas = ((m_areaRoot != null) ? m_areaRoot.GetComponentsInChildren<Collider>() : gameObject.GetComponentsInChildren<Collider>());
 		if ((bool)m_baseModel)
 		{
 			m_areaMeshes = new MeshRenderer[m_hitAreas.Length][];
@@ -110,7 +110,7 @@
 		int areaIndex = GetAreaIndex(hit.m_hitCollider);
 		if (areaIndex == -1)
 		{
-			ZLog.Log("Invalid hit area on " + base.gameObject.name);
+			ZLog.Log("Invalid hit area on " + gameObject.name);
 			return;
 		}
 		ZLog.Log("Hit mine rock area " + areaIndex);
```

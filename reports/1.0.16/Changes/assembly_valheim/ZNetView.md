# `ZNetView.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+16/-16` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZNetView.cs
+++ b/ZNetView.cs
@@ -50,7 +50,7 @@
 		m_body = GetComponent<Rigidbody>();
 		if (m_useInitZDO && m_initZDO == null)
 		{
-			ZLog.LogWarning("Double ZNetview when initializing object " + base.gameObject.name);
+			ZLog.LogWarning("Double ZNetview when initializing object " + gameObject.name);
 		}
 		if (m_initZDO != null)
 		{
@@ -69,14 +69,14 @@
 				Vector3 vec = m_zdo.GetVec3(ZDOVars.s_scaleHash, Vector3.zero);
 				if (vec != Vector3.zero)
 				{
-					base.transform.localScale = vec;
+					transform.localScale = vec;
 				}
 				else
 				{
-					float num = m_zdo.GetFloat(ZDOVars.s_scaleScalarHash, base.transform.localScale.x);
-					if (!base.transform.localScale.x.Equals(num))
+					float num = m_zdo.GetFloat(ZDOVars.s_scaleScalarHash, transform.localScale.x);
+					if (!transform.localScale.x.Equals(num))
 					{
-						base.transform.localScale = new Vector3(num, num, num);
+						transform.localScale = new Vector3(num, num, num);
 					}
 				}
 			}
@@ -88,12 +88,12 @@
 		else
 		{
 			int stableHashCode = GetPrefabName().GetStableHashCode();
-			m_zdo = ZDOMan.instance.CreateNewZDO(base.transform.position, stableHashCode);
+			m_zdo = ZDOMan.instance.CreateNewZDO(transform.position, stableHashCode);
 			m_zdo.Persistent = m_persistent;
 			m_zdo.Type = m_type;
 			m_zdo.Distant = m_distant;
 			m_zdo.SetPrefab(stableHashCode);
-			m_zdo.SetRotation(base.transform.rotation);
+			m_zdo.SetRotation(transform.rotation);
 			if (m_syncInitialScale)
 			{
 				SyncScale();
@@ -110,9 +110,9 @@
 
 	public void SetLocalScale(Vector3 scale)
 	{
-		if (!(base.transform.localScale == scale))
-		{
-			base.transform.localScale = scale;
+		if (!(transform.localScale == scale))
+		{
+			transform.localScale = scale;
 			if (m_zdo != null && m_syncInitialScale && IsOwner())
 			{
 				SyncScale();
@@ -122,9 +122,9 @@
 
 	private void SyncScale()
 	{
-		if (!m_lastLocalScale.Equals(base.transform.localScale))
-		{
-			m_lastLocalScale = base.transform.localScale;
+		if (!m_lastLocalScale.Equals(transform.localScale))
+		{
+			m_lastLocalScale = transform.localScale;
 			m_zdo.Set(ZDOVars.s_scaleHash, m_lastLocalScale);
 		}
 	}
@@ -149,7 +149,7 @@
 		{
 			return;
 		}
-		base.gameObject.GetComponentsInChildren(m_tempComponents);
+		gameObject.GetComponentsInChildren(m_tempComponents);
 		foreach (MonoBehaviour tempComponent in m_tempComponents)
 		{
 			string text = tempComponent.GetType().Name;
@@ -216,12 +216,12 @@
 
 	private string GetPrefabName()
 	{
-		return Utils.GetPrefabName(base.gameObject);
+		return Utils.GetPrefabName(gameObject);
 	}
 
 	public void Destroy()
 	{
-		ZNetScene.instance.Destroy(base.gameObject);
+		ZNetScene.instance.Destroy(gameObject);
 	}
 
 	public bool IsOwner()
```

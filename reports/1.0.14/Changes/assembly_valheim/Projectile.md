# `Projectile.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Projectile.cs
+++ b/Projectile.cs
@@ -702,13 +702,16 @@
 		{
 			m_didHit = true;
 			base.transform.position = hitPoint;
-			m_nview.InvokeRPC("RPC_OnHit");
+			if (m_nview.IsValid())
+			{
+				m_nview.InvokeRPC("RPC_OnHit");
+			}
 			m_ttl = m_stayTTL;
 		}
 		if ((bool)collider && collider.attachedRigidbody != null)
 		{
 			ZNetView componentInParent = collider.gameObject.GetComponentInParent<ZNetView>();
-			if ((bool)componentInParent && (m_attachToClosestBone || m_attachToRigidBody))
+			if ((bool)componentInParent && componentInParent.IsValid() && (m_attachToClosestBone || m_attachToRigidBody))
 			{
 				m_nview.InvokeRPC("RPC_Attach", componentInParent.GetZDO().m_uid);
 			}
```

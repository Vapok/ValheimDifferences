# `ZSyncTransform.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+34/-34` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZSyncTransform.cs
+++ b/ZSyncTransform.cs
@@ -77,7 +77,7 @@
 		m_character = GetComponent<Character>();
 		if (m_nview.GetZDO() == null)
 		{
-			base.enabled = false;
+			enabled = false;
 			return;
 		}
 		if ((bool)m_body)
@@ -115,7 +115,7 @@
 	{
 		if (!m_body)
 		{
-			return base.transform.position;
+			return transform.position;
 		}
 		return m_body.position;
 	}
@@ -135,12 +135,12 @@
 			bool flag3 = false;
 			if (m_syncPosition)
 			{
-				base.transform.position = zDO.GetPosition();
+				transform.position = zDO.GetPosition();
 				flag3 = true;
 			}
 			if (m_syncRotation)
 			{
-				base.transform.rotation = zDO.GetRotation();
+				transform.rotation = zDO.GetRotation();
 				flag3 = true;
 			}
 			if (m_syncBodyVelocity && (bool)m_body)
@@ -153,26 +153,26 @@
 				Physics.SyncTransforms();
 			}
 		}
-		if (base.transform.position.y < -5000f)
+		if (transform.position.y < -5000f)
 		{
 			if ((bool)m_body)
 			{
 				m_body.linearVelocity = Vector3.zero;
 			}
-			ZLog.Log("Object fell out of world:" + base.gameObject.name);
-			float groundHeight = ZoneSystem.instance.GetGroundHeight(base.transform.position);
-			Vector3 position = base.transform.position;
+			ZLog.Log("Object fell out of world:" + gameObject.name);
+			float groundHeight = ZoneSystem.instance.GetGroundHeight(transform.position);
+			Vector3 position = transform.position;
 			position.y = groundHeight + 1f;
-			base.transform.position = position;
+			transform.position = position;
 			if ((bool)m_body)
 			{
 				Physics.SyncTransforms();
 			}
 			if ((bool)GetComponent<FloatingTerrain>())
 			{
-				Rigidbody body = FloatingTerrain.GetBody(base.gameObject);
+				Rigidbody body = FloatingTerrain.GetBody(gameObject);
 				body.linearVelocity = Vector3.zero;
-				body.transform.position = base.transform.position;
+				body.transform.position = transform.position;
 			}
 			return;
 		}
@@ -223,18 +223,18 @@
 				m_tempParentCached = m_tempParent;
 			}
 		}
-		if (m_syncRotation && base.transform.hasChanged)
-		{
-			Quaternion rotation = (m_body ? m_body.rotation : base.transform.rotation);
+		if (m_syncRotation && transform.hasChanged)
+		{
+			Quaternion rotation = (m_body ? m_body.rotation : transform.rotation);
 			zDO.SetRotation(rotation);
 		}
-		if (m_syncScale && base.transform.hasChanged)
-		{
-			if (m_lastLocalScale.Equals(base.transform.localScale))
+		if (m_syncScale && transform.hasChanged)
+		{
+			if (m_lastLocalScale.Equals(transform.localScale))
 			{
 				return;
 			}
-			m_lastLocalScale = base.transform.localScale;
+			m_lastLocalScale = transform.localScale;
 			zDO.Set(ZDOVars.s_scaleHash, m_lastLocalScale);
 		}
 		if ((bool)m_body)
@@ -246,7 +246,7 @@
 			}
 			m_body.useGravity = m_useGravity;
 		}
-		base.transform.hasChanged = false;
+		transform.hasChanged = false;
 	}
 
 	private bool GetRelativePosition(ZDO zdo, out ZDOID parent, out string attachJoint, out Vector3 relativePos, out Quaternion relativeRot, out Vector3 relativeVel)
@@ -255,15 +255,15 @@
 		{
 			return m_character.GetRelativePosition(out parent, out attachJoint, out relativePos, out relativeRot, out relativeVel);
 		}
-		if ((bool)base.transform.parent)
-		{
-			ZNetView zNetView = (base.transform.parent ? base.transform.parent.GetComponent<ZNetView>() : null);
+		if ((bool)transform.parent)
+		{
+			ZNetView zNetView = (transform.parent ? transform.parent.GetComponent<ZNetView>() : null);
 			if ((bool)zNetView && zNetView.IsValid())
 			{
 				parent = zNetView.GetZDO().m_uid;
 				attachJoint = "";
-				relativePos = base.transform.localPosition;
-				relativeRot = base.transform.localRotation;
+				relativePos = transform.localPosition;
+				relativeRot = transform.localRotation;
 				relativeVel = Vector3.zero;
 				return true;
 			}
@@ -428,9 +428,9 @@
 			if (m_syncRotation && !usedLocalRotation)
 			{
 				Quaternion rotation2 = zDO.GetRotation();
-				if (Quaternion.Angle(base.transform.rotation, rotation2) > 0.001f)
-				{
-					base.transform.rotation = Quaternion.Slerp(base.transform.rotation, rotation2, 0.5f);
+				if (Quaternion.Angle(transform.rotation, rotation2) > 0.001f)
+				{
+					transform.rotation = Quaternion.Slerp(transform.rotation, rotation2, 0.5f);
 				}
 			}
 			if ((bool)m_body)
@@ -465,13 +465,13 @@
 		Vector3 vec3 = zDO.GetVec3(ZDOVars.s_scaleHash, Vector3.zero);
 		if (vec3 != Vector3.zero)
 		{
-			base.transform.localScale = vec3;
-			return;
-		}
-		float num = zDO.GetFloat(ZDOVars.s_scaleScalarHash, base.transform.localScale.x);
-		if (!base.transform.localScale.x.Equals(num))
-		{
-			base.transform.localScale = new Vector3(num, num, num);
+			transform.localScale = vec3;
+			return;
+		}
+		float num = zDO.GetFloat(ZDOVars.s_scaleScalarHash, transform.localScale.x);
+		if (!transform.localScale.x.Equals(num))
+		{
+			transform.localScale = new Vector3(num, num, num);
 		}
 	}
 
```

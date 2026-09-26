# `StaticPhysics.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+17/-17` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/StaticPhysics.cs
+++ b/StaticPhysics.cs
@@ -38,7 +38,7 @@
 
 	public override void SUpdate(float time, Vector2s referenceZone)
 	{
-		if (!m_falling && ShouldUpdate(time) && !ZNetScene.OutsideActiveArea(base.transform.position, referenceZone))
+		if (!m_falling && ShouldUpdate(time) && !ZNetScene.OutsideActiveArea(transform.position, referenceZone))
 		{
 			if (m_fall)
 			{
@@ -54,7 +54,7 @@
 	private void CheckFall()
 	{
 		float fallHeight = GetFallHeight();
-		if (base.transform.position.y > fallHeight + 0.05f)
+		if (transform.position.y > fallHeight + 0.05f)
 		{
 			Fall();
 		}
@@ -64,62 +64,62 @@
 	{
 		if (m_checkSolids)
 		{
-			if (ZoneSystem.instance.GetSolidHeight(base.transform.position, m_fallCheckRadius, out var height, base.transform))
+			if (ZoneSystem.instance.GetSolidHeight(transform.position, m_fallCheckRadius, out var height, transform))
 			{
 				return height;
 			}
-			return base.transform.position.y;
+			return transform.position.y;
 		}
-		if (ZoneSystem.instance.GetGroundHeight(base.transform.position, out var height2))
+		if (ZoneSystem.instance.GetGroundHeight(transform.position, out var height2))
 		{
 			return height2;
 		}
-		return base.transform.position.y;
+		return transform.position.y;
 	}
 
 	private void Fall()
 	{
 		m_falling = true;
-		base.gameObject.isStatic = false;
+		gameObject.isStatic = false;
 		InvokeRepeating("FallUpdate", 0.05f, 0.05f);
 	}
 
 	private void FallUpdate()
 	{
 		float fallHeight = GetFallHeight();
-		Vector3 position = base.transform.position;
+		Vector3 position = transform.position;
 		position.y -= 0.2f;
 		if (position.y <= fallHeight)
 		{
 			position.y = fallHeight;
 			StopFalling();
 		}
-		base.transform.position = position;
+		transform.position = position;
 		if ((bool)m_nview && m_nview.IsValid() && m_nview.IsOwner())
 		{
-			m_nview.GetZDO().SetPosition(base.transform.position);
+			m_nview.GetZDO().SetPosition(transform.position);
 		}
 	}
 
 	private void StopFalling()
 	{
-		base.gameObject.isStatic = true;
+		gameObject.isStatic = true;
 		m_falling = false;
 		CancelInvoke("FallUpdate");
 	}
 
 	private void PushUp()
 	{
-		if (ZoneSystem.instance.GetGroundHeight(base.transform.position, out var height) && base.transform.position.y < height - 0.05f)
+		if (ZoneSystem.instance.GetGroundHeight(transform.position, out var height) && transform.position.y < height - 0.05f)
 		{
-			base.gameObject.isStatic = false;
-			Vector3 position = base.transform.position;
+			gameObject.isStatic = false;
+			Vector3 position = transform.position;
 			position.y = height;
-			base.transform.position = position;
-			base.gameObject.isStatic = true;
+			transform.position = position;
+			gameObject.isStatic = true;
 			if ((bool)m_nview && m_nview.IsValid() && m_nview.IsOwner())
 			{
-				m_nview.GetZDO().SetPosition(base.transform.position);
+				m_nview.GetZDO().SetPosition(transform.position);
 			}
 		}
 	}
```

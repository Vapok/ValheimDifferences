# `Catapult.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Catapult.cs
+++ b/Catapult.cs
@@ -228,7 +228,7 @@
 			{
 				return;
 			}
-			Vector3 normalized = (m_forceVector.transform.position - base.transform.position).normalized;
+			Vector3 normalized = (m_forceVector.transform.position - transform.position).normalized;
 			foreach (Character launchCharacter in m_launchCharacters)
 			{
 				launchCharacter.ForceJump(normalized * m_preLaunchForce);
@@ -298,10 +298,10 @@
 		m_movingLegs = true;
 		if (m_lockedLegs)
 		{
-			m_legDownEffect.Create(base.transform.position, base.transform.rotation);
+			m_legDownEffect.Create(transform.position, transform.rotation);
 			return;
 		}
-		m_legUpEffect.Create(base.transform.position, base.transform.rotation);
+		m_legUpEffect.Create(transform.position, transform.rotation);
 		m_rigidBody.mass = m_baseMass;
 	}
 
@@ -409,7 +409,7 @@
 
 	private void ShootProjectile()
 	{
-		Vector3 vector = m_forceVector.transform.position - base.transform.position;
+		Vector3 vector = m_forceVector.transform.position - transform.position;
 		Vector3 vector2 = vector.normalized;
 		m_shootReleaseEffect.Create(m_loadPoint.transform.position, Quaternion.LookRotation(vector2));
 		Projectile projectile = m_projectile;
@@ -517,7 +517,7 @@
 		foreach (Character launchCharacter in m_launchCharacters)
 		{
 			launchCharacter.ReleaseTempParent();
-			Vector3 normalized = (m_forceVector.transform.position - base.transform.position).normalized;
+			Vector3 normalized = (m_forceVector.transform.position - transform.position).normalized;
 			launchCharacter.ForceJump(normalized * m_launchForce);
 			launchCharacter.StandUpOnNextGround();
 		}
```

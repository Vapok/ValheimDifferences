# `Aoe.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+18/-18` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Aoe.cs
+++ b/Aoe.cs
@@ -321,8 +321,8 @@
 		}
 		if (m_owner != null && m_attachToCaster)
 		{
-			base.transform.position = m_owner.transform.TransformPoint(m_offset);
-			base.transform.rotation = m_owner.transform.rotation * m_localRot;
+			transform.position = m_owner.transform.TransformPoint(m_offset);
+			transform.rotation = m_owner.transform.rotation * m_localRot;
 		}
 		if (m_activationTimer > 0f)
 		{
@@ -342,7 +342,7 @@
 			m_chainDelay -= fixedDeltaTime;
 			if (m_chainDelay <= 0f && Random.value < m_chainStartChance)
 			{
-				Vector3 position = base.transform.position;
+				Vector3 position = transform.position;
 				FindHits();
 				SortHits();
 				int num = Random.Range(m_chainMinTargets, m_chainMaxTargets + 1);
@@ -381,7 +381,7 @@
 								}
 							}
 							num--;
-							float num2 = Vector3.Distance(position2, base.transform.position);
+							float num2 = Vector3.Distance(position2, transform.position);
 							GameObject[] array = m_chainEffects.Create(position + Vector3.up, Quaternion.LookRotation(position.DirTo(position2 + Vector3.up)));
 							for (int j = 0; j < array.Length; j++)
 							{
@@ -416,7 +416,7 @@
 
 	public void Initiate()
 	{
-		m_initiateEffect.Create(base.transform.position, Quaternion.identity);
+		m_initiateEffect.Create(transform.position, Quaternion.identity);
 		CheckHits();
 	}
 
@@ -451,7 +451,7 @@
 	private void FindHits()
 	{
 		m_hitList.Clear();
-		int num = ((m_useCollider != null) ? Physics.OverlapBoxNonAlloc(base.transform.position + m_useCollider.center, m_useCollider.size / 2f, s_hits, base.transform.rotation, m_rayMask) : Physics.OverlapSphereNonAlloc(base.transform.position, m_radius, s_hits, m_rayMask));
+		int num = ((m_useCollider != null) ? Physics.OverlapBoxNonAlloc(transform.position + m_useCollider.center, m_useCollider.size / 2f, s_hits, transform.rotation, m_rayMask) : Physics.OverlapSphereNonAlloc(transform.position, m_radius, s_hits, m_rayMask));
 		s_hitList.Clear();
 		for (int i = 0; i < num; i++)
 		{
@@ -510,7 +510,7 @@
 
 	private void SortHits()
 	{
-		s_hitList.Sort((Collider a, Collider b) => Vector3.Distance(a.transform.position, base.transform.position).CompareTo(Vector3.Distance(b.transform.position, base.transform.position)));
+		s_hitList.Sort((Collider a, Collider b) => Vector3.Distance(a.transform.position, transform.position).CompareTo(Vector3.Distance(b.transform.position, transform.position)));
 	}
 
 	public void Setup(Character owner, Vector3 velocity, float hitNoise, HitData hitData, ItemDrop.ItemData item, ItemDrop.ItemData ammo)
@@ -524,8 +524,8 @@
 		}
 		if (m_attachToCaster && owner != null)
 		{
-			m_offset = owner.transform.InverseTransformPoint(base.transform.position);
-			m_localRot = Quaternion.Inverse(owner.transform.rotation) * base.transform.rotation;
+			m_offset = owner.transform.InverseTransformPoint(transform.position);
+			m_localRot = Quaternion.Inverse(owner.transform.rotation) * transform.rotation;
 		}
 		if (hitData != null && m_useAttackSettings)
 		{
@@ -576,7 +576,7 @@
 		{
 			if (!m_useTriggers)
 			{
-				ZLog.LogWarning("AOE got OnTriggerStay but trigger damage is disabled in " + base.gameObject.name);
+				ZLog.LogWarning("AOE got OnTriggerStay but trigger damage is disabled in " + gameObject.name);
 			}
 			else if (ShouldHit(collider))
 			{
@@ -603,7 +603,7 @@
 		float num2 = 1f;
 		if (m_scaleDamageByDistance)
 		{
-			num2 = m_distanceScaleCurve.Evaluate(Mathf.Clamp01(Vector3.Distance(gameObject.transform.position, base.transform.position) / m_radius));
+			num2 = m_distanceScaleCurve.Evaluate(Mathf.Clamp01(Vector3.Distance(gameObject.transform.position, transform.position) / m_radius));
 		}
 		IDestructible component = gameObject.GetComponent<IDestructible>();
 		if (component != null)
@@ -625,14 +625,14 @@
 		Heightmap component2 = gameObject.GetComponent<Heightmap>();
 		if ((object)component2 != null)
 		{
-			FootStep.GroundMaterial groundMaterial = component2.GetGroundMaterial(Vector3.up, base.transform.position, m_groundLavaValue);
-			FootStep.GroundMaterial groundMaterial2 = component2.GetGroundMaterial(Vector3.up, base.transform.position);
+			FootStep.GroundMaterial groundMaterial = component2.GetGroundMaterial(Vector3.up, transform.position, m_groundLavaValue);
+			FootStep.GroundMaterial groundMaterial2 = component2.GetGroundMaterial(Vector3.up, transform.position);
 			FootStep.GroundMaterial groundMaterial3 = ((m_groundLavaValue >= 0f) ? groundMaterial : groundMaterial2);
 			if ((bool)m_spawnOnHitTerrain && (m_spawnOnGroundType == FootStep.GroundMaterial.Everything || m_spawnOnGroundType.HasFlag(groundMaterial3)) && (!m_hitTerrainOnlyOnce || !m_hasHitTerrain))
 			{
 				m_hasHitTerrain = true;
 				int num3 = ((m_multiSpawnMin == 0) ? 1 : Random.Range(m_multiSpawnMin, m_multiSpawnMax));
-				Vector3 position = base.transform.position;
+				Vector3 position = transform.position;
 				for (int i = 0; i < num3; i++)
 				{
 					GameObject gameObject2 = Attack.SpawnOnHitTerrain(position, m_spawnOnHitTerrain, m_owner, m_hitNoise, null, null, m_randomRotation);
@@ -673,7 +673,7 @@
 			{
 				float num6 = Random.Range(m_launchForceMinMax.x, m_launchForceMinMax.y);
 				num6 *= num2;
-				Vector3 a = hitPoint.DirTo(base.transform.position);
+				Vector3 a = hitPoint.DirTo(transform.position);
 				if (m_launchForceUpFactor > 0f)
 				{
 					a = Vector3.Slerp(a, Vector3.up, m_launchForceUpFactor);
@@ -687,13 +687,13 @@
 			return false;
 		}
 		bool flag2 = (component is Destructible destructible && destructible.m_spawnWhenDestroyed != null) || (object)gameObject.GetComponent<MineRock5>() != null;
-		Vector3 dir = (m_attackForceForward ? base.transform.forward : (hitPoint - base.transform.position).normalized);
+		Vector3 dir = (m_attackForceForward ? transform.forward : (hitPoint - transform.position).normalized);
 		HitData hitData = new HitData();
 		hitData.m_hitCollider = collider;
 		hitData.m_damage = GetDamage();
 		hitData.m_pushForce = m_attackForce * num * num2;
 		hitData.m_backstabBonus = m_backstabBonus;
-		hitData.m_point = (flag2 ? base.transform.position : hitPoint);
+		hitData.m_point = (flag2 ? transform.position : hitPoint);
 		hitData.m_dir = dir;
 		hitData.m_statusEffectHash = GetStatusEffect(character);
 		Character owner = m_owner;
@@ -715,7 +715,7 @@
 		if (m_knockBackForce > 0f)
 		{
 			Character component3 = gameObject.GetComponent<Character>();
-			component3?.ApplyPushback((component3.transform.position - base.transform.position).normalized, m_knockBackForce);
+			component3?.ApplyPushback((component3.transform.position - transform.position).normalized, m_knockBackForce);
 		}
 		if (Terminal.m_showTests && Terminal.m_testList.ContainsKey("damage"))
 		{
```

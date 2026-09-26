# `TreeBase.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+13/-13` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/TreeBase.cs
+++ b/TreeBase.cs
@@ -76,9 +76,9 @@
 
 	private IEnumerator GrowAnimation()
 	{
-		GameObject animatedTrunk = Object.Instantiate(m_trunk, m_trunk.transform.position, m_trunk.transform.rotation, base.transform);
+		GameObject animatedTrunk = Object.Instantiate(m_trunk, m_trunk.transform.position, m_trunk.transform.rotation, transform);
 		animatedTrunk.isStatic = false;
-		LODGroup component = base.transform.GetComponent<LODGroup>();
+		LODGroup component = transform.GetComponent<LODGroup>();
 		if ((bool)component)
 		{
 			component.fadeMode = LODFadeMode.None;
@@ -94,7 +94,7 @@
 		m_trunk.SetActive(value: true);
 		if (m_nview.IsOwner())
 		{
-			m_respawnEffect.Create(base.transform.position, base.transform.rotation, base.transform);
+			m_respawnEffect.Create(transform.position, transform.rotation, transform);
 		}
 	}
 
@@ -133,8 +133,8 @@
 		if (!flag2)
 		{
 			ZDOID gamepadEffectsExclusiveToPlayer = (hit.GetAttacker() ? hit.GetAttacker().GetZDOID() : ZDOID.None);
-			m_hitEffect.Create(hit.m_point, Quaternion.identity, base.transform, 1f, -1, gamepadEffectsExclusiveToPlayer);
-			Player closestPlayer = Player.GetClosestPlayer(base.transform.position, 10f);
+			m_hitEffect.Create(hit.m_point, Quaternion.identity, transform, 1f, -1, gamepadEffectsExclusiveToPlayer);
+			Player closestPlayer = Player.GetClosestPlayer(transform.position, 10f);
 			if ((bool)closestPlayer)
 			{
 				closestPlayer.AddNoise(100f);
@@ -146,23 +146,23 @@
 		}
 		if ((bool)m_spawnOnDamage)
 		{
-			Object.Instantiate(m_spawnOnDamage, m_spawnOnDamageSpawnPoint ? m_spawnOnDamageSpawnPoint.transform.position : base.transform.position, Quaternion.identity).GetComponent<IProjectile>()?.Setup(null, m_spawnOnDamageProjVelocity, 0f, null, null, null);
+			Object.Instantiate(m_spawnOnDamage, m_spawnOnDamageSpawnPoint ? m_spawnOnDamageSpawnPoint.transform.position : transform.position, Quaternion.identity).GetComponent<IProjectile>()?.Setup(null, m_spawnOnDamageProjVelocity, 0f, null, null, null);
 		}
 		if (!(num <= 0f))
 		{
 			return;
 		}
-		m_destroyedEffect.Create(base.transform.position, base.transform.rotation, base.transform);
+		m_destroyedEffect.Create(transform.position, transform.rotation, transform);
 		SpawnLog(hit.m_dir);
 		List<GameObject> dropList = m_dropWhenDestroyed.GetDropList();
 		for (int i = 0; i < dropList.Count; i++)
 		{
 			Vector2 vector = Random.insideUnitCircle * 0.5f;
-			Vector3 position = base.transform.position + Vector3.up * m_spawnYOffset + new Vector3(vector.x, m_spawnYStep * (float)i, vector.y);
+			Vector3 position = transform.position + Vector3.up * m_spawnYOffset + new Vector3(vector.x, m_spawnYStep * (float)i, vector.y);
 			Quaternion rotation = Quaternion.Euler(0f, Random.Range(0, 360), 0f);
 			Object.Instantiate(dropList[i], position, rotation);
 		}
-		base.gameObject.SetActive(value: false);
+		gameObject.SetActive(value: false);
 		m_nview.Destroy();
 		if (hit.GetAttacker() == Player.m_localPlayer)
 		{
@@ -225,11 +225,11 @@
 	private void SpawnLog(Vector3 hitDir)
 	{
 		GameObject gameObject = Object.Instantiate(m_logPrefab, m_logSpawnPoint.position, m_logSpawnPoint.rotation);
-		gameObject.GetComponent<ZNetView>().SetLocalScale(base.transform.localScale);
+		gameObject.GetComponent<ZNetView>().SetLocalScale(transform.localScale);
 		Rigidbody component = gameObject.GetComponent<Rigidbody>();
-		component.mass *= base.transform.localScale.x;
+		component.mass *= transform.localScale.x;
 		component.ResetInertiaTensor();
-		component.AddForceAtPosition(hitDir * 0.2f * component.mass, gameObject.transform.position + Vector3.up * 4f * base.transform.localScale.y, ForceMode.Impulse);
+		component.AddForceAtPosition(hitDir * 0.2f * component.mass, gameObject.transform.position + Vector3.up * 4f * transform.localScale.y, ForceMode.Impulse);
 		ImpactEffect component2 = gameObject.GetComponent<ImpactEffect>();
 		if (component2 != null)
 		{
@@ -241,7 +241,7 @@
 		}
 		if ((bool)m_stubPrefab)
 		{
-			Object.Instantiate(m_stubPrefab, base.transform.position, base.transform.rotation).GetComponent<ZNetView>().SetLocalScale(base.transform.localScale);
+			Object.Instantiate(m_stubPrefab, transform.position, transform.rotation).GetComponent<ZNetView>().SetLocalScale(transform.localScale);
 		}
 	}
 }
```

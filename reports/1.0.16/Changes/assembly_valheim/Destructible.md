# `Destructible.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+11/-11` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Destructible.cs
+++ b/Destructible.cs
@@ -130,14 +130,14 @@
 		if (m_triggerPrivateArea && (bool)attacker)
 		{
 			bool destroyed = num <= 0f;
-			PrivateArea.OnObjectDamaged(base.transform.position, attacker, destroyed);
+			PrivateArea.OnObjectDamaged(transform.position, attacker, destroyed);
 		}
 		ZDOID gamepadEffectsExclusiveToPlayer = (attacker ? attacker.GetZDOID() : ZDOID.None);
-		m_hitEffect.Create(hit.m_point, Quaternion.identity, base.transform, 1f, -1, gamepadEffectsExclusiveToPlayer);
-		m_hitEffect.Create(hit.m_point, Quaternion.identity, base.transform);
+		m_hitEffect.Create(hit.m_point, Quaternion.identity, transform, 1f, -1, gamepadEffectsExclusiveToPlayer);
+		m_hitEffect.Create(hit.m_point, Quaternion.identity, transform);
 		if (m_hitEffectBigThreshold > 0f)
 		{
-			m_hitEffectBig.Create(hit.m_point, Quaternion.identity, base.transform);
+			m_hitEffectBig.Create(hit.m_point, Quaternion.identity, transform);
 		}
 		if (m_hitEffectBuildUpThreshold > 0f)
 		{
@@ -145,7 +145,7 @@
 			if (m_damageBuildup > m_hitEffectBuildUpThreshold)
 			{
 				m_damageBuildup -= m_hitEffectBuildUpThreshold;
-				m_hitEffectBuildup.Create(hit.m_point, Quaternion.identity, base.transform);
+				m_hitEffectBuildup.Create(hit.m_point, Quaternion.identity, transform);
 			}
 		}
 		if (m_onDamaged != null)
@@ -162,7 +162,7 @@
 		}
 		if ((bool)m_spawnWhenDamaged)
 		{
-			UnityEngine.Object.Instantiate(m_spawnWhenDamaged, base.transform.position, base.transform.rotation).GetComponent<ZNetView>()?.SetLocalScale(base.transform.localScale);
+			UnityEngine.Object.Instantiate(m_spawnWhenDamaged, transform.position, transform.rotation).GetComponent<ZNetView>()?.SetLocalScale(transform.localScale);
 		}
 		if (num <= 0f)
 		{
@@ -186,7 +186,7 @@
 		CreateDestructionEffects(hitPoint, hitDir, hitCharacter);
 		if (m_destroyNoise > 0f && (hit == null || hit.m_hitType != HitData.HitType.CinderFire))
 		{
-			Player closestPlayer = Player.GetClosestPlayer(base.transform.position, 10f);
+			Player closestPlayer = Player.GetClosestPlayer(transform.position, 10f);
 			if ((bool)closestPlayer)
 			{
 				closestPlayer.AddNoise(m_destroyNoise);
@@ -203,11 +203,11 @@
 		}
 		if ((bool)m_spawnWhenDestroyed)
 		{
-			GameObject gameObject = UnityEngine.Object.Instantiate(m_spawnWhenDestroyed, base.transform.position, base.transform.rotation);
+			GameObject gameObject = UnityEngine.Object.Instantiate(m_spawnWhenDestroyed, transform.position, transform.rotation);
 			ZNetView component = gameObject.GetComponent<ZNetView>();
 			if ((object)component != null)
 			{
-				component.SetLocalScale(base.transform.localScale);
+				component.SetLocalScale(transform.localScale);
 				if (flag)
 				{
 					component.GetZDO().Set(ZDOVars.s_cheated, value: true);
@@ -229,7 +229,7 @@
 
 	private void CreateDestructionEffects(Vector3 hitPoint, Vector3 hitDir, Character hitCharacter)
 	{
-		GameObject[] array = m_destroyedEffect.Create(base.transform.position, base.transform.rotation, base.transform, 1f, -1, hitCharacter ? hitCharacter.GetZDOID() : ZDOID.None);
+		GameObject[] array = m_destroyedEffect.Create(transform.position, transform.rotation, transform, 1f, -1, hitCharacter ? hitCharacter.GetZDOID() : ZDOID.None);
 		for (int i = 0; i < array.Length; i++)
 		{
 			Gibber component = array[i].GetComponent<Gibber>();
@@ -246,7 +246,7 @@
 
 	private void RPC_CreateFragments(long peer)
 	{
-		CreateFragments(base.gameObject);
+		CreateFragments(gameObject);
 	}
 
 	public static void CreateFragments(GameObject rootObject, bool visibleOnly = true)
```

# `FootStep.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+8/-8` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/FootStep.cs
+++ b/FootStep.cs
@@ -129,7 +129,7 @@
 		{
 			UpdateFootstep(dt);
 			UpdateFootlessFootstep(dt);
-			m_lastPosition = base.transform.position;
+			m_lastPosition = transform.position;
 		}
 	}
 
@@ -138,7 +138,7 @@
 		if (m_feet.Length != 0)
 		{
 			Camera mainCamera = Utils.GetMainCamera();
-			if (!(mainCamera == null) && !(Vector3.Distance(base.transform.position, mainCamera.transform.position) > m_footstepCullDistance))
+			if (!(mainCamera == null) && !(Vector3.Distance(transform.position, mainCamera.transform.position) > m_footstepCullDistance))
 			{
 				UpdateFootstepCurveTrigger(dt);
 			}
@@ -149,7 +149,7 @@
 	{
 		if (m_feet.Length == 0 && m_footlessFootsteps)
 		{
-			Vector3 position = base.transform.position;
+			Vector3 position = transform.position;
 			if (!m_character.IsOnGround())
 			{
 				m_distanceAccumulator = 0f;
@@ -161,7 +161,7 @@
 			if (m_distanceAccumulator > m_footlessTriggerDistance)
 			{
 				m_distanceAccumulator -= m_footlessTriggerDistance;
-				OnFoot(base.transform);
+				OnFoot(transform);
 			}
 		}
 	}
@@ -249,7 +249,7 @@
 	{
 		if (m_nview.IsValid())
 		{
-			Vector3 vector = ((foot != null) ? foot.position : base.transform.position);
+			Vector3 vector = ((foot != null) ? foot.position : transform.position);
 			MotionType motionType = GetMotionType(m_character);
 			GroundMaterial groundMaterial = GetGroundMaterial(m_character, vector);
 			int num = FindBestStepEffect(groundMaterial, motionType);
@@ -274,11 +274,11 @@
 
 	private void DoEffect(StepEffect effect, Vector3 point)
 	{
-		Vector3 emitterVelocity = base.transform.position - m_lastPosition;
+		Vector3 emitterVelocity = transform.position - m_lastPosition;
 		GameObject[] effectPrefabs = effect.m_effectPrefabs;
 		foreach (GameObject gameObject in effectPrefabs)
 		{
-			GameObject gameObject2 = UnityEngine.Object.Instantiate(gameObject, point, base.transform.rotation);
+			GameObject gameObject2 = UnityEngine.Object.Instantiate(gameObject, point, transform.rotation);
 			SetEffectCreator(gameObject2);
 			s_stepInstances.Enqueue(gameObject2);
 			ParticleSystem[] componentsInChildren = gameObject2.GetComponentsInChildren<ParticleSystem>();
@@ -458,7 +458,7 @@
 		for (int i = 0; i < m_effects.Count; i++)
 		{
 			StepEffect stepEffect2 = m_effects[i];
-			if (((stepEffect2.m_material & material) != GroundMaterial.None || (stepEffect == null && (stepEffect2.m_material & GroundMaterial.Default) != GroundMaterial.None)) && (stepEffect2.m_motionType & motion) != 0)
+			if (((stepEffect2.m_material & material) != 0 || (stepEffect == null && (stepEffect2.m_material & GroundMaterial.Default) != 0)) && (stepEffect2.m_motionType & motion) != 0)
 			{
 				stepEffect = stepEffect2;
 				result = i;
```

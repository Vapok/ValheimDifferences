# `Raven.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+19/-19` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Raven.cs
+++ b/Raven.cs
@@ -112,7 +112,7 @@
 
 	private void Awake()
 	{
-		base.transform.position = new Vector3(0f, 100000f, 0f);
+		transform.position = new Vector3(0f, 100000f, 0f);
 		m_instance = this;
 		m_animator = m_visual.GetComponentInChildren<Animator>();
 		m_collider = GetComponent<Collider>();
@@ -148,9 +148,9 @@
 		{
 			return false;
 		}
-		if ((m_hasTalked || m_dialogShown) && Chat.instance.IsDialogVisible(base.gameObject))
-		{
-			Chat.instance.ClearNpcText(base.gameObject);
+		if ((m_hasTalked || m_dialogShown) && Chat.instance.IsDialogVisible(gameObject))
+		{
+			Chat.instance.ClearNpcText(gameObject);
 			m_dialogShown = false;
 		}
 		else
@@ -193,7 +193,7 @@
 		{
 			text = "<color=orange>" + topic + "</color>\n" + text;
 		}
-		Chat.instance.SetNpcText(base.gameObject, Vector3.up * m_textOffset, m_textCullDistance, longTimeout ? m_longDialogVisibleTime : m_dialogVisibleTime, showName ? m_name : "", text, large);
+		Chat.instance.SetNpcText(gameObject, Vector3.up * m_textOffset, m_textCullDistance, longTimeout ? m_longDialogVisibleTime : m_dialogVisibleTime, showName ? m_name : "", text, large);
 		m_animator.SetTrigger("talk");
 	}
 
@@ -206,7 +206,7 @@
 	{
 		if (IsSpawned())
 		{
-			m_idleEffect.Create(base.transform.position, base.transform.rotation);
+			m_idleEffect.Create(transform.position, transform.rotation);
 			CancelInvoke("IdleEffect");
 			InvokeRepeating("IdleEffect", UnityEngine.Random.Range(m_idleEffectIntervalMin, m_idleEffectIntervalMax), UnityEngine.Random.Range(m_idleEffectIntervalMin, m_idleEffectIntervalMax));
 		}
@@ -218,7 +218,7 @@
 		{
 			return true;
 		}
-		if (Chat.instance.IsDialogVisible(base.gameObject))
+		if (Chat.instance.IsDialogVisible(gameObject))
 		{
 			return false;
 		}
@@ -230,14 +230,14 @@
 		m_timeSinceTeleport += Time.deltaTime;
 		if (!IsAway() && !IsFlying() && (bool)Player.m_localPlayer)
 		{
-			Vector3 vector = Player.m_localPlayer.transform.position - base.transform.position;
+			Vector3 vector = Player.m_localPlayer.transform.position - transform.position;
 			vector.y = 0f;
 			vector.Normalize();
-			float f = Vector3.SignedAngle(base.transform.forward, vector, Vector3.up);
+			float f = Vector3.SignedAngle(transform.forward, vector, Vector3.up);
 			if (Mathf.Abs(f) > m_minRotationAngle)
 			{
 				m_animator.SetFloat("anglevel", m_rotateSpeed * Mathf.Sign(f), 0.4f, Time.deltaTime);
-				base.transform.rotation = Quaternion.RotateTowards(base.transform.rotation, Quaternion.LookRotation(vector), Time.deltaTime * m_rotateSpeed);
+				transform.rotation = Quaternion.RotateTowards(transform.rotation, Quaternion.LookRotation(vector), Time.deltaTime * m_rotateSpeed);
 			}
 			else
 			{
@@ -246,7 +246,7 @@
 		}
 		if (IsSpawned())
 		{
-			if (Player.m_localPlayer != null && !Chat.instance.IsDialogVisible(base.gameObject) && Vector3.Distance(Player.m_localPlayer.transform.position, base.transform.position) < m_autoTalkDistance)
+			if (Player.m_localPlayer != null && !Chat.instance.IsDialogVisible(gameObject) && Vector3.Distance(Player.m_localPlayer.transform.position, transform.position) < m_autoTalkDistance)
 			{
 				m_randomTextTimer += Time.deltaTime;
 				float num = (m_hasTalked ? m_randomTextInterval : m_randomTextIntervalImportant);
@@ -263,7 +263,7 @@
 					}
 				}
 			}
-			if ((Player.m_localPlayer == null || Vector3.Distance(Player.m_localPlayer.transform.position, base.transform.position) > m_despawnDistance || EnemyNearby(base.transform.position) || RandEventSystem.InEvent() || m_currentText == null || m_groundObject == null || m_hasTalked) && CanHide())
+			if ((Player.m_localPlayer == null || Vector3.Distance(Player.m_localPlayer.transform.position, transform.position) > m_despawnDistance || EnemyNearby(transform.position) || RandEventSystem.InEvent() || m_currentText == null || m_groundObject == null || m_hasTalked) && CanHide())
 			{
 				bool forceTeleport = GetBestText() != null || m_groundObject == null;
 				FlyAway(forceTeleport);
@@ -420,7 +420,7 @@
 
 	private void FlyAway(bool forceTeleport = false)
 	{
-		Chat.instance.ClearNpcText(base.gameObject);
+		Chat.instance.ClearNpcText(gameObject);
 		if (forceTeleport || IsUnderRoof())
 		{
 			m_animator.SetTrigger("poff");
@@ -443,7 +443,7 @@
 				FlyAway(forceTeleport: true);
 				m_currentText = null;
 			}
-			if (IsAway() && bestText != null && !EnemyNearby(base.transform.position) && !RandEventSystem.InEvent())
+			if (IsAway() && bestText != null && !EnemyNearby(transform.position) && !RandEventSystem.InEvent())
 			{
 				bool forceTeleport = m_timeSinceTeleport < 6f;
 				Spawn(bestText, forceTeleport);
@@ -496,7 +496,7 @@
 		if (text.m_static)
 		{
 			m_groundObject = text.m_guidePoint.gameObject;
-			base.transform.position = text.m_guidePoint.transform.position;
+			transform.position = text.m_guidePoint.transform.position;
 		}
 		else
 		{
@@ -504,7 +504,7 @@
 			{
 				return;
 			}
-			base.transform.position = point;
+			transform.position = point;
 			m_groundObject = landOn;
 		}
 		m_currentText = text;
@@ -515,10 +515,10 @@
 		{
 			m_hasTalked = true;
 		}
-		Vector3 forward = Player.m_localPlayer.transform.position - base.transform.position;
+		Vector3 forward = Player.m_localPlayer.transform.position - transform.position;
 		forward.y = 0f;
 		forward.Normalize();
-		base.transform.rotation = Quaternion.LookRotation(forward);
+		transform.rotation = Quaternion.LookRotation(forward);
 		if (forceTeleport)
 		{
 			m_animator.SetTrigger("teleportin");
@@ -543,7 +543,7 @@
 
 	private bool IsUnderRoof()
 	{
-		return Physics.Raycast(base.transform.position + Vector3.up * 0.2f, Vector3.up, 20f, LayerMask.GetMask("Default", "static_solid", "piece"));
+		return Physics.Raycast(transform.position + Vector3.up * 0.2f, Vector3.up, 20f, LayerMask.GetMask("Default", "static_solid", "piece"));
 	}
 
 	public static void RegisterStaticText(RavenText text)
```

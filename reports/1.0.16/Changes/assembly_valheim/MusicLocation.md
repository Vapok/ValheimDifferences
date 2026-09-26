# `MusicLocation.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MusicLocation.cs
+++ b/MusicLocation.cs
@@ -47,13 +47,13 @@
 		{
 			return;
 		}
-		float p_X = Vector3.Distance(base.transform.position, Player.m_localPlayer.transform.position);
+		float p_X = Vector3.Distance(transform.position, Player.m_localPlayer.transform.position);
 		float target = 1f - Utils.SmoothStep(m_radius * 0.5f, m_radius, p_X);
 		volume = Mathf.MoveTowards(volume, target, Time.deltaTime);
 		float num = volume * m_baseVolume * MusicMan.m_masterMusicVolume;
 		if (volume > 0f && !m_audioSource.isPlaying && !m_blockLoopAndFade)
 		{
-			if ((m_oneTime && HasPlayed()) || (m_notIfEnemies && BaseAI.HaveEnemyInRange(Player.m_localPlayer, base.transform.position, m_radius)))
+			if ((m_oneTime && HasPlayed()) || (m_notIfEnemies && BaseAI.HaveEnemyInRange(Player.m_localPlayer, transform.position, m_radius)))
 			{
 				return;
 			}
@@ -120,6 +120,6 @@
 	private void OnDrawGizmos()
 	{
 		Gizmos.color = new Color(0.6f, 0.8f, 0.8f, 0.5f);
-		Gizmos.DrawWireSphere(base.transform.position, m_radius);
+		Gizmos.DrawWireSphere(transform.position, m_radius);
 	}
 }
```

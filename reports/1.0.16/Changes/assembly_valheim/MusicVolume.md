# `MusicVolume.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+10/-10` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MusicVolume.cs
+++ b/MusicVolume.cs
@@ -84,7 +84,7 @@
 
 	private void RPC_PlayMusic(long sender)
 	{
-		bool flag = Vector3.Distance(Player.m_localPlayer.transform.position, base.transform.position) < m_radius + m_surroundingPlayersAdditionalRadius;
+		bool flag = Vector3.Distance(Player.m_localPlayer.transform.position, transform.position) < m_radius + m_surroundingPlayersAdditionalRadius;
 		if (flag)
 		{
 			PlayMusic();
@@ -97,7 +97,7 @@
 
 	private void PlayMusic()
 	{
-		ZLog.Log("MusicLocation '" + base.name + "' Playing Music: " + m_musicName);
+		ZLog.Log("MusicLocation '" + name + "' Playing Music: " + m_musicName);
 		m_PlayCount++;
 		MusicMan.instance.LocationMusic(m_musicName);
 		if (m_loopMusic)
@@ -146,7 +146,7 @@
 
 	private void OnEnter()
 	{
-		ZLog.Log("MusicLocation.OnEnter: " + base.name);
+		ZLog.Log("MusicLocation.OnEnter: " + name);
 		if (!string.IsNullOrEmpty(m_musicName) && (m_maxPlaysPerActivation == 0 || m_PlayCount < m_maxPlaysPerActivation) && UnityEngine.Random.Range(0f, 1f) <= m_musicChance && (m_musicCanRepeat || MusicMan.instance.m_lastLocationMusic != m_musicName))
 		{
 			if ((bool)m_nview)
@@ -162,12 +162,12 @@
 
 	private void OnExit()
 	{
-		ZLog.Log("MusicLocation.OnExit: " + base.name);
+		ZLog.Log("MusicLocation.OnExit: " + name);
 	}
 
 	private void OnExitWide()
 	{
-		ZLog.Log("MusicLocation.OnExitWide: " + base.name);
+		ZLog.Log("MusicLocation.OnExitWide: " + name);
 		if (MusicMan.instance.m_lastLocationMusic == m_musicName && (m_stopMusicOnExit || m_loopMusic))
 		{
 			MusicMan.instance.LocationMusic(null);
@@ -185,7 +185,7 @@
 			}
 			return GetOuterBounds().Contains(point);
 		}
-		float num = Vector3.Distance(base.transform.position, point);
+		float num = Vector3.Distance(transform.position, point);
 		if (checkOuter)
 		{
 			return num < m_radius + m_outerRadiusExtra;
@@ -198,9 +198,9 @@
 		if (!IsBox())
 		{
 			Gizmos.color = new Color(0.6f, 0.8f, 0.8f, 0.5f);
-			Gizmos.DrawWireSphere(base.transform.position, m_radius);
+			Gizmos.DrawWireSphere(transform.position, m_radius);
 			Gizmos.color = new Color(0.6f, 0.8f, 0.8f, 0.25f);
-			Gizmos.DrawWireSphere(base.transform.position, m_radius + m_outerRadiusExtra);
+			Gizmos.DrawWireSphere(transform.position, m_radius + m_outerRadiusExtra);
 		}
 		else
 		{
@@ -228,13 +228,13 @@
 	private Bounds GetInnerBounds()
 	{
 		Bounds box = GetBox();
-		return new Bounds(box.center + base.transform.position, box.size);
+		return new Bounds(box.center + transform.position, box.size);
 	}
 
 	private Bounds GetOuterBounds()
 	{
 		Bounds box = GetBox();
-		return new Bounds(box.center + base.transform.position, box.size + new Vector3(m_outerRadiusExtra, m_outerRadiusExtra, m_outerRadiusExtra));
+		return new Bounds(box.center + transform.position, box.size + new Vector3(m_outerRadiusExtra, m_outerRadiusExtra, m_outerRadiusExtra));
 	}
 
 	private float MinBoundDimension()
```

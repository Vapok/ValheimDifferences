# `RuneStone.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/RuneStone.cs
+++ b/RuneStone.cs
@@ -58,11 +58,11 @@
 		Player player = character as Player;
 		if (player == Player.m_localPlayer && m_interactionSound != null)
 		{
-			UnityEngine.Object.Instantiate(m_interactionSound, base.transform);
+			UnityEngine.Object.Instantiate(m_interactionSound, transform);
 		}
 		if (!string.IsNullOrEmpty(m_locationName))
 		{
-			Game.instance.DiscoverClosestLocation(m_locationName, base.transform.position, m_pinName, (int)m_pinType, m_showMap);
+			Game.instance.DiscoverClosestLocation(m_locationName, transform.position, m_pinName, (int)m_pinType, m_showMap);
 		}
 		RandomRuneText randomText = GetRandomText();
 		if (randomText != null)
@@ -104,7 +104,7 @@
 		{
 			return null;
 		}
-		Vector3 position = base.transform.position;
+		Vector3 position = transform.position;
 		int seed = (int)position.x * (int)position.z;
 		UnityEngine.Random.State state = UnityEngine.Random.state;
 		UnityEngine.Random.InitState(seed);
```

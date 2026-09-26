# `AudioMan.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+9/-9` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/AudioMan.cs
+++ b/AudioMan.cs
@@ -209,7 +209,7 @@
 		m_instance = this;
 		UnityEngine.Object.DontDestroyOnLoad(base.gameObject);
 		GameObject gameObject = new GameObject("ocean_ambient_loop");
-		gameObject.transform.SetParent(base.transform);
+		gameObject.transform.SetParent(transform);
 		m_oceanAmbientSource = gameObject.AddComponent<AudioSource>();
 		m_oceanAmbientSource.loop = true;
 		m_oceanAmbientSource.spatialBlend = 0.75f;
@@ -225,7 +225,7 @@
 		m_oceanAmbientSource.priority = 0;
 		m_oceanAmbientSource.Play();
 		GameObject gameObject2 = new GameObject("ambient_loop");
-		gameObject2.transform.SetParent(base.transform);
+		gameObject2.transform.SetParent(transform);
 		m_ambientLoopSource = gameObject2.AddComponent<AudioSource>();
 		m_ambientLoopSource.loop = true;
 		m_ambientLoopSource.spatialBlend = 0f;
@@ -234,7 +234,7 @@
 		m_ambientLoopSource.priority = 0;
 		m_ambientLoopSource.volume = 0f;
 		GameObject gameObject3 = new GameObject("wind_loop");
-		gameObject3.transform.SetParent(base.transform);
+		gameObject3.transform.SetParent(transform);
 		m_windLoopSource = gameObject3.AddComponent<AudioSource>();
 		m_windLoopSource.loop = true;
 		m_windLoopSource.spatialBlend = 0f;
@@ -247,7 +247,7 @@
 		if (m_enableShieldDomeHum)
 		{
 			GameObject gameObject4 = UnityEngine.Object.Instantiate(m_shieldHumPrefab);
-			gameObject4.transform.SetParent(base.transform);
+			gameObject4.transform.SetParent(transform);
 			m_shieldHumSource = gameObject4.GetComponent<AudioSource>();
 		}
 		m_maxLavaLoops = GetLoopingMaxConcurrency(m_lavaLoopPrefab.GetComponent<ZSFX>());
@@ -375,7 +375,7 @@
 		if (SelectRandomAmbientClip(out var clip, out fadeoutDuration))
 		{
 			Vector3 randomAmbiencePoint = GetRandomAmbiencePoint();
-			GameObject gameObject = UnityEngine.Object.Instantiate(m_randomAmbientPrefab, randomAmbiencePoint, Quaternion.identity, base.transform);
+			GameObject gameObject = UnityEngine.Object.Instantiate(m_randomAmbientPrefab, randomAmbiencePoint, Quaternion.identity, transform);
 			ZSFX component = gameObject.GetComponent<ZSFX>();
 			component.m_audioClips = new AudioClip[1] { clip };
 			component.Play();
@@ -429,7 +429,7 @@
 		}
 		if (i != 5)
 		{
-			GameObject gameObject = UnityEngine.Object.Instantiate(m_randomAmbientPrefab, vector, Quaternion.identity, base.transform);
+			GameObject gameObject = UnityEngine.Object.Instantiate(m_randomAmbientPrefab, vector, Quaternion.identity, transform);
 			ZSFX component = gameObject.GetComponent<ZSFX>();
 			AudioClip audioClip = m_randomLavaNoises[UnityEngine.Random.Range(0, m_randomLavaNoises.Count - 1)];
 			component.m_audioClips = new AudioClip[1] { audioClip };
@@ -464,7 +464,7 @@
 				return;
 			}
 			ZSFX component = UnityEngine.Object.Instantiate(m_lavaLoopPrefab, vector, Quaternion.identity).GetComponent<ZSFX>();
-			component.OnDestroyingSfx += delegate(ZSFX zsfx)
+			component.OnDestroyingSfx += (ZSFX zsfx) =>
 			{
 				if (m_ambientLavaLoops.Contains(zsfx))
 				{
@@ -727,7 +727,7 @@
 	{
 		foreach (BiomeAmbients randomAmbient in m_randomAmbients)
 		{
-			if ((randomAmbient.m_biome & biome) != Heightmap.Biome.None)
+			if ((randomAmbient.m_biome & biome) != 0)
 			{
 				return randomAmbient;
 			}
@@ -787,7 +787,7 @@
 			sfx.ConcurrencyDisable();
 		}
 		m_loopingSfx.Add(sfx);
-		sfx.OnDestroyingSfx += delegate(ZSFX zsfx)
+		sfx.OnDestroyingSfx += (ZSFX zsfx) =>
 		{
 			m_loopingSfx.Remove(zsfx);
 		};
```

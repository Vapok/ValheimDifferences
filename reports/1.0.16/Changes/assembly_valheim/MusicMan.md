# `MusicMan.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MusicMan.cs
+++ b/MusicMan.cs
@@ -118,7 +118,7 @@
 		}
 		m_instance = this;
 		GameObject gameObject = new GameObject("music");
-		gameObject.transform.SetParent(base.transform);
+		gameObject.transform.SetParent(transform);
 		m_musicSource = gameObject.AddComponent<AudioSource>();
 		m_musicSource.loop = true;
 		m_musicSource.spatialBlend = 0f;
```

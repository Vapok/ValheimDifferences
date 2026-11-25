# `SlowUpdater.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+11/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Awake() [Method Body Modified]`
- `UpdateLoop() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/SlowUpdater.cs
+++ b/SlowUpdater.cs
@@ -1,10 +1,15 @@
 using System.Collections;
 using System.Collections.Generic;
+using System.Diagnostics;
 using UnityEngine;
 
 public class SlowUpdater : MonoBehaviour
 {
 	private const int m_updatesPerFrame = 100;
+
+	private const int m_minimumUpdatesPerFrame = 10;
+
+	private const float m_maximumTimeAllocation = 0.25f;
 
 	private void Awake()
 	{
@@ -13,15 +18,19 @@
 
 	private IEnumerator UpdateLoop()
 	{
+		Stopwatch sw = new Stopwatch();
 		while (true)
 		{
 			List<SlowUpdate> instances = SlowUpdate.GetAllInstaces();
 			int index = 0;
+			int target = 0;
 			while (index < instances.Count)
 			{
+				target += 100;
 				float time = Time.time;
+				sw.Restart();
 				Vector2s zone = ZoneSystem.GetZone(ZNet.instance.GetReferencePosition());
-				for (int i = 0; i < 100; i++)
+				for (int i = 0; i < 10 || (index < target && sw.Elapsed.TotalMilliseconds < 0.25); i++)
 				{
 					if (instances.Count == 0)
 					{
@@ -37,7 +46,7 @@
 				}
 				yield return null;
 			}
-			yield return new WaitForSeconds(0.1f);
+			yield return null;
 		}
 	}
 }
```

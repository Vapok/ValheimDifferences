# `RandomPieceRotation.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/RandomPieceRotation.cs
+++ b/RandomPieceRotation.cs
@@ -16,14 +16,14 @@
 
 	private void Awake()
 	{
-		Vector3 position = base.transform.position;
+		Vector3 position = transform.position;
 		int seed = (int)position.x * (int)(position.y * 10f) * (int)(position.z * 100f);
 		Random.State state = Random.state;
 		Random.InitState(seed);
 		float x = (m_rotateX ? ((float)Random.Range(0, m_stepsX) * 360f / (float)m_stepsX) : 0f);
 		float y = (m_rotateY ? ((float)Random.Range(0, m_stepsY) * 360f / (float)m_stepsY) : 0f);
 		float z = (m_rotateZ ? ((float)Random.Range(0, m_stepsZ) * 360f / (float)m_stepsZ) : 0f);
-		base.transform.localRotation = Quaternion.Euler(x, y, z);
+		transform.localRotation = Quaternion.Euler(x, y, z);
 		Random.state = state;
 	}
 }
```

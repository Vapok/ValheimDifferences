# `WaterVolume.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/WaterVolume.cs
+++ b/WaterVolume.cs
@@ -174,7 +174,7 @@
 			float waveFactorBig = 1f - (float)WorldGenerator.DeepNorthWaveFade(point.x, point.z);
 			num = ((num2 == 0f) ? 0f : CalcWave(point, num2, waterTime, waveFactor, waveFactorBig));
 		}
-		float num3 = base.transform.position.y + num + m_surfaceOffset;
+		float num3 = transform.position.y + num + m_surfaceOffset;
 		if (m_forceDepth < 0f && Utils.LengthXZ(point) > 10500f)
 		{
 			num3 -= 100f;
@@ -234,7 +234,7 @@
 		{
 			return m_oneDepth;
 		}
-		Vector3 vector = base.transform.InverseTransformPoint(point);
+		Vector3 vector = transform.InverseTransformPoint(point);
 		Vector3 size = m_collider.bounds.size;
 		float t = (vector.x + size.x / 2f) / size.x;
 		float t2 = (vector.z + size.z / 2f) / size.z;
@@ -317,6 +317,6 @@
 	private void OnDrawGizmosSelected()
 	{
 		Gizmos.color = Color.yellow;
-		Gizmos.DrawWireCube(base.transform.position + Vector3.up * m_surfaceOffset, new Vector3(2f, 0.05f, 2f));
+		Gizmos.DrawWireCube(transform.position + Vector3.up * m_surfaceOffset, new Vector3(2f, 0.05f, 2f));
 	}
 }
```

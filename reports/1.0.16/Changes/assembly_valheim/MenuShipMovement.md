# `MenuShipMovement.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MenuShipMovement.cs
+++ b/MenuShipMovement.cs
@@ -18,6 +18,6 @@
 	private void Update()
 	{
 		m_time += Time.deltaTime;
-		base.transform.rotation = Quaternion.Euler(Mathf.Sin(m_time * m_freq) * m_xAngle, 0f, Mathf.Sin(m_time * 1.5341234f * m_freq) * m_zAngle);
+		transform.rotation = Quaternion.Euler(Mathf.Sin(m_time * m_freq) * m_xAngle, 0f, Mathf.Sin(m_time * 1.5341234f * m_freq) * m_zAngle);
 	}
 }
```

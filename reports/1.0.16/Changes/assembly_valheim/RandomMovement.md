# `RandomMovement.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/RandomMovement.cs
+++ b/RandomMovement.cs
@@ -10,13 +10,13 @@
 
 	private void Start()
 	{
-		m_basePosition = base.transform.localPosition;
+		m_basePosition = transform.localPosition;
 	}
 
 	private void Update()
 	{
 		float num = Time.time * m_frequency;
 		Vector3 vector = new Vector3(Mathf.Sin(num) * Mathf.Sin(num * 0.56436f), Mathf.Sin(num * 0.56436f) * Mathf.Sin(num * 0.688742f), Mathf.Cos(num * 0.758348f) * Mathf.Cos(num * 0.4563696f)) * m_movement;
-		base.transform.localPosition = m_basePosition + vector;
+		transform.localPosition = m_basePosition + vector;
 	}
 }
```

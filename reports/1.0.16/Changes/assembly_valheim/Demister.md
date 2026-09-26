# `Demister.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Demister.cs
+++ b/Demister.cs
@@ -16,7 +16,7 @@
 	private void Awake()
 	{
 		m_forceField = GetComponent<ParticleSystemForceField>();
-		m_lastUpdatePosition = base.transform.position;
+		m_lastUpdatePosition = transform.position;
 		if (m_disableForcefieldDelay > 0f)
 		{
 			Invoke("DisableForcefield", m_disableForcefieldDelay);
@@ -40,7 +40,7 @@
 
 	public float GetMovedDistance()
 	{
-		Vector3 position = base.transform.position;
+		Vector3 position = transform.position;
 		if (position == m_lastUpdatePosition)
 		{
 			return 0f;
```

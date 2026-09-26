# `Feast.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Feast.cs
+++ b/Feast.cs
@@ -42,7 +42,7 @@
 		UpdateVisual();
 		if (!m_foodItem)
 		{
-			m_foodItem = base.gameObject.GetComponent<ItemDrop>();
+			m_foodItem = gameObject.GetComponent<ItemDrop>();
 		}
 		if (!m_foodItem)
 		{
@@ -106,7 +106,7 @@
 
 	public void RPC_OnEat(long sender)
 	{
-		m_eatEffect.Create(base.transform.position, base.transform.rotation);
+		m_eatEffect.Create(transform.position, transform.rotation);
 		UpdateVisual();
 	}
 
@@ -126,7 +126,7 @@
 
 	private bool InUseDistance(Humanoid human)
 	{
-		return Vector3.Distance(human.transform.position, base.transform.position) < m_useDistance;
+		return Vector3.Distance(human.transform.position, transform.position) < m_useDistance;
 	}
 
 	public string GetHoverText()
```

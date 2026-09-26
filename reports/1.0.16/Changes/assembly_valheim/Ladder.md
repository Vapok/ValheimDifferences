# `Ladder.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Ladder.cs
+++ b/Ladder.cs
@@ -48,7 +48,7 @@
 
 	private bool InUseDistance(Humanoid human)
 	{
-		return Vector3.Distance(human.transform.position, base.transform.position) < m_useDistance;
+		return Vector3.Distance(human.transform.position, transform.position) < m_useDistance;
 	}
 
 	public float GetHoverOffset()
```

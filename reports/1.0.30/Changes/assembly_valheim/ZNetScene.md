# `ZNetScene.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `AddInstance() [Method Body Modified]`
- `IsPrefabZDOValid() [Method Body Modified]`
- `private bool IsPrefabZDOValid(ZDO zdo)`
- `public bool IsPrefabZDOValid(ZDO zdo)`

---

## 📝 Code Diff

```diff
--- a/ZNetScene.cs
+++ b/ZNetScene.cs
@@ -75,7 +75,7 @@
 		m_instances[zdo] = nview;
 	}
 
-	private bool IsPrefabZDOValid(ZDO zdo)
+	public bool IsPrefabZDOValid(ZDO zdo)
 	{
 		int prefab = zdo.GetPrefab();
 		if (prefab == 0)
```

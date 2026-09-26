# `MaterialVariation.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MaterialVariation.cs
+++ b/MaterialVariation.cs
@@ -41,7 +41,7 @@
 		}
 		if (!m_nview || !m_renderer)
 		{
-			ZLog.LogError("Missing nview or renderer on '" + base.transform.gameObject.name + "'");
+			ZLog.LogError("Missing nview or renderer on '" + transform.gameObject.name + "'");
 		}
 		m_nview.Register<int>("RPC_UpdateMaterial", RPC_UpdateMaterial);
 		InvokeRepeating("CheckMaterial", 0f, 0.2f);
```

# `RandomMaterialValues.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/RandomMaterialValues.cs
+++ b/RandomMaterialValues.cs
@@ -56,7 +56,7 @@
 		m_piece = GetComponentInParent<Piece>();
 		if (!m_nview)
 		{
-			ZLog.LogError("Missing nview on '" + base.transform.gameObject.name + "'");
+			ZLog.LogError("Missing nview on '" + transform.gameObject.name + "'");
 		}
 		InvokeRepeating("CheckMaterial", 0f, 0.2f);
 	}
@@ -77,7 +77,7 @@
 					VectorVariationProperty vectorVariationProperty = m_vectorProperties[i];
 					foreach (string propertyName in vectorVariationProperty.m_propertyNames)
 					{
-						MaterialMan.instance.SetValue(base.gameObject, Shader.PropertyToID(propertyName), vectorVariationProperty.GetValue(m_randomSeed + i));
+						MaterialMan.instance.SetValue(gameObject, Shader.PropertyToID(propertyName), vectorVariationProperty.GetValue(m_randomSeed + i));
 					}
 				}
 				m_isSet = true;
```

# `ParticleIntensityScaler.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+10/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ParticleIntensityScaler.cs
+++ b/ParticleIntensityScaler.cs
@@ -274,7 +274,15 @@
 				}
 				if (scaleLifetime > 0f)
 				{
-					float multiplier = ((!inverseLifetimeScaling) ? (num * scaleLifetime) : ((num <= 0f) ? 0f : (1f / (num * scaleLifetime))));
+					float multiplier;
+					if (inverseLifetimeScaling)
+					{
+						multiplier = ((num <= 0f) ? 0f : (1f / (num * scaleLifetime)));
+					}
+					else
+					{
+						multiplier = num * scaleLifetime;
+					}
 					main.startLifetime = MultiplyCurve(particleData.startLifetime, multiplier);
 				}
 				if (scaleAlpha > 0f)
@@ -407,7 +415,7 @@
 			}
 			if (colorKeys.Length > 8 || gradient2.alphaKeys.Length > 8)
 			{
-				Debug.LogError($"Gradient on {base.gameObject.transform.parent.parent.name} {base.gameObject} has {colorKeys.Length} color keys and {gradient2.alphaKeys.Length} alpha keys, which may cause issues when scaling. Consider reducing the number of keys to 8 or less.", base.gameObject);
+				Debug.LogError($"Gradient on {gameObject.transform.parent.parent.name} {gameObject} has {colorKeys.Length} color keys and {gradient2.alphaKeys.Length} alpha keys, which may cause issues when scaling. Consider reducing the number of keys to 8 or less.", gameObject);
 			}
 			gradient2.SetKeys(colorKeys, gradient2.alphaKeys);
 			gradient.gradient = gradient2;
```

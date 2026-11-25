# `GraphicsSettingIntExtentions.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `GetRange() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/GraphicsSettingIntExtentions.cs
+++ b/GraphicsSettingIntExtentions.cs
@@ -69,6 +69,7 @@
 		case GraphicsSettingInt.Vegetation:
 			return new RangeIntInclusive(1, 3);
 		case GraphicsSettingInt.Lights:
+			return new RangeIntInclusive(-1, 2);
 		case GraphicsSettingInt.ShadowQuality:
 			return new RangeIntInclusive(0, 2);
 		case GraphicsSettingInt.LOD:
```

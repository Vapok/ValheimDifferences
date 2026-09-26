# `placeable_bigrock_01.json` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Category**: `pieces`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Explanation**: Disables rain damage immunity for Big Rock 1, causing it to suffer weather degradation over time when left unroofed.
* **Main Asset Report**: [⬅ Back to Main Asset Diff Report](../Valheim_Assets_Diff.md)
* **Main Game Diff**: [⬅ Back to Valheim Assembly Diff](../../Valheim_Diff.md)

---

## 📝 Asset Diff

```diff
--- /home/vapok/Modding/Valheim/ValheimAssets/1.0.15/pieces/placeable_bigrock_01.json	2026-09-25 08:45:35.836906289 -0400
+++ /home/vapok/Modding/Valheim/ValheimAssets/1.0.16/pieces/placeable_bigrock_01.json	2026-09-25 21:47:59.248576227 -0400
@@ -77,7 +77,7 @@
       "m_hitNoise": 0.0,
       "m_materialType": 1,
       "m_minToolTier": 0,
-      "m_noRoofWear": true,
+      "m_noRoofWear": false,
       "m_noSupportWear": true,
       "m_outsideRequiredBiomeDamage": 25.0,
       "m_requiredBiome": 0,
```

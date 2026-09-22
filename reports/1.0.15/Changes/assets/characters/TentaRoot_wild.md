# `TentaRoot_wild.json` Diff (`1.0.14` $\rightarrow$ `1.0.15`)

* **Category**: `characters`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Explanation**: Converted the hardcoded display name to the localization key '$enemy_root' so wild tentacle roots display correctly translated names.
* **Main Asset Report**: [⬅ Back to Main Asset Diff Report](../Valheim_Assets_Diff.md)
* **Main Game Diff**: [⬅ Back to Valheim Assembly Diff](../../Valheim_Diff.md)

---

## 📝 Asset Diff

```diff
--- /home/vapok/Modding/Valheim/ValheimAssets/1.0.14/characters/TentaRoot_wild.json	2026-09-21 23:08:52.241987479 -0400
+++ /home/vapok/Modding/Valheim/ValheimAssets/1.0.15/characters/TentaRoot_wild.json	2026-09-21 23:14:50.316799022 -0400
@@ -57,7 +57,7 @@
       "m_lavaFullDamage": 100.0,
       "m_lavaSlowHeight": 0.8,
       "m_lavaSlowMax": 0.5,
-      "m_name": "Root",
+      "m_name": "$enemy_root",
       "m_perfectBlockStaminaDrain": 0.0,
       "m_regenAllHPTime": 3600.0,
       "m_runSpeed": 0.0,
```

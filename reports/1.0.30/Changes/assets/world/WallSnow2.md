# `WallSnow2.json` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Category**: `world`
* **Status**: `🟡 MODIFIED` (`+13/-0` lines)
* **Explanation**: Modified component field attributes.
* **Main Asset Report**: [⬅ Back to Main Asset Diff Report](../Valheim_Assets_Diff.md)
* **Main Game Diff**: [⬅ Back to Valheim Assembly Diff](../../Valheim_Diff.md)

---

## 📝 Asset Diff

```diff
--- /home/vapok/Modding/Valheim/ValheimAssets/1.0.21/world/WallSnow2.json	2026-10-28 09:13:04.435058765 -0400
+++ /home/vapok/Modding/Valheim/ValheimAssets/1.0.30/world/WallSnow2.json	2026-11-25 05:01:39.775172373 -0500
@@ -1,5 +1,18 @@
 {
   "components": {
+    "Destructible": {
+      "m_autoCreateFragments": false,
+      "m_destroyNoise": 0.0,
+      "m_destructibleType": 1,
+      "m_health": 100.0,
+      "m_hitEffectBigThreshold": 0.0,
+      "m_hitEffectBuildUpThreshold": 0.0,
+      "m_hitNoise": 0.0,
+      "m_minDamageTreshold": 0.0,
+      "m_minToolTier": 0,
+      "m_triggerPrivateArea": false,
+      "m_ttl": 0.0
+    },
     "SnowDestruction": {
       "m_destructionChanceMultiplier": 1.0
     },
```

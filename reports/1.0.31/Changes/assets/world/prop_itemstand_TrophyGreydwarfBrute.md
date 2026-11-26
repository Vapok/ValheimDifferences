# `prop_itemstand_TrophyGreydwarfBrute.json` Diff (`1.0.30` $\rightarrow$ `1.0.31`)

* **Category**: `world`
* **Status**: `🟡 MODIFIED` (`+31/-13` lines)
* **Explanation**: Modified component field attributes.
* **Main Asset Report**: [⬅ Back to Main Asset Diff Report](../Valheim_Assets_Diff.md)
* **Main Game Diff**: [⬅ Back to Valheim Assembly Diff](../../Valheim_Diff.md)

---

## 📝 Asset Diff

```diff
--- /home/vapok/Modding/Valheim/ValheimAssets/1.0.30/world/prop_itemstand_TrophyGreydwarfBrute.json	2026-11-25 05:01:39.433839918 -0500
+++ /home/vapok/Modding/Valheim/ValheimAssets/1.0.31/world/prop_itemstand_TrophyGreydwarfBrute.json	2026-11-26 09:29:17.229658375 -0500
@@ -1,22 +1,40 @@
 {
   "components": {
-    "Destructible": {
-      "m_autoCreateFragments": false,
-      "m_destroyNoise": 0.0,
-      "m_destructibleType": 1,
-      "m_health": 10.0,
-      "m_hitEffectBigThreshold": 0.0,
-      "m_hitEffectBuildUpThreshold": 0.0,
-      "m_hitNoise": 0.0,
-      "m_minDamageTreshold": 0.0,
-      "m_minToolTier": 0,
-      "m_triggerPrivateArea": false,
-      "m_ttl": 0.0
-    },
     "DropOnDestroyed": {
       "m_spawnYOffset": 0.5,
       "m_spawnYStep": 0.3
     },
+    "WearNTear": {
+      "m_ashDamageImmune": false,
+      "m_ashDamageResist": false,
+      "m_autoCreateFragments": true,
+      "m_burnable": true,
+      "m_comOffset": {
+        "x": 0.0,
+        "y": 0.0,
+        "z": 0.0
+      },
+      "m_destroyNoise": 0.0,
+      "m_eventDamage": 25.0,
+      "m_eventDamageDeviation": 10.0,
+      "m_forceCorrectCOMCalculation": false,
+      "m_health": 50.0,
+      "m_hitNoise": 0.0,
+      "m_materialType": 0,
+      "m_minToolTier": 0,
+      "m_noRoofWear": true,
+      "m_noSupportWear": true,
+      "m_outsideRequiredBiomeDamage": 25.0,
+      "m_requiredBiome": 0,
+      "m_requiredPersistentEvent": "",
+      "m_roofCheckOffset": 0.0,
+      "m_snowBuildup": 0.0,
+      "m_snowDamageImmune": true,
+      "m_staticPosition": true,
+      "m_supports": true,
+      "m_takeDamageIfInsideEvent": false,
+      "m_triggerPrivateArea": true
+    },
     "ZNetView": {
       "m_distant": false,
       "m_persistent": true,
```

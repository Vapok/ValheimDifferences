# `placeable_bigrock_02.json` Diff (`1.0.14` $\rightarrow$ `1.0.15`)

* **Category**: `pieces`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Explanation**: Enabled resource recovery so players get building materials refunded when deconstructing or destroying this large rock piece.
* **Main Asset Report**: [⬅ Back to Main Asset Diff Report](../Valheim_Assets_Diff.md)
* **Main Game Diff**: [⬅ Back to Valheim Assembly Diff](../../Valheim_Diff.md)

---

## 📝 Asset Diff

```diff
--- /home/vapok/Modding/Valheim/ValheimAssets/1.0.14/pieces/placeable_bigrock_02.json	2026-09-21 23:08:52.279690023 -0400
+++ /home/vapok/Modding/Valheim/ValheimAssets/1.0.15/pieces/placeable_bigrock_02.json	2026-09-21 23:14:50.359279649 -0400
@@ -48,7 +48,7 @@
           "amount": 10,
           "amountPerLevel": 0,
           "item": "Stone",
-          "recover": false
+          "recover": true
         }
       ],
       "m_returnResourceHeightOffset": 1.0,
```

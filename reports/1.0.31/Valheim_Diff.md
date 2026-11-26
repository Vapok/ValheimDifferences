# Valheim API & Assembly Diff: `1.0.30` $\rightarrow$ `1.0.31`

> Automated decompilation comparison, mod impact report, and transpiler IL safety audit generated between Valheim version **1.0.30** and **1.0.31**.
>
> 🛡️ **Unity Asset Diff**: [View Detailed Unity Asset Difference Report](Changes/assets/Valheim_Assets_Diff.md)

## 📊 Executive Summary

| Metric | Count |
| :--- | :--- |
| **Assemblies Changed** | `1` / `9` |
| **Game Classes Modified** | `4` |
| **Game Classes Added** | `0` |
| **Game Classes Deleted** | `0` |
| **Total Lines Added** | `+27` |
| **Total Lines Removed** | `-14` |
| **Critical Breaking Mods** | `0` mod(s) |
| **High Risk Mod Patches** | `0` mod(s) |
| **Medium Risk Mod Patches** | `2` mod(s) |
| **Transpiler Hooks Audited** | `7` total (`7` safe / `0` caution / `0` critical) |

## 🔬 Transpiler Safety Audit

Audits every Harmony Transpiler across workspace mods to verify whether the underlying vanilla IL hook methods were modified in this game version.

<table>
  <thead>
    <tr>
      <th align="center">Status</th>
      <th align="left">Mod</th>
      <th align="left">Hook Target Class &amp; Method</th>
      <th align="left">Source Location</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>Humanoid.UpdateEquipmentStatusEffects</code></td>
      <td><code>Humanoid.cs:19</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'Humanoid' and method 'UpdateEquipmentStatusEffects' are 100% UNCHANGED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>InventoryGui.Update</code></td>
      <td><code>InventoryGui.cs:385</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'InventoryGui' and method 'Update' are 100% UNCHANGED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>ItemData.GetWeight</code></td>
      <td><code>ItemDrop.cs:22</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'ItemData' and method 'GetWeight' are 100% UNCHANGED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>Player.SetControls</code></td>
      <td><code>PlayerSetControlsPatch.cs:9</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'Player' and method 'SetControls' are 100% UNCHANGED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>Player.UpdateAttackBowDraw</code></td>
      <td><code>PlayerUpdateAttackBowDrawPatch.cs:8</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'Player' and method 'UpdateAttackBowDraw' are 100% UNCHANGED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>NoFogBruh</code></strong></td>
      <td><code>PostProcessingBehaviour.OnPreRender</code></td>
      <td><code>DisableFogComponent.cs:289</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'PostProcessingBehaviour' and method 'OnPreRender' are 100% UNCHANGED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>XPortalNetworks</code></strong></td>
      <td><code>TeleportWorld.UpdatePortal</code></td>
      <td><code>TeleportWorld.cs:87</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'TeleportWorld' and method 'UpdatePortal' are 100% UNCHANGED.</em></td>
    </tr>
  </tbody>
</table>

## 🛡️ Mod Impact: Unity Asset Cross-Reference

Scans workspace mods for direct references (prefab names, item drops, status effects, and recipes) against modified Unity assets.

<table>
  <thead>
    <tr>
      <th align="center">Risk</th>
      <th align="left">Mod</th>
      <th align="left">Referenced Asset</th>
      <th align="left">Source Location</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center" rowspan="2">🟡 <code>MEDIUM</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>LinenThread</code> (<code>items</code>)</td>
      <td><code>NetKitManager.cs:69</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟡 <code>MEDIUM</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>LinenThread</code> (<code>items</code>)</td>
      <td><code>NetKitManager.cs:104</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>piece_cauldron</code> (<code>pieces</code>)</td>
      <td><code>BaitFactory.cs:36</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>piece_cauldron</code> (<code>pieces</code>)</td>
      <td><code>BaitFactory.cs:45</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>piece_cauldron</code> (<code>pieces</code>)</td>
      <td><code>BaitFactory.cs:54</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>piece_cauldron</code> (<code>pieces</code>)</td>
      <td><code>BaitFactory.cs:63</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>piece_cauldron</code> (<code>pieces</code>)</td>
      <td><code>BaitFactory.cs:72</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>piece_cauldron</code> (<code>pieces</code>)</td>
      <td><code>BaitFactory.cs:81</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>piece_cauldron</code> (<code>pieces</code>)</td>
      <td><code>BaitFactory.cs:90</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>piece_cauldron</code> (<code>pieces</code>)</td>
      <td><code>BaitFactory.cs:99</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>piece_cauldron</code> (<code>pieces</code>)</td>
      <td><code>FoodFactory.cs:56</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>piece_cauldron</code> (<code>pieces</code>)</td>
      <td><code>FoodFactory.cs:68</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>piece_cauldron</code> (<code>pieces</code>)</td>
      <td><code>FoodFactory.cs:77</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>piece_cauldron</code> (<code>pieces</code>)</td>
      <td><code>FoodFactory.cs:86</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>piece_cauldron</code> (<code>pieces</code>)</td>
      <td><code>FoodFactory.cs:95</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>piece_cauldron</code> (<code>pieces</code>)</td>
      <td><code>FoodFactory.cs:104</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>DoorOpenerBruh</code></strong></td>
      <td><code>ashwood_door</code> (<code>pieces</code>)</td>
      <td><code>DoorFactory.cs:27</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>DoorOpenerBruh</code></strong></td>
      <td><code>wood_fence_gate</code> (<code>pieces</code>)</td>
      <td><code>DoorFactory.cs:38</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>DoorOpenerBruh</code></strong></td>
      <td><code>stave_gate</code> (<code>pieces</code>)</td>
      <td><code>DoorFactory.cs:39</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>Vapok.Common</code></strong></td>
      <td><code>piece_cauldron</code> (<code>pieces</code>)</td>
      <td><code>ItemManager.cs:32</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>Vapok.Common</code></strong></td>
      <td><code>piece_spinningwheel</code> (<code>pieces</code>)</td>
      <td><code>ItemManager.cs:51</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>WardMeBruh</code></strong></td>
      <td><code>piece_cauldron</code> (<code>pieces</code>)</td>
      <td><code>KeystoneItemFactory.cs:489</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Modified component field attributes.</em></td>
    </tr>
  </tbody>
</table>

## 🎯 Mod Impact Assessment

Scans all workspace mod projects for Harmony patches, transpilers, and breaking API references against modified game classes.

| Mod Project | Risk Level | Breaking API & Direct Hook Issues | Patches on Modified Classes | Touched Game Classes |
| :--- | :---: | :--- | :--- | :--- |
| **`AdventureBackpacks`** | 🟢 LOW | *None* | *None* | `Version` |
| **`AutoFeedRedux`** | 🟢 LOW | *None* | *None* | `Version` |
| **`BaitMeBruh`** | 🟢 LOW | *None* | *None* | `BuildUi`, `CookingStation`, `Version` |
| **`BepInEx.ConfigDrawers`** | 🟢 LOW | *None* | *None* | `Version` |
| **`BetterSleepBruh`** | 🟡 MEDIUM | *None* | `CookingStation.GetDeltaTime` | `CookingStation`, `Version` |
| **`ConsoleBuddy`** | 🟢 LOW | *None* | *None* | `Version` |
| **`DoorOpenerBruh`** | 🟢 LOW | *None* | *None* | `Version` |
| **`FastItemTransfer`** | 🟢 LOW | *None* | *None* | `Version` |
| **`NoFogBruh`** | 🟢 LOW | *None* | *None* | `Version` |
| **`RandomSpawnPointBruh`** | 🟢 LOW | *None* | *None* | `Version` |
| **`SaveYourLuckBruh`** | 🟢 LOW | *None* | *None* | `Version` |
| **`ShieldMeBruh`** | 🟢 LOW | *None* | *None* | `Version` |
| **`TheQueensDeadBruh`** | 🟢 LOW | *None* | *None* | `Version` |
| **`Vapok.Common`** | 🟢 LOW | *None* | *None* | `Version` |
| **`WardMeBruh`** | 🟡 MEDIUM | *None* | `CookingStation.Awake` | `CookingStation`, `Version` |
| **`XPortalNetworks`** | 🟢 LOW | *None* | *None* | `Version` |

## 📦 Assemblies Overview

| Assembly | Modified | Added | Deleted | Line Changes |
| :--- | :--- | :--- | :--- | :--- |
| `Assembly-CSharp.dll` | `0` | `0` | `0` | *No Changes* |
| `assembly_googleanalytics.dll` | `0` | `0` | `0` | *No Changes* |
| `assembly_guiutils.dll` | `0` | `0` | `0` | *No Changes* |
| `assembly_lux.dll` | `0` | `0` | `0` | *No Changes* |
| `assembly_postprocessing.dll` | `0` | `0` | `0` | *No Changes* |
| `assembly_simplemeshcombine.dll` | `0` | `0` | `0` | *No Changes* |
| `assembly_sunshafts.dll` | `0` | `0` | `0` | *No Changes* |
| `assembly_utils.dll` | `0` | `0` | `0` | *No Changes* |
| [`assembly_valheim.dll`](#assembly_valheim) | `4` | `0` | `0` | `+27` / `-14` |

---

## 🔧 Assembly: `assembly_valheim.dll` <a id="assembly_valheim"></a>

**Changes Summary:** `4` modified, `0` added, `0` deleted (`+27` / `-14` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`BuildUi.cs`](Changes/assembly_valheim/BuildUi.md) | `FavoritePiece() [Method Body Modified]`<br>`OnTouchLongPressStarted() [Method Body Modified]`<br>`SearchFieldDeselect() [Method Body Modified]`<br>`SearchFieldSelect() [Method Body Modified]`<br>`SubscribeEvents() [Method Body Modified]`<br>*...and 3 more* |
| 🟡 `MOD` | [`BuildUiFavoriteCategoryCheckButton.cs`](Changes/assembly_valheim/BuildUiFavoriteCategoryCheckButton.md) | `Awake() [Method Body Modified]`<br>`Awake() [Method Removed]`<br>`OnClick() [Method Body Modified]`<br>`private void Awake()` |
| 🟡 `MOD` | [`CookingStation.cs`](Changes/assembly_valheim/CookingStation.md) | `SpawnItem() [Method Body Modified]` |
| 🟡 `MOD` | [`Version.cs`](Changes/assembly_valheim/Version.md) | *Class level change* |

---

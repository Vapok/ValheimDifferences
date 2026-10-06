# Valheim API & Assembly Diff: `1.0.16` $\rightarrow$ `1.0.17`

> Automated decompilation comparison, mod impact report, and transpiler IL safety audit generated between Valheim version **1.0.16** and **1.0.17**.
>
> 🛡️ **Unity Asset Diff**: [View Detailed Unity Asset Difference Report](Changes/assets/Valheim_Assets_Diff.md)

## 📊 Executive Summary

| Metric | Count |
| :--- | :--- |
| **Assemblies Changed** | `1` / `9` |
| **Game Classes Modified** | `5` |
| **Game Classes Added** | `0` |
| **Game Classes Deleted** | `0` |
| **Total Lines Added** | `+35` |
| **Total Lines Removed** | `-6` |
| **High Risk Mod Patches** | `0` mod(s) |
| **Medium Risk Mod Patches** | `4` mod(s) |
| **Transpiler Hooks Audited** | `5` total (`5` safe / `0` caution / `0` critical) |

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
      <td><code>ItemData.GetWeight</code></td>
      <td><code>ItemDrop.cs:16</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'ItemData' and method 'GetWeight' are 100% UNCHANGED.</em></td>
    </tr>
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
      <td><code>InventoryGui.cs:342</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'InventoryGui' and method 'Update' are 100% UNCHANGED.</em></td>
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

✅ **Verified Safe**: None of the `0` modified Unity assets are referenced by active workspace mods.

## 🎯 Mod Impact Assessment

Scans all workspace mod projects for Harmony patches, transpilers, and references against modified game classes.

| Mod Project | Risk Level | Direct Patches on Changed Methods | Patches on Modified Classes | Touched Game Classes |
| :--- | :---: | :--- | :--- | :--- |
| **`AdventureBackpacks`** | 🟡 MEDIUM | *None* | `Inventory.Changed`<br>`Inventory.RemoveItem`<br>`Inventory.RemoveItem`<br>`Inventory.RemoveOneItem`<br>`Inventory.CanAddItem`<br>`Inventory.AddItem`<br>`Inventory.AddItem`<br>`Inventory.RemoveItem`<br>`Inventory.CountItems`<br>`Inventory.HaveItem`<br>`Inventory.MoveAll`<br>`Inventory.MoveItemToThis`<br>`Inventory.MoveItemToThis`<br>`Inventory.UpdateTotalWeight`<br>`Inventory.IsTeleportable` | `Inventory`, `ItemDrop`, `Version` |
| **`AutoFeedRedux`** | 🟢 LOW | *None* | *None* | `Inventory`, `ItemDrop`, `Version` |
| **`BepInEx.ConfigDrawers`** | 🟢 LOW | *None* | *None* | `Version` |
| **`BetterSleepBruh`** | 🟢 LOW | *None* | *None* | `Version`, `ZDOMan` |
| **`ConsoleBuddy`** | 🟢 LOW | *None* | *None* | `Version` |
| **`DoorOpenerBruh`** | 🟢 LOW | *None* | *None* | `ItemDrop`, `Version` |
| **`FastItemTransfer`** | 🟢 LOW | *None* | *None* | `Inventory`, `ItemDrop`, `Version` |
| **`NoFogBruh`** | 🟢 LOW | *None* | *None* | `Version` |
| **`RandomSpawnPointBruh`** | 🟢 LOW | *None* | *None* | `Inventory`, `ItemDrop`, `Version` |
| **`SaveYourLuckBruh`** | 🟢 LOW | *None* | *None* | `Version` |
| **`ShieldMeBruh`** | 🟡 MEDIUM | *None* | `Inventory.MoveItemToThis`<br>`Inventory.MoveItemToThis`<br>`Inventory.RemoveItem` | `Inventory`, `ItemDrop`, `Version` |
| **`TheQueensDeadBruh`** | 🟢 LOW | *None* | *None* | `Version` |
| **`Vapok.Common`** | 🟢 LOW | *None* | *None* | `Inventory`, `ItemDrop`, `Version` |
| **`WardMeBruh`** | 🟡 MEDIUM | *None* | `ZDOMan.HandleDestroyedZDO` | `Inventory`, `ItemDrop`, `Version`, `ZDOMan` |
| **`XPortalNetworks`** | 🟡 MEDIUM | *None* | `ZDOMan.ConnectPortals` | `ItemDrop`, `Version`, `ZDOMan` |

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
| [`assembly_valheim.dll`](#assembly_valheim) | `5` | `0` | `0` | `+35` / `-6` |

---

## 🔧 Assembly: `assembly_valheim.dll` <a id="assembly_valheim"></a>

**Changes Summary:** `5` modified, `0` added, `0` deleted (`+35` / `-6` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`Inventory.cs`](Changes/assembly_valheim/Inventory.md) | *Class level change* |
| 🟡 `MOD` | [`ItemDrop.cs`](Changes/assembly_valheim/ItemDrop.md) | `private void OnValidate()`<br>`public void ResetVariantIfInvalid()` |
| 🟡 `MOD` | [`VariantDialog.cs`](Changes/assembly_valheim/VariantDialog.md) | *Class level change* |
| 🟡 `MOD` | [`Version.cs`](Changes/assembly_valheim/Version.md) | *Class level change* |
| 🟡 `MOD` | [`ZDOMan.cs`](Changes/assembly_valheim/ZDOMan.md) | *Class level change* |

---

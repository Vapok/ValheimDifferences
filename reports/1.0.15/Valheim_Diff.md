# Valheim API & Assembly Diff: `1.0.14` $\rightarrow$ `1.0.15`

> Automated decompilation comparison, mod impact report, and transpiler IL safety audit generated between Valheim version **1.0.14** and **1.0.15**.

## 📊 Executive Summary

| Metric | Count |
| :--- | :--- |
| **Assemblies Changed** | `1` / `9` |
| **Game Classes Modified** | `6` |
| **Game Classes Added** | `0` |
| **Game Classes Deleted** | `0` |
| **Total Lines Added** | `+23` |
| **Total Lines Removed** | `-22` |
| **High Risk Mod Patches** | `0` mod(s) |
| **Medium Risk Mod Patches** | `3` mod(s) |
| **Transpiler Hooks Audited** | `11` total (`11` safe / `0` caution / `0` critical) |

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
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>InventoryGui.Update</code></td>
      <td><code>InventoryGui.cs:308</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'InventoryGui' was modified elsewhere, but method 'Update' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>InventoryGui.SetupRequirement</code></td>
      <td><code>InventoryGui.cs:534</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'InventoryGui' was modified elsewhere, but method 'SetupRequirement' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>ItemData.GetWeight</code></td>
      <td><code>ItemDrop.cs:14</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'ItemData' and method 'GetWeight' are 100% UNCHANGED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>Player.HaveRequirementItems</code></td>
      <td><code>Player.cs:172</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'Player' and method 'HaveRequirementItems' are 100% UNCHANGED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>Player.ConsumeResources</code></td>
      <td><code>Player.cs:297</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'Player' and method 'ConsumeResources' are 100% UNCHANGED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>Humanoid.UpdateEquipmentStatusEffects</code></td>
      <td><code>Humanoid.cs:17</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'Humanoid' and method 'UpdateEquipmentStatusEffects' are 100% UNCHANGED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>NoFogBruh</code></strong></td>
      <td><code>PostProcessingBehaviour.OnPreRender</code></td>
      <td><code>DisableFogComponent.cs:297</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'PostProcessingBehaviour' and method 'OnPreRender' are 100% UNCHANGED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>Vapok.Common</code></strong></td>
      <td><code>InventoryGui.UpdateRecipe</code></td>
      <td><code>ItemManager.cs:2159</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'InventoryGui' was modified elsewhere, but method 'UpdateRecipe' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>Vapok.Common</code></strong></td>
      <td><code>InventoryGui.SetupRequirementList</code></td>
      <td><code>ItemManager.cs:2160</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'InventoryGui' was modified elsewhere, but method 'SetupRequirementList' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>Vapok.Common</code></strong></td>
      <td><code>PieceTable.UpdateAvailable</code></td>
      <td><code>PieceManager.cs:1201</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'PieceTable' and method 'UpdateAvailable' are 100% UNCHANGED.</em></td>
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

## 🎯 Mod Impact Assessment

Scans all workspace mod projects for Harmony patches, transpilers, and references against modified game classes.

| Mod Project | Risk Level | Direct Patches on Changed Methods | Patches on Modified Classes | Touched Game Classes |
| :--- | :---: | :--- | :--- | :--- |
| **`AdventureBackpacks`** | 🟡 MEDIUM | *None* | `InventoryGui.OnRightClickItem`<br>`InventoryGrid.UpdateGui`<br>`Inventory.Changed`<br>`InventoryGui.OnDropOutside`<br>`Inventory.RemoveItem`<br>`Inventory.RemoveItem`<br>`Inventory.RemoveOneItem`<br>`Inventory.CanAddItem`<br>`Inventory.AddItem`<br>`Inventory.RemoveItem`<br>`InventoryGrid.DropItem`<br>`Inventory.MoveAll`<br>`Inventory.MoveItemToThis`<br>`Inventory.MoveItemToThis`<br>`Inventory.UpdateTotalWeight`<br>`Inventory.IsTeleportable`<br>`InventoryGui.DoCrafting`<br>`InventoryGui.OnSelectedItem`<br>`InventoryGui.Update`<br>`InventoryGui.SetupRequirement` | `Inventory`, `InventoryGrid`, `InventoryGui`, `ItemDrop`, `Version` |
| **`AutoFeedRedux`** | 🟢 LOW | *None* | *None* | `ItemDrop`, `Version` |
| **`BepInEx.ConfigDrawers`** | 🟢 LOW | *None* | *None* | `Version` |
| **`BetterSleepBruh`** | 🟢 LOW | *None* | *None* | `Version` |
| **`ConsoleBuddy`** | 🟢 LOW | *None* | *None* | `Version` |
| **`DoorOpenerBruh`** | 🟢 LOW | *None* | *None* | `ItemDrop`, `Version` |
| **`FastItemTransfer`** | 🟡 MEDIUM | *None* | `InventoryGui.OnRightClickItem` | `Inventory`, `InventoryGrid`, `InventoryGui`, `ItemDrop`, `Version` |
| **`NoFogBruh`** | 🟢 LOW | *None* | *None* | `Version` |
| **`RandomSpawnPointBruh`** | 🟢 LOW | *None* | *None* | `Version` |
| **`ShieldMeBruh`** | 🟡 MEDIUM | *None* | `InventoryGui.Show`<br>`Inventory.MoveItemToThis`<br>`Inventory.MoveItemToThis`<br>`Inventory.RemoveItem`<br>`InventoryGrid.DropItem`<br>`InventoryGrid.UpdateGui` | `Inventory`, `InventoryGrid`, `InventoryGui`, `ItemDrop`, `Version` |
| **`TheQueensDeadBruh`** | 🟢 LOW | *None* | *None* | `Version` |
| **`Vapok.Common`** | 🟢 LOW | *None* | *None* | `Inventory`, `InventoryGui`, `ItemDrop`, `Version` |
| **`XPortalNetworks`** | 🟢 LOW | *None* | *None* | `ItemDrop`, `Version` |

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
| [`assembly_valheim.dll`](#assembly_valheim) | `6` | `0` | `0` | `+23` / `-22` |

---

## 🔧 Assembly: `assembly_valheim.dll` <a id="assembly_valheim"></a>

**Changes Summary:** `6` modified, `0` added, `0` deleted (`+23` / `-22` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`Inventory.cs`](Changes/assembly_valheim/Inventory.md) | *Class level change* |
| 🟡 `MOD` | [`InventoryGrid.cs`](Changes/assembly_valheim/InventoryGrid.md) | *Class level change* |
| 🟡 `MOD` | [`InventoryGui.cs`](Changes/assembly_valheim/InventoryGui.md) | *Class level change* |
| 🟡 `MOD` | [`ItemDrop.cs`](Changes/assembly_valheim/ItemDrop.md) | *Class level change* |
| 🟡 `MOD` | [`TerrainComp.cs`](Changes/assembly_valheim/TerrainComp.md) | *Class level change* |
| 🟡 `MOD` | [`Version.cs`](Changes/assembly_valheim/Version.md) | *Class level change* |

---

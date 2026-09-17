# Valheim API & Assembly Diff: `1.0.12` $\rightarrow$ `1.0.14`

> Automated decompilation comparison, mod impact report, and transpiler IL safety audit generated between Valheim version **1.0.12** and **1.0.14**.

## 📊 Executive Summary

| Metric | Count |
| :--- | :--- |
| **Assemblies Changed** | `2` / `9` |
| **Game Classes Modified** | `32` |
| **Game Classes Added** | `0` |
| **Game Classes Deleted** | `0` |
| **Total Lines Added** | `+412` |
| **Total Lines Removed** | `-287` |
| **High Risk Mod Patches** | `0` mod(s) |
| **Medium Risk Mod Patches** | `11` mod(s) |
| **Transpiler Hooks Audited** | `17` total (`16` safe / `1` caution / `0` critical) |

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
      <td><code>ItemDrop.cs:14</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'ItemData' and method 'GetWeight' are 100% UNCHANGED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>Container.Awake</code></td>
      <td><code>Container.cs:68</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'Container' and method 'Awake' are 100% UNCHANGED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>Humanoid.UpdateEquipmentStatusEffects</code></td>
      <td><code>Humanoid.cs:17</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'Humanoid' was modified elsewhere, but method 'UpdateEquipmentStatusEffects' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>InventoryGui.Update</code></td>
      <td><code>InventoryGui.cs:272</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'InventoryGui' was modified elsewhere, but method 'Update' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>InventoryGui.SetupRequirement</code></td>
      <td><code>InventoryGui.cs:502</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'InventoryGui' was modified elsewhere, but method 'SetupRequirement' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>Player.HaveRequirementItems</code></td>
      <td><code>Player.cs:93</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'Player' was modified elsewhere, but method 'HaveRequirementItems' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>Player.ConsumeResources</code></td>
      <td><code>Player.cs:156</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'Player' was modified elsewhere, but method 'ConsumeResources' is UNTOUCHED.</em></td>
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
      <td><code>Inventory.FindFreeStackSpace</code></td>
      <td><code>CustomDataManager.cs:680</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'Inventory' was modified elsewhere, but method 'FindFreeStackSpace' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">⚠️ <code>CAUTION</code></td>
      <td><strong><code>Vapok.Common</code></strong></td>
      <td><code>Inventory.FindFreeStackItem</code></td>
      <td><code>CustomDataManager.cs:681</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Target method 'Inventory.FindFreeStackItem' was MODIFIED in this update. Review recommended to verify IL instructions.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>Vapok.Common</code></strong></td>
      <td><code>ItemDrop.AutoStackItems</code></td>
      <td><code>CustomDataManager.cs:683</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'ItemDrop' and method 'AutoStackItems' are 100% UNCHANGED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>Vapok.Common</code></strong></td>
      <td><code>InventoryGui.DoCrafting</code></td>
      <td><code>CustomDataManager.cs:685</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'InventoryGui' was modified elsewhere, but method 'DoCrafting' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>Vapok.Common</code></strong></td>
      <td><code>ItemDrop.Awake</code></td>
      <td><code>CustomDataManager.cs:695</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'ItemDrop' and method 'Awake' are 100% UNCHANGED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>Vapok.Common</code></strong></td>
      <td><code>InventoryGui.UpdateRecipe</code></td>
      <td><code>ItemManager.cs:1848</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'InventoryGui' was modified elsewhere, but method 'UpdateRecipe' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>Vapok.Common</code></strong></td>
      <td><code>InventoryGui.SetupRequirementList</code></td>
      <td><code>ItemManager.cs:1849</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'InventoryGui' was modified elsewhere, but method 'SetupRequirementList' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>Vapok.Common</code></strong></td>
      <td><code>PieceTable.UpdateAvailable</code></td>
      <td><code>PieceManager.cs:1096</code></td>
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
| **`AdventureBackpacks`** | 🟡 MEDIUM | *None* | `InventoryGui.OnRightClickItem`<br>`Humanoid.UseItem`<br>`InventoryGrid.UpdateGui`<br>`SEMan.RemoveStatusEffect`<br>`FejdStartup.Start`<br>`Humanoid.UpdateEquipmentStatusEffects`<br>`Humanoid.UnequipItem`<br>`Humanoid.EquipItem`<br>`Inventory.Changed`<br>`InventoryGui.OnDropOutside`<br>`Humanoid.DropItem`<br>`Inventory.RemoveItem`<br>`Inventory.RemoveItem`<br>`Inventory.RemoveOneItem`<br>`Inventory.AddItem`<br>`Inventory.AddItem`<br>`InventoryGrid.DropItem`<br>`Inventory.MoveAll`<br>`Inventory.MoveItemToThis`<br>`Inventory.MoveItemToThis`<br>`Inventory.UpdateTotalWeight`<br>`Inventory.IsTeleportable`<br>`InventoryGui.DoCrafting`<br>`InventoryGui.OnSelectedItem`<br>`InventoryGui.Update`<br>`InventoryGui.SetupRequirement`<br>`Player.Awake`<br>`Player.HaveRequirementItems`<br>`Player.ConsumeResources` | `FejdStartup`, `Humanoid`, `Inventory`, `InventoryGrid`, `InventoryGui`, `Piece`, `Player`, `SEMan`, `Version`, `ZInput` |
| **`AutoFeedRedux`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake` | `FejdStartup`, `Humanoid`, `Player`, `Version` |
| **`BetterSleepBruh`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake`<br>`ZNet.UpdateNetTime` | `FejdStartup`, `Minimap`, `Player`, `Terminal`, `Version`, `ZNet` |
| **`ConsoleBuddy`** | 🟡 MEDIUM | *None* | `Terminal.AddString`<br>`FejdStartup.Awake` | `FejdStartup`, `Terminal`, `Version` |
| **`DoorOpenerBruh`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake`<br>`Player.SetLocalPlayer` | `FejdStartup`, `Piece`, `Player`, `Version` |
| **`FastItemTransfer`** | 🟡 MEDIUM | *None* | `InventoryGui.OnRightClickItem`<br>`Humanoid.UseItem`<br>`FejdStartup.Awake` | `FejdStartup`, `Humanoid`, `Inventory`, `InventoryGrid`, `InventoryGui`, `Player`, `Version` |
| **`NoFogBruh`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake` | `FejdStartup`, `Version` |
| **`RandomSpawnPointBruh`** | 🟢 LOW | *None* | *None* | `Player`, `Version` |
| **`ShieldMeBruh`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake`<br>`InventoryGui.Show`<br>`Player.SetLocalPlayer`<br>`Player.OnDeath`<br>`Humanoid.EquipItem`<br>`Humanoid.UnequipItem`<br>`InventoryGrid.UpdateGui`<br>`Inventory.MoveItemToThis`<br>`Inventory.MoveItemToThis`<br>`Inventory.RemoveItem`<br>`InventoryGrid.DropItem` | `FejdStartup`, `Humanoid`, `Inventory`, `InventoryGrid`, `InventoryGui`, `Player`, `Version` |
| **`TheQueensDeadBruh`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake` | `FejdStartup`, `Version` |
| **`Vapok.Common`** | 🟡 MEDIUM | *None* | `ZNet.OnNewConnection` | `Attack`, `Character`, `FejdStartup`, `Inventory`, `InventoryGui`, `Minimap`, `Piece`, `Player`, `Terminal`, `Version`, `ZNet` |
| **`XPortalNetworks`** | 🟡 MEDIUM | *None* | `Piece.SetCreator`<br>`Piece.CanBeRemoved`<br>`Player.PlacePiece`<br>`ZNet.RPC_PeerInfo` | `Minimap`, `Piece`, `Player`, `Version`, `ZInput`, `ZNet` |

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
| [`assembly_utils.dll`](#assembly_utils) | `1` | `0` | `0` | `+97` / `-53` |
| [`assembly_valheim.dll`](#assembly_valheim) | `31` | `0` | `0` | `+315` / `-234` |

---

## 🔧 Assembly: `assembly_utils.dll` <a id="assembly_utils"></a>

**Changes Summary:** `1` modified, `0` added, `0` deleted (`+97` / `-53` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`ZInput.cs`](Changes/assembly_utils/ZInput.md) | `private Vector2 ApplyDeadzoneVector(Vector2 value)`<br>`private Vector2 ApplyDeadzoneVector(Vector2 value, bool smooth)`<br>`private float ApplyDeadzoneFloat(float value)`<br>`private float ApplyDeadzoneFloat(float value, bool smooth)`<br>`private void ApplyDeadzoneToMagnitude(ref float magnitude)`<br>*...and 15 more* |

---

## 🔧 Assembly: `assembly_valheim.dll` <a id="assembly_valheim"></a>

**Changes Summary:** `31` modified, `0` added, `0` deleted (`+315` / `-234` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`Achievements.cs`](Changes/assembly_valheim/Achievements.md) | *Class level change* |
| 🟡 `MOD` | [`AltBiomeWorldData.cs`](Changes/assembly_valheim/AltBiomeWorldData.md) | *Class level change* |
| 🟡 `MOD` | [`Attack.cs`](Changes/assembly_valheim/Attack.md) | *Class level change* |
| 🟡 `MOD` | [`Character.cs`](Changes/assembly_valheim/Character.md) | *Class level change* |
| 🟡 `MOD` | [`CinematicsManager.cs`](Changes/assembly_valheim/CinematicsManager.md) | *Class level change* |
| 🟡 `MOD` | [`FejdStartup.cs`](Changes/assembly_valheim/FejdStartup.md) | `private IEnumerator PlayIntroCinematic()`<br>`private IEnumerator TryPlayIntroCinematic()` |
| 🟡 `MOD` | [`GameCamera.cs`](Changes/assembly_valheim/GameCamera.md) | *Class level change* |
| 🟡 `MOD` | [`GraphicsSettingsManager.cs`](Changes/assembly_valheim/GraphicsSettingsManager.md) | `private static void ApplyShaderKeywords(in GraphicsSettingsState settings)`<br>`private void ApplyTesselation(in GraphicsSettingsState settings)` |
| 🟡 `MOD` | [`GrapplingPoint.cs`](Changes/assembly_valheim/GrapplingPoint.md) | *Class level change* |
| 🟡 `MOD` | [`Humanoid.cs`](Changes/assembly_valheim/Humanoid.md) | *Class level change* |
| 🟡 `MOD` | [`Inventory.cs`](Changes/assembly_valheim/Inventory.md) | *Class level change* |
| 🟡 `MOD` | [`InventoryGrid.cs`](Changes/assembly_valheim/InventoryGrid.md) | *Class level change* |
| 🟡 `MOD` | [`InventoryGui.cs`](Changes/assembly_valheim/InventoryGui.md) | *Class level change* |
| 🟡 `MOD` | [`Leviathan.cs`](Changes/assembly_valheim/Leviathan.md) | *Class level change* |
| 🟡 `MOD` | [`Minimap.cs`](Changes/assembly_valheim/Minimap.md) | *Class level change* |
| 🟡 `MOD` | [`Piece.cs`](Changes/assembly_valheim/Piece.md) | `public static void CheckLenientBuildAchUnlocked(Achievement buildAchievement, bool afterLocalPlayerExists, bool useTagStats)`<br>`public static void CheckLenientBuildAchUnlocked(Achievement buildAchievement, bool showPopup, bool useTagStats)` |
| 🟡 `MOD` | [`Player.cs`](Changes/assembly_valheim/Player.md) | *Class level change* |
| 🟡 `MOD` | [`PlayerController.cs`](Changes/assembly_valheim/PlayerController.md) | *Class level change* |
| 🟡 `MOD` | [`PresentManager.cs`](Changes/assembly_valheim/PresentManager.md) | `public void RequestTargetFrameRate(int targetFrameRate, int targetRefreshRate)`<br>`public void RequestTargetFrameRate(int value)` |
| 🟡 `MOD` | [`Projectile.cs`](Changes/assembly_valheim/Projectile.md) | *Class level change* |
| 🟡 `MOD` | [`ReportUser.cs`](Changes/assembly_valheim/ReportUser.md) | *Class level change* |
| 🟡 `MOD` | [`SEMan.cs`](Changes/assembly_valheim/SEMan.md) | *Class level change* |
| 🟡 `MOD` | [`StaticRotation.cs`](Changes/assembly_valheim/StaticRotation.md) | *Class level change* |
| 🟡 `MOD` | [`Terminal.cs`](Changes/assembly_valheim/Terminal.md) | *Class level change* |
| 🟡 `MOD` | [`TerrainComp.cs`](Changes/assembly_valheim/TerrainComp.md) | `private TerrainComp GetNeighbor(Vector3 worldPos, int x, int y, float radius)`<br>`private TerrainComp TryGetNeighbor(Vector3 worldPos, int x, int y, float radius)` |
| 🟡 `MOD` | [`Valheim.SettingsGui/AccessibilitySettings.cs`](Changes/assembly_valheim/AccessibilitySettings.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.SettingsGui/GamepadSettings.cs`](Changes/assembly_valheim/GamepadSettings.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.SettingsGui/GameplaySettings.cs`](Changes/assembly_valheim/GameplaySettings.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.SettingsGui/KeyboardMouseSettings.cs`](Changes/assembly_valheim/KeyboardMouseSettings.md) | `public void SetConsoleEnabled(bool enabled)` |
| 🟡 `MOD` | [`Version.cs`](Changes/assembly_valheim/Version.md) | *Class level change* |
| 🟡 `MOD` | [`ZNet.cs`](Changes/assembly_valheim/ZNet.md) | *Class level change* |

---

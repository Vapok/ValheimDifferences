# Valheim API & Assembly Diff: `1.0.17` $\rightarrow$ `1.0.20`

> Automated decompilation comparison, mod impact report, and transpiler IL safety audit generated between Valheim version **1.0.17** and **1.0.20**.
>
> 🛡️ **Unity Asset Diff**: [View Detailed Unity Asset Difference Report](Changes/assets/Valheim_Assets_Diff.md)

## 📊 Executive Summary

| Metric | Count |
| :--- | :--- |
| **Assemblies Changed** | `1` / `9` |
| **Game Classes Modified** | `30` |
| **Game Classes Added** | `1` |
| **Game Classes Deleted** | `0` |
| **Total Lines Added** | `+215` |
| **Total Lines Removed** | `-100` |
| **High Risk Mod Patches** | `0` mod(s) |
| **Medium Risk Mod Patches** | `15` mod(s) |
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
      <td><code>ItemData.GetWeight</code></td>
      <td><code>ItemDrop.cs:17</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'ItemData' and method 'GetWeight' are 100% UNCHANGED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>InventoryGui.Update</code></td>
      <td><code>InventoryGui.cs:378</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'InventoryGui' was modified elsewhere, but method 'Update' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>Player.SetControls</code></td>
      <td><code>PlayerSetControlsPatch.cs:9</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'Player' was modified elsewhere, but method 'SetControls' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>BaitMeBruh</code></strong></td>
      <td><code>Player.UpdateAttackBowDraw</code></td>
      <td><code>PlayerUpdateAttackBowDrawPatch.cs:8</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'Player' was modified elsewhere, but method 'UpdateAttackBowDraw' is UNTOUCHED.</em></td>
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
| **`AdventureBackpacks`** | 🟡 MEDIUM | *None* | `InventoryGui.OnRightClickItem`<br>`FejdStartup.Start`<br>`Inventory.Changed`<br>`InventoryGui.OnDropOutside`<br>`Inventory.RemoveItem`<br>`Inventory.RemoveItem`<br>`Inventory.RemoveOneItem`<br>`Inventory.CanAddItem`<br>`Inventory.AddItem`<br>`Inventory.AddItem`<br>`Inventory.RemoveItem`<br>`Inventory.CountItems`<br>`Inventory.HaveItem`<br>`Inventory.MoveAll`<br>`Inventory.MoveItemToThis`<br>`Inventory.MoveItemToThis`<br>`Inventory.UpdateTotalWeight`<br>`Inventory.IsTeleportable`<br>`Container.TakeAll`<br>`Container.RPC_TakeAllResponse`<br>`Container.Interact`<br>`Container.Save`<br>`Container.Load`<br>`Container.Awake`<br>`Container.IsOwner`<br>`Container.IsInUse`<br>`Container.SetInUse`<br>`Container.CheckAccess`<br>`Container.StackAll`<br>`InventoryGui.DoCrafting`<br>`InventoryGui.OnSelectedItem`<br>`InventoryGui.Update`<br>`InventoryGui.SetupRequirement`<br>`InventoryGui.UpdateRecipeList`<br>`InventoryGui.UpdateRecipe`<br>`InventoryGui.OnCraftPressed`<br>`InventoryGui.Hide`<br>`InventoryGui.CloseContainer`<br>`InventoryGui.Show`<br>`InventoryGui.OnTakeAll`<br>`Player.HaveRequirements`<br>`Player.HaveRequirements`<br>`Player.HaveRequirementItems`<br>`Player.UpdatePlacement`<br>`Player.GetFirstRequiredItem`<br>`Player.OnDestroy`<br>`Player.OnDeath`<br>`Player.UpdateEnvStatusEffects`<br>`Player.ApplyArmorDamageMods`<br>`Player.GetBodyArmor`<br>`Player.Update` | `Container`, `FejdStartup`, `Inventory`, `InventoryGui`, `ItemDrop`, `Piece`, `Player`, `Version`, `ZNet` |
| **`AutoFeedRedux`** | 🟡 MEDIUM | *None* | `Container.Awake`<br>`Container.OnDestroyed`<br>`FejdStartup.Awake` | `Character`, `Container`, `FejdStartup`, `Inventory`, `ItemDrop`, `Player`, `Version` |
| **`BaitMeBruh`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake`<br>`Player.AttachStart`<br>`Player.CanMove`<br>`Player.SetControls`<br>`Player.OnInventoryChanged`<br>`Player.UpdateAttach`<br>`Player.UpdateKnownRecipesList`<br>`Player.UpdatePlacementGhost`<br>`Player.CheckKeyboardRadialPressed`<br>`Player.UpdateAttackBowDraw` | `Character`, `Container`, `CookingStation`, `FejdStartup`, `Inventory`, `InventoryGui`, `ItemDrop`, `Piece`, `Player`, `Version`, `ZoneSystem` |
| **`BepInEx.ConfigDrawers`** | 🟢 LOW | *None* | *None* | `Container`, `Version` |
| **`BetterSleepBruh`** | 🟡 MEDIUM | *None* | `Player.AttachStart`<br>`Player.AttachStop`<br>`FejdStartup.Awake`<br>`CookingStation.GetDeltaTime`<br>`Fermenter.GetFermentationTime`<br>`Smelter.GetDeltaTime`<br>`ZNet.UpdateNetTime`<br>`ZNet.SaveWorld` | `Console`, `CookingStation`, `FejdStartup`, `Fermenter`, `Minimap`, `Player`, `PlayerProfile`, `Smelter`, `Terminal`, `Version`, `World`, `ZDOMan`, `ZNet`, `ZPlayFabMatchmaking`, `ZSteamMatchmaking`, `ZoneSystem` |
| **`ConsoleBuddy`** | 🟡 MEDIUM | *None* | `Console.Awake`<br>`Terminal.AddString`<br>`FejdStartup.Awake` | `Console`, `FejdStartup`, `Terminal`, `Version` |
| **`DoorOpenerBruh`** | 🟡 MEDIUM | *None* | `Player.SetLocalPlayer`<br>`FejdStartup.Awake` | `FejdStartup`, `ItemDrop`, `Piece`, `Player`, `Version`, `World` |
| **`FastItemTransfer`** | 🟡 MEDIUM | *None* | `InventoryGui.OnRightClickItem`<br>`FejdStartup.Awake` | `FejdStartup`, `Inventory`, `InventoryGui`, `ItemDrop`, `Player`, `Version` |
| **`NoFogBruh`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake` | `FejdStartup`, `Version`, `World` |
| **`RandomSpawnPointBruh`** | 🟡 MEDIUM | *None* | `Terminal.InitTerminal`<br>`Minimap.UpdateExplore` | `Inventory`, `ItemDrop`, `Minimap`, `Player`, `Terminal`, `Version`, `ZoneSystem` |
| **`SaveYourLuckBruh`** | 🟡 MEDIUM | *None* | `Player.Save`<br>`Player.Load`<br>`Player.OnSpawned`<br>`Player.OnDestroy`<br>`CharacterDrop.GenerateDropList`<br>`FejdStartup.Awake` | `Character`, `CharacterDrop`, `FejdStartup`, `Player`, `Version`, `ZNet` |
| **`ShieldMeBruh`** | 🟡 MEDIUM | *None* | `Player.OnDeath`<br>`InventoryGui.Show`<br>`Player.SetLocalPlayer`<br>`FejdStartup.Awake`<br>`Inventory.MoveItemToThis`<br>`Inventory.MoveItemToThis`<br>`Inventory.RemoveItem` | `FejdStartup`, `Inventory`, `InventoryGui`, `ItemDrop`, `Player`, `PlayerProfile`, `Version` |
| **`TheQueensDeadBruh`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake` | `FejdStartup`, `Version`, `ZoneSystem` |
| **`Vapok.Common`** | 🟡 MEDIUM | *None* | `ZNet.OnNewConnection` | `Character`, `CharacterDrop`, `Console`, `Container`, `FejdStartup`, `Inventory`, `InventoryGui`, `ItemDrop`, `Minimap`, `Piece`, `Player`, `Smelter`, `Terminal`, `Version`, `World`, `ZNet`, `ZoneSystem` |
| **`WardMeBruh`** | 🟡 MEDIUM | *None* | `Player.UpdateFood`<br>`Character.RPC_Damage`<br>`Smelter.Awake`<br>`Minimap.UpdatePins`<br>`Player.UpdateEnvStatusEffects`<br>`Player.SetPlayerID`<br>`Player.OnSpawned`<br>`ZNet.RPC_CharacterID`<br>`ZNet.SaveWorld`<br>`ZNet.RPC_PlayerID`<br>`FejdStartup.Awake`<br>`ZDOMan.HandleDestroyedZDO`<br>`CookingStation.Awake`<br>`Player.GetComfortLevel`<br>`Player.InShelter`<br>`Player.UpdateEnvStatusEffects`<br>`Player.UpdateEnvStatusEffects`<br>`InventoryGui.UpdateContainer`<br>`Container.Awake`<br>`Container.Interact`<br>`Container.GetHoverText`<br>`Player.Update`<br>`Piece.DropResources` | `Character`, `Console`, `Container`, `CookingStation`, `FejdStartup`, `Inventory`, `InventoryGui`, `ItemDrop`, `Minimap`, `Piece`, `Player`, `PlayerProfile`, `Smelter`, `Version`, `World`, `ZDOMan`, `ZNet`, `ZoneSystem` |
| **`XPortalNetworks`** | 🟡 MEDIUM | *None* | `ZNet.RPC_PeerInfo`<br>`Piece.SetCreator`<br>`Piece.CanBeRemoved`<br>`ZDOMan.ConnectPortals` | `ItemDrop`, `Minimap`, `Piece`, `Player`, `Version`, `ZDOMan`, `ZNet`, `ZoneSystem` |

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
| [`assembly_valheim.dll`](#assembly_valheim) | `30` | `1` | `0` | `+215` / `-100` |

---

## 🔧 Assembly: `assembly_valheim.dll` <a id="assembly_valheim"></a>

**Changes Summary:** `30` modified, `1` added, `0` deleted (`+215` / `-100` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`Character.cs`](Changes/assembly_valheim/Character.md) | *Class level change* |
| 🟡 `MOD` | [`CharacterDrop.cs`](Changes/assembly_valheim/CharacterDrop.md) | *Class level change* |
| 🟢 `ADD` | [`CheatUtils.cs`](Changes/assembly_valheim/CheatUtils.md) | *Class level change* |
| 🟡 `MOD` | [`ChunkSaveMapping.cs`](Changes/assembly_valheim/ChunkSaveMapping.md) | *Class level change* |
| 🟡 `MOD` | [`Console.cs`](Changes/assembly_valheim/Console.md) | *Class level change* |
| 🟡 `MOD` | [`Container.cs`](Changes/assembly_valheim/Container.md) | *Class level change* |
| 🟡 `MOD` | [`CookingStation.cs`](Changes/assembly_valheim/CookingStation.md) | *Class level change* |
| 🟡 `MOD` | [`Destructible.cs`](Changes/assembly_valheim/Destructible.md) | *Class level change* |
| 🟡 `MOD` | [`DropOnDestroyed.cs`](Changes/assembly_valheim/DropOnDestroyed.md) | *Class level change* |
| 🟡 `MOD` | [`FejdStartup.cs`](Changes/assembly_valheim/FejdStartup.md) | *Class level change* |
| 🟡 `MOD` | [`Fermenter.cs`](Changes/assembly_valheim/Fermenter.md) | *Class level change* |
| 🟡 `MOD` | [`Inventory.cs`](Changes/assembly_valheim/Inventory.md) | *Class level change* |
| 🟡 `MOD` | [`InventoryGui.cs`](Changes/assembly_valheim/InventoryGui.md) | *Class level change* |
| 🟡 `MOD` | [`ItemDrop.cs`](Changes/assembly_valheim/ItemDrop.md) | `public void EnsureValid()`<br>`public void ResetVariantIfInvalid()` |
| 🟡 `MOD` | [`MasterClient.cs`](Changes/assembly_valheim/MasterClient.md) | *Class level change* |
| 🟡 `MOD` | [`Minimap.cs`](Changes/assembly_valheim/Minimap.md) | *Class level change* |
| 🟡 `MOD` | [`Piece.cs`](Changes/assembly_valheim/Piece.md) | *Class level change* |
| 🟡 `MOD` | [`Player.cs`](Changes/assembly_valheim/Player.md) | `public float GetItemUpgradeChance(int hash)` |
| 🟡 `MOD` | [`PlayerProfile.cs`](Changes/assembly_valheim/PlayerProfile.md) | *Class level change* |
| 🟡 `MOD` | [`Ragdoll.cs`](Changes/assembly_valheim/Ragdoll.md) | *Class level change* |
| 🟡 `MOD` | [`ServerListGui.cs`](Changes/assembly_valheim/ServerListGui.md) | *Class level change* |
| 🟡 `MOD` | [`Smelter.cs`](Changes/assembly_valheim/Smelter.md) | *Class level change* |
| 🟡 `MOD` | [`Terminal.cs`](Changes/assembly_valheim/Terminal.md) | *Class level change* |
| 🟡 `MOD` | [`Version.cs`](Changes/assembly_valheim/Version.md) | *Class level change* |
| 🟡 `MOD` | [`World.cs`](Changes/assembly_valheim/World.md) | *Class level change* |
| 🟡 `MOD` | [`ZDOMan.cs`](Changes/assembly_valheim/ZDOMan.md) | *Class level change* |
| 🟡 `MOD` | [`ZNet.cs`](Changes/assembly_valheim/ZNet.md) | *Class level change* |
| 🟡 `MOD` | [`ZPlayFabLobbySearch.cs`](Changes/assembly_valheim/ZPlayFabLobbySearch.md) | *Class level change* |
| 🟡 `MOD` | [`ZPlayFabMatchmaking.cs`](Changes/assembly_valheim/ZPlayFabMatchmaking.md) | *Class level change* |
| 🟡 `MOD` | [`ZSteamMatchmaking.cs`](Changes/assembly_valheim/ZSteamMatchmaking.md) | *Class level change* |
| 🟡 `MOD` | [`ZoneSystem.cs`](Changes/assembly_valheim/ZoneSystem.md) | *Class level change* |

---

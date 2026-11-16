# Valheim API & Assembly Diff: `1.0.20` $\rightarrow$ `1.0.21`

> Automated decompilation comparison, mod impact report, and transpiler IL safety audit generated between Valheim version **1.0.20** and **1.0.21**.
>
> 🛡️ **Unity Asset Diff**: [View Detailed Unity Asset Difference Report](Changes/assets/Valheim_Assets_Diff.md)

## 📊 Executive Summary

| Metric | Count |
| :--- | :--- |
| **Assemblies Changed** | `2` / `9` |
| **Game Classes Modified** | `35` |
| **Game Classes Added** | `0` |
| **Game Classes Deleted** | `0` |
| **Total Lines Added** | `+338` |
| **Total Lines Removed** | `-142` |
| **Critical Breaking Mods** | `0` mod(s) |
| **High Risk Mod Patches** | `2` mod(s) |
| **Medium Risk Mod Patches** | `12` mod(s) |
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
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>InventoryGui.Update</code></td>
      <td><code>InventoryGui.cs:385</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'InventoryGui' was modified elsewhere, but method 'Update' is UNTOUCHED.</em></td>
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

Scans all workspace mod projects for Harmony patches, transpilers, and breaking API references against modified game classes.

| Mod Project | Risk Level | Breaking API & Direct Hook Issues | Patches on Modified Classes | Touched Game Classes |
| :--- | :---: | :--- | :--- | :--- |
| **`AdventureBackpacks`** | 🔴 HIGH | ⚠️ `FejdStartup.Start` (Postfix)<br>⚠️ `ArmorStand.UpdateAttach` (Prefix)<br>⚠️ `ItemStand.UpdateAttach` (Prefix) | `InventoryGui.OnRightClickItem`<br>`Player.HaveRequirements`<br>`Player.HaveRequirements`<br>`Player.HaveRequirementItems`<br>`Player.UpdatePlacement`<br>`Player.GetFirstRequiredItem`<br>`Player.OnDestroy`<br>`Player.OnDeath`<br>`Player.UpdateEnvStatusEffects`<br>`Player.ApplyArmorDamageMods`<br>`Player.GetBodyArmor`<br>`Player.Update`<br>`ArmorStand.UseItem`<br>`ItemStand.UseItem`<br>`InventoryGui.OnDropOutside`<br>`InventoryGui.DoCrafting`<br>`InventoryGui.OnSelectedItem`<br>`InventoryGui.Update`<br>`InventoryGui.SetupRequirement`<br>`InventoryGui.UpdateRecipeList`<br>`InventoryGui.UpdateRecipe`<br>`InventoryGui.OnCraftPressed`<br>`InventoryGui.Hide`<br>`InventoryGui.CloseContainer`<br>`InventoryGui.Show`<br>`InventoryGui.OnTakeAll` | `ArmorStand`, `FejdStartup`, `InventoryGui`, `ItemDrop`, `ItemStand`, `Piece`, `Player`, `StatusEffect`, `Version` |
| **`AutoFeedRedux`** | 🟡 MEDIUM | *None* | `WearNTear.Damage`<br>`FejdStartup.Awake` | `Character`, `FejdStartup`, `ItemDrop`, `Player`, `Version`, `WearNTear` |
| **`BaitMeBruh`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake`<br>`Player.AttachStart`<br>`Player.CanMove`<br>`Player.SetControls`<br>`Player.OnInventoryChanged`<br>`Player.UpdateAttach`<br>`Player.UpdateKnownRecipesList`<br>`Player.UpdatePlacementGhost`<br>`Player.CheckKeyboardRadialPressed`<br>`Player.UpdateAttackBowDraw` | `Character`, `Chat`, `CookingStation`, `FejdStartup`, `InventoryGui`, `ItemDrop`, `ItemStand`, `Piece`, `Player`, `Ship`, `Version`, `WearNTear` |
| **`BepInEx.ConfigDrawers`** | 🟢 LOW | *None* | *None* | `Version` |
| **`BetterSleepBruh`** | 🟡 MEDIUM | *None* | `Player.AttachStart`<br>`Player.AttachStop`<br>`FejdStartup.Awake`<br>`CookingStation.GetDeltaTime`<br>`Ship.UpdateWaterForce` | `CookingStation`, `FejdStartup`, `FileHelpers`, `Minimap`, `Player`, `PlayerProfile`, `SaveSystem`, `SaveWithBackups`, `Ship`, `Terminal`, `Version` |
| **`ConsoleBuddy`** | 🟡 MEDIUM | *None* | `Terminal.AddString`<br>`FejdStartup.Awake` | `FejdStartup`, `Terminal`, `Version` |
| **`DoorOpenerBruh`** | 🟡 MEDIUM | *None* | `Player.SetLocalPlayer`<br>`FejdStartup.Awake` | `FejdStartup`, `ItemDrop`, `Piece`, `Player`, `Version` |
| **`FastItemTransfer`** | 🟡 MEDIUM | *None* | `InventoryGui.OnRightClickItem`<br>`FejdStartup.Awake` | `FejdStartup`, `InventoryGui`, `ItemDrop`, `Player`, `Version` |
| **`NoFogBruh`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake` | `FejdStartup`, `Version` |
| **`RandomSpawnPointBruh`** | 🔴 HIGH | ⚠️ `Terminal.InitTerminal` (Postfix) | `Minimap.UpdateExplore` | `ItemDrop`, `Minimap`, `Player`, `Terminal`, `Version` |
| **`SaveYourLuckBruh`** | 🟡 MEDIUM | *None* | `Player.Save`<br>`Player.OnSpawned`<br>`Player.OnDestroy`<br>`Player.Load`<br>`FejdStartup.Awake`<br>`FejdStartup.OnNewCharacterDone` | `Character`, `FejdStartup`, `Player`, `Version` |
| **`ShieldMeBruh`** | 🟡 MEDIUM | *None* | `Player.OnDeath`<br>`InventoryGui.Show`<br>`Player.SetLocalPlayer`<br>`FejdStartup.Awake` | `FejdStartup`, `InventoryGui`, `ItemDrop`, `Player`, `PlayerProfile`, `Version` |
| **`TheQueensDeadBruh`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake` | `FejdStartup`, `Version` |
| **`Vapok.Common`** | 🟢 LOW | *None* | *None* | `Character`, `FejdStartup`, `InventoryGui`, `ItemDrop`, `Minimap`, `Piece`, `Player`, `StatusEffect`, `Terminal`, `Version` |
| **`WardMeBruh`** | 🟡 MEDIUM | *None* | `Player.UpdateFood`<br>`Character.RPC_Damage`<br>`Minimap.UpdatePins`<br>`Player.SetPlayerID`<br>`Player.OnSpawned`<br>`FejdStartup.Awake`<br>`CookingStation.Awake`<br>`Player.GetComfortLevel`<br>`Player.InShelter`<br>`Player.UpdateEnvStatusEffects`<br>`Player.UpdateEnvStatusEffects`<br>`ShieldDomeImageEffect.OnRenderImage`<br>`ShieldDomeImageEffect.OnDestroy`<br>`WearNTear.HaveRoof`<br>`WearNTear.HaveAshRoof`<br>`WearNTear.UpdateWear`<br>`WearNTear.Destroy`<br>`InventoryGui.UpdateContainer`<br>`Player.Update`<br>`Piece.DropResources`<br>`Player.UpdateEnvStatusEffects` | `Character`, `Chat`, `CookingStation`, `FejdStartup`, `GraphicsSettingsManager`, `InventoryGui`, `ItemDrop`, `Minimap`, `Piece`, `Player`, `PlayerProfile`, `SaveSystem`, `ShieldDomeImageEffect`, `StatusEffect`, `Version`, `WearNTear` |
| **`XPortalNetworks`** | 🟡 MEDIUM | *None* | `Piece.SetCreator`<br>`Piece.CanBeRemoved`<br>`WearNTear.OnPlaced`<br>`WearNTear.Destroy` | `ItemDrop`, `Minimap`, `Piece`, `Player`, `Version`, `WearNTear` |

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
| [`assembly_utils.dll`](#assembly_utils) | `1` | `0` | `0` | `+18` / `-5` |
| [`assembly_valheim.dll`](#assembly_valheim) | `34` | `0` | `0` | `+320` / `-137` |

---

## 🔧 Assembly: `assembly_utils.dll` <a id="assembly_utils"></a>

**Changes Summary:** `1` modified, `0` added, `0` deleted (`+18` / `-5` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`FileHelpers.cs`](Changes/assembly_utils/FileHelpers.md) | `CloudFileWriteInChunks() [Method Body Modified]`<br>`GetFileSizes() [Method Body Modified]`<br>`GetSourceString() [Method Body Modified]`<br>`ValidPath() [Method Body Modified]`<br>`public static bool ValidPath(string name)` |

---

## 🔧 Assembly: `assembly_valheim.dll` <a id="assembly_valheim"></a>

**Changes Summary:** `34` modified, `0` added, `0` deleted (`+320` / `-137` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`AchievementsGui.cs`](Changes/assembly_valheim/AchievementsGui.md) | `CloseDetails() [Method Body Modified]`<br>`NavigateAchievements() [Method Body Modified]`<br>`OnDisable() [Method Body Modified]`<br>`OnEnable() [Method Body Modified]`<br>`ResetSelected() [Method Body Modified]`<br>*...and 4 more* |
| 🟡 `MOD` | [`ArmorStand.cs`](Changes/assembly_valheim/ArmorStand.md) | `UpdateAttach() [Method Body Modified]` |
| 🟡 `MOD` | [`BlockCheckHandler.cs`](Changes/assembly_valheim/BlockCheckHandler.md) | `CheckForBlocked() [Method Body Modified]`<br>`OnRelationsChanged() [Method Body Modified]` |
| 🟡 `MOD` | [`Character.cs`](Changes/assembly_valheim/Character.md) | `ApplySlippery() [Method Body Modified]`<br>`UpdateWalking() [Method Body Modified]` |
| 🟡 `MOD` | [`Chat.cs`](Changes/assembly_valheim/Chat.md) | `UpdateNpcTexts() [Method Body Modified]` |
| 🟡 `MOD` | [`CinematicsManager.cs`](Changes/assembly_valheim/CinematicsManager.md) | `Stop() [Method Body Modified]` |
| 🟡 `MOD` | [`CookingStation.cs`](Changes/assembly_valheim/CookingStation.md) | `DropAllItems() [Method Body Modified]`<br>`GetFuel() [Method Body Modified]`<br>`RPC_AddItem() [Method Body Modified]`<br>`RPC_RemoveDoneItem() [Method Body Modified]`<br>`SetSlot() [Method Body Modified]`<br>*...and 5 more* |
| 🟡 `MOD` | [`DamageText.cs`](Changes/assembly_valheim/DamageText.md) | `UpdateWorldTexts() [Method Body Modified]` |
| 🟡 `MOD` | [`Feast.cs`](Changes/assembly_valheim/Feast.md) | `GetHoverText() [Method Body Modified]` |
| 🟡 `MOD` | [`FejdStartup.cs`](Changes/assembly_valheim/FejdStartup.md) | `OnWorldStart() [Method Body Modified]`<br>`Start() [Method Body Modified]` |
| 🟡 `MOD` | [`GraphicsSettingsManager.cs`](Changes/assembly_valheim/GraphicsSettingsManager.md) | `RequestTargetFrameRateFromPreset() [Method Body Modified]`<br>`ScaleTarget3DResolutionByCurrentRenderingArea() [Method Body Modified]` |
| 🟡 `MOD` | [`GrapplingPoint.cs`](Changes/assembly_valheim/GrapplingPoint.md) | `Activate() [Method Body Modified]`<br>`Pull() [Method Body Modified]` |
| 🟡 `MOD` | [`InventoryGui.cs`](Changes/assembly_valheim/InventoryGui.md) | `Awake() [Method Body Modified]`<br>`OnReleasedOutside() [Method Body Modified]`<br>`OnStackAll() [Method Body Modified]`<br>`private void OnReleasedOutside()` |
| 🟡 `MOD` | [`ItemDrop.cs`](Changes/assembly_valheim/ItemDrop.md) | `OnValidate() [Method Body Modified]` |
| 🟡 `MOD` | [`ItemStand.cs`](Changes/assembly_valheim/ItemStand.md) | `UpdateAttach() [Method Body Modified]` |
| 🟡 `MOD` | [`Minimap.cs`](Changes/assembly_valheim/Minimap.md) | `OnMapDblClick() [Method Body Modified]` |
| 🟡 `MOD` | [`Piece.cs`](Changes/assembly_valheim/Piece.md) | `CheckClusteredBuildPieceStats() [Method Body Modified]`<br>`CheckLenientBuildAchUnlocked() [Method Body Modified]` |
| 🟡 `MOD` | [`PlatformInitializer.cs`](Changes/assembly_valheim/PlatformInitializer.md) | `InitializeAndLoadPrefs() [Method Body Modified]`<br>`InitializeSaveDataStorage() [Method Body Modified]`<br>`RetroactivePathFix() [Method Body Modified]`<br>`private static void RetroactivePathFix(string[] allFilePaths)` |
| 🟡 `MOD` | [`Player.cs`](Changes/assembly_valheim/Player.md) | `SurvivedOneDay() [Method Body Modified]`<br>`UpdateBaseValue() [Method Body Modified]`<br>`UpdateStats() [Method Body Modified]` |
| 🟡 `MOD` | [`PlayerClothWindShelter.cs`](Changes/assembly_valheim/PlayerClothWindShelter.md) | `Awake() [Method Body Modified]`<br>`SetPlayer() [Method Body Modified]` |
| 🟡 `MOD` | [`PlayerProfile.cs`](Changes/assembly_valheim/PlayerProfile.md) | `GetStat() [Method Body Modified]`<br>`public float GetStat(PlayerStatType stat)`<br>`public float GetStat(PlayerStatType stat, DifficultyRequirement difficultyReq)` |
| 🟡 `MOD` | [`SaveCollection.cs`](Changes/assembly_valheim/SaveCollection.md) | `EnsureLocalLoaded() [Method Body Modified]`<br>`GetAllFilesInSource() [Method Body Modified]`<br>`KeepOnlyNewest() [Method Body Modified]`<br>`Reload() [Method Body Modified]`<br>`ReloadLocal() [Method Body Modified]`<br>*...and 6 more* |
| 🟡 `MOD` | [`SaveSystem.cs`](Changes/assembly_valheim/SaveSystem.md) | `ForceRefreshCache() [Method Body Modified]`<br>`ForceRefreshLocalCache() [Method Body Modified]`<br>`private static void InvalidateCache()`<br>`public static void ForceRefreshLocalCache(SaveDataType type)`<br>`public static void InvalidateCache()` |
| 🟡 `MOD` | [`SaveWithBackups.cs`](Changes/assembly_valheim/SaveWithBackups.md) | `ClearSaveFiles() [Method Body Modified]`<br>`EnsureSortedAndPrimaryFileDetermined() [Method Body Modified]`<br>`RemoveSaveFile() [Method Body Modified]`<br>`public void ClearSaveFiles()` |
| 🟡 `MOD` | [`ScrollRectEnsureVisible.cs`](Changes/assembly_valheim/ScrollRectEnsureVisible.md) | `CenterOnItem() [Method Body Modified]`<br>`Reset() [Method Body Modified]` |
| 🟡 `MOD` | [`ShieldDomeImageEffect.cs`](Changes/assembly_valheim/ShieldDomeImageEffect.md) | `RemoveShield() [Method Body Modified]` |
| 🟡 `MOD` | [`ShieldDomeParticleColor.cs`](Changes/assembly_valheim/ShieldDomeParticleColor.md) | `Start() [Method Body Modified]` |
| 🟡 `MOD` | [`Ship.cs`](Changes/assembly_valheim/Ship.md) | `CustomFixedUpdate() [Method Body Modified]`<br>`IsSailUp() [Method Body Modified]`<br>`UpdateRudder() [Method Body Modified]`<br>`UpdateSail() [Method Body Modified]`<br>`UpdateSailSize() [Method Body Modified]`<br>*...and 4 more* |
| 🟡 `MOD` | [`StatusEffect.cs`](Changes/assembly_valheim/StatusEffect.md) | `GetDuration() [Method Body Modified]`<br>`GetRemaningTime() [Method Body Modified]`<br>`SetDuration() [Method Body Modified]`<br>`public void SetDuration(float time)` |
| 🟡 `MOD` | [`StoreGui.cs`](Changes/assembly_valheim/StoreGui.md) | `Show() [Method Body Modified]` |
| 🟡 `MOD` | [`Terminal.cs`](Changes/assembly_valheim/Terminal.md) | `InitTerminal() [Method Body Modified]` |
| 🟡 `MOD` | [`Valheim.SettingsGui/GamepadSettings.cs`](Changes/assembly_valheim/GamepadSettings.md) | `Initialize() [Method Body Modified]` |
| 🟡 `MOD` | [`Version.cs`](Changes/assembly_valheim/Version.md) | *Class level change* |
| 🟡 `MOD` | [`WearNTear.cs`](Changes/assembly_valheim/WearNTear.md) | `ClearCachedSupport() [Method Body Modified]`<br>`UpdateSupport() [Method Body Modified]` |

---

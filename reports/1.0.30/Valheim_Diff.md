# Valheim API & Assembly Diff: `1.0.21` $\rightarrow$ `1.0.30`

> Automated decompilation comparison, mod impact report, and transpiler IL safety audit generated between Valheim version **1.0.21** and **1.0.30**.
>
> 🛡️ **Unity Asset Diff**: [View Detailed Unity Asset Difference Report](Changes/assets/Valheim_Assets_Diff.md)

## 📊 Executive Summary

| Metric | Count |
| :--- | :--- |
| **Assemblies Changed** | `2` / `9` |
| **Game Classes Modified** | `60` |
| **Game Classes Added** | `3` |
| **Game Classes Deleted** | `0` |
| **Total Lines Added** | `+1510` |
| **Total Lines Removed** | `-1068` |
| **Critical Breaking Mods** | `0` mod(s) |
| **High Risk Mod Patches** | `14` mod(s) |
| **Medium Risk Mod Patches** | `0` mod(s) |
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

✅ **Verified Safe**: None of the `14` modified Unity assets are referenced by active workspace mods.

## 🎯 Mod Impact Assessment

Scans all workspace mod projects for Harmony patches, transpilers, and breaking API references against modified game classes.

| Mod Project | Risk Level | Breaking API & Direct Hook Issues | Patches on Modified Classes | Touched Game Classes |
| :--- | :---: | :--- | :--- | :--- |
| **`AdventureBackpacks`** | 🔴 HIGH | ⚠️ `KeyHints.UpdateHints` (Postfix)<br>⚠️ `InventoryGui.DoCrafting` (Patch) | `InventoryGui.OnRightClickItem`<br>`FejdStartup.Start`<br>`Player.HaveRequirements`<br>`Player.HaveRequirements`<br>`Player.HaveRequirementItems`<br>`Player.UpdatePlacement`<br>`Player.GetFirstRequiredItem`<br>`Player.OnDestroy`<br>`Player.OnDeath`<br>`Player.UpdateEnvStatusEffects`<br>`Player.ApplyArmorDamageMods`<br>`Player.GetBodyArmor`<br>`Player.Update`<br>`InventoryGui.OnDropOutside`<br>`InventoryGui.OnSelectedItem`<br>`InventoryGui.Update`<br>`InventoryGui.SetupRequirement`<br>`InventoryGui.UpdateRecipeList`<br>`InventoryGui.UpdateRecipe`<br>`InventoryGui.OnCraftPressed`<br>`InventoryGui.Hide`<br>`InventoryGui.CloseContainer`<br>`InventoryGui.Show`<br>`InventoryGui.OnTakeAll` | `FejdStartup`, `InventoryGui`, `KeyHints`, `Menu`, `Player`, `Utils`, `Version`, `ZDO`, `ZInput`, `ZNet`, `ZNetScene`, `ZPackage`, `ZoneSystem` |
| **`AutoFeedRedux`** | 🔴 HIGH | ⚠️ `FejdStartup.Awake` (Prefix) | `Tameable.Awake`<br>`WearNTear.Damage` | `Character`, `FejdStartup`, `Player`, `Tameable`, `Version`, `WearNTear`, `ZDO` |
| **`BaitMeBruh`** | 🔴 HIGH | ⚠️ `FejdStartup.Awake` (Prefix)<br>⚠️ `FishingFloat.Catch` (Postfix)<br>⚠️ `SpawnSystem.UpdateSpawnList` (Prefix)<br>⚠️ `KeyHints.UpdateHints` (Patch) | `Player.AttachStart`<br>`Player.CanMove`<br>`Player.SetControls`<br>`Player.OnInventoryChanged`<br>`Player.UpdateAttach`<br>`Player.UpdateKnownRecipesList`<br>`FishingFloat.RPC_Nibble`<br>`FishingFloat.TryToHook`<br>`Player.UpdatePlacementGhost`<br>`FishingFloat.FixedUpdate`<br>`FishingFloat.Setup`<br>`Player.CheckKeyboardRadialPressed`<br>`Player.UpdateAttackBowDraw` | `BuildUi`, `Character`, `CookingStation`, `EnvMan`, `FejdStartup`, `FishingFloat`, `InventoryGui`, `KeyHints`, `Menu`, `Player`, `Sign`, `SpawnSystem`, `Utils`, `Version`, `WearNTear`, `ZDO`, `ZInput`, `ZNetScene`, `ZoneSystem` |
| **`BepInEx.ConfigDrawers`** | 🟢 LOW | *None* | *None* | `Version` |
| **`BetterSleepBruh`** | 🔴 HIGH | ⚠️ `FejdStartup.Awake` (Prefix) | `Player.AttachStart`<br>`Player.AttachStop`<br>`EnvMan.CalculateCanSleep`<br>`CookingStation.GetDeltaTime`<br>`ZNet.UpdateNetTime`<br>`ZNet.SaveWorld` | `Console`, `CookingStation`, `DungeonDB`, `EnvMan`, `FejdStartup`, `PlayFabManager`, `Player`, `PlayerProfile`, `Terminal`, `Utils`, `Version`, `ZDO`, `ZDOMan`, `ZNet`, `ZNetScene`, `ZPackage`, `ZPlayFabMatchmaking`, `ZSteamMatchmaking`, `ZoneSystem` |
| **`ConsoleBuddy`** | 🔴 HIGH | ⚠️ `Console.Awake` (Postfix)<br>⚠️ `FejdStartup.Awake` (Prefix) | `Terminal.AddString` | `Console`, `FejdStartup`, `Terminal`, `Version` |
| **`DoorOpenerBruh`** | 🔴 HIGH | ⚠️ `FejdStartup.Awake` (Prefix) | `Player.SetLocalPlayer`<br>`ZNetScene.Awake` | `FejdStartup`, `Player`, `Utils`, `Version`, `ZDO`, `ZNetScene` |
| **`FastItemTransfer`** | 🔴 HIGH | ⚠️ `FejdStartup.Awake` (Prefix) | `InventoryGui.OnRightClickItem` | `FejdStartup`, `InventoryGui`, `Player`, `Version` |
| **`NoFogBruh`** | 🔴 HIGH | ⚠️ `EnvMan.SetEnv` (Postfix)<br>⚠️ `EnvMan.SetEnv` (Prefix)<br>⚠️ `FejdStartup.Awake` (Prefix) | `EnvMan.Update`<br>`EnvMan.SetParticleArrayEnabled`<br>`EnvMan.GetAvailableEnvironments`<br>`EnvMan.GetEnvironmentOverride`<br>`EnvMan.QueueEnvironment`<br>`EnvMan.QueueEnvironment`<br>`EnvMan.SetForceEnvironment`<br>`EnvMan.Awake`<br>`EnvMan.AppendEnvironment` | `EnvMan`, `FejdStartup`, `Utils`, `Version` |
| **`RandomSpawnPointBruh`** | 🔴 HIGH | ⚠️ `Terminal.InitTerminal` (Postfix) | *None* | `Player`, `Terminal`, `Utils`, `Version`, `ZNet`, `ZNetScene`, `ZoneSystem` |
| **`SaveYourLuckBruh`** | 🔴 HIGH | ⚠️ `FejdStartup.Awake` (Prefix) | `Player.Save`<br>`Player.OnSpawned`<br>`Player.OnDestroy`<br>`Player.Load`<br>`FejdStartup.OnNewCharacterDone` | `Character`, `FejdStartup`, `Player`, `Version`, `ZNet` |
| **`ShieldMeBruh`** | 🔴 HIGH | ⚠️ `FejdStartup.Awake` (Prefix) | `Player.OnDeath`<br>`InventoryGui.Show`<br>`Player.SetLocalPlayer` | `FejdStartup`, `InventoryGui`, `Player`, `PlayerProfile`, `Version` |
| **`TheQueensDeadBruh`** | 🔴 HIGH | ⚠️ `EnvMan.SetEnv` (Prefix)<br>⚠️ `FejdStartup.Awake` (Prefix) | *None* | `EnvMan`, `FejdStartup`, `Utils`, `Version`, `ZoneSystem` |
| **`Vapok.Common`** | 🟢 LOW | *None* | *None* | `BinarySearchDictionary`, `Character`, `Console`, `FejdStartup`, `InventoryGui`, `Player`, `Smoke`, `SpawnSystem`, `Tameable`, `Terminal`, `Utils`, `Version`, `ZDO`, `ZDOExtraData`, `ZInput`, `ZNet`, `ZNetScene`, `ZPackage`, `ZoneSystem` |
| **`WardMeBruh`** | 🔴 HIGH | ⚠️ `FejdStartup.Awake` (Prefix)<br>⚠️ `ShieldGenerator.OnDestroy` (Prefix)<br>⚠️ `CookingStation.Awake` (Postfix) | `Player.UpdateFood`<br>`Character.RPC_Damage`<br>`Player.SetPlayerID`<br>`Player.OnSpawned`<br>`ZNet.RPC_CharacterID`<br>`ZNet.SaveWorld`<br>`ZNet.RPC_PlayerID`<br>`ShieldGenerator.CheckProjectile`<br>`ShieldGenerator.Start`<br>`ZDOMan.HandleDestroyedZDO`<br>`Cover.IsUnderRoof`<br>`Player.GetComfortLevel`<br>`Player.InShelter`<br>`Player.UpdateEnvStatusEffects`<br>`Player.UpdateEnvStatusEffects`<br>`SpawnSystem.IsSpawnPointGood`<br>`SpawnSystem.Spawn`<br>`WearNTear.HaveRoof`<br>`WearNTear.HaveAshRoof`<br>`WearNTear.UpdateWear`<br>`WearNTear.Destroy`<br>`InventoryGui.UpdateContainer`<br>`Menu.Update`<br>`Player.Update`<br>`Player.UpdateEnvStatusEffects` | `Character`, `Console`, `CookingStation`, `Cover`, `FejdStartup`, `GameCamera`, `GraphicsSettingsManager`, `InventoryGui`, `Menu`, `Player`, `PlayerProfile`, `ShieldGenerator`, `SpawnSystem`, `Tameable`, `Utils`, `Version`, `WearNTear`, `ZDO`, `ZDOExtraData`, `ZDOMan`, `ZInput`, `ZNet`, `ZNetScene`, `ZPackage`, `ZoneSystem` |
| **`XPortalNetworks`** | 🔴 HIGH | ⚠️ `ZNet.RPC_PeerInfo` (Postfix) | `WearNTear.OnPlaced`<br>`WearNTear.Destroy`<br>`ZDOMan.ConnectPortals` | `Player`, `Utils`, `Version`, `WearNTear`, `ZDO`, `ZDOExtraData`, `ZDOMan`, `ZInput`, `ZNet`, `ZNetScene`, `ZPackage`, `ZoneSystem` |

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
| [`assembly_utils.dll`](#assembly_utils) | `5` | `2` | `0` | `+139` / `-124` |
| [`assembly_valheim.dll`](#assembly_valheim) | `55` | `1` | `0` | `+1371` / `-944` |

---

## 🔧 Assembly: `assembly_utils.dll` <a id="assembly_utils"></a>

**Changes Summary:** `5` modified, `2` added, `0` deleted (`+139` / `-124` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`BinarySearchDictionary.cs`](Changes/assembly_utils/BinarySearchDictionary.md) | `BinaryFindKeyIndex() [Method Body Modified]`<br>`Compare() [Method Body Modified]`<br>`GetFastIterableKeyValues() [Method Body Modified]`<br>`GetValueByIndex() [Method Body Modified]`<br>`GetValueOrDefault() [Method Body Modified]`<br>*...and 10 more* |
| 🟡 `MOD` | [`BrotliCompressor.cs`](Changes/assembly_utils/BrotliCompressor.md) | `CompressBytes() [Method Body Modified]`<br>`CompressFile() [Method Body Modified]`<br>`CompressFile() [Method Removed]`<br>`CompressStream() [Method Body Modified]`<br>`CompressStream() [Method Removed]`<br>*...and 18 more* |
| 🟢 `ADD` | [`ColorUtils.cs`](Changes/assembly_utils/ColorUtils.md) | *Class level change* |
| 🟡 `MOD` | [`Cover.cs`](Changes/assembly_utils/Cover.md) | `CreateCoverRays() [Method Body Modified]`<br>`Setup() [Method Body Modified]` |
| 🟢 `ADD` | [`FastIterableKeyValues.cs`](Changes/assembly_utils/FastIterableKeyValues.md) | *Class level change* |
| 🟡 `MOD` | [`Utils.cs`](Changes/assembly_utils/Utils.md) | `CloseToZero() [Method Body Modified]`<br>`QuantizeHalfDegrees() [Method Body Modified]`<br>`ReadQuaternion() [Method Body Modified]`<br>`SmallPosition() [Method Body Modified]`<br>`public static uint QuantizeHalfDegrees(float degrees)` |
| 🟡 `MOD` | [`ZInput.cs`](Changes/assembly_utils/ZInput.md) | `ApplyDeadzoneFloat() [Method Body Modified]`<br>`ApplyDeadzoneToMagnitude() [Method Body Modified]`<br>`ApplyDeadzoneVector() [Method Body Modified]`<br>`GetScrollModifier() [Method Body Modified]`<br>`m_stickDeadZone [Field Removed, was float]`<br>*...and 2 more* |

---

## 🔧 Assembly: `assembly_valheim.dll` <a id="assembly_valheim"></a>

**Changes Summary:** `55` modified, `1` added, `0` deleted (`+1371` / `-944` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`BuildUi.cs`](Changes/assembly_valheim/BuildUi.md) | `ConfigureButtonNavigation() [Method Body Modified]`<br>`FavoritePiece() [Method Body Modified]`<br>`FocusPiece() [Method Body Modified]`<br>`FocusPieceListScrolling() [Method Body Modified]`<br>`FocusPieceListScrolling() [Method Removed]`<br>*...and 51 more* |
| 🟡 `MOD` | [`BuildUiPieceButton.cs`](Changes/assembly_valheim/BuildUiPieceButton.md) | `Awake() [Method Body Modified]`<br>`OnDestroy() [Method Body Modified]`<br>`OnMiddleClick() [Method Body Modified]`<br>`OnPointerEnter() [Method Body Modified]`<br>`Setup() [Method Body Modified]`<br>*...and 1 more* |
| 🟡 `MOD` | [`Character.cs`](Changes/assembly_valheim/Character.md) | `UpdateAshlandsWater() [Method Body Modified]` |
| 🟡 `MOD` | [`ConditionalObject.cs`](Changes/assembly_valheim/ConditionalObject.md) | `Awake() [Method Body Modified]`<br>`Update() [Method Body Modified]` |
| 🟡 `MOD` | [`ConnectPanel.cs`](Changes/assembly_valheim/ConnectPanel.md) | `IsVisible() [Method Body Modified]`<br>`Start() [Method Body Modified]`<br>`Update() [Method Body Modified]`<br>`UpdateConnectPanelGUI() [Method Body Modified]`<br>`UpdateFps() [Method Body Modified]`<br>*...and 5 more* |
| 🟡 `MOD` | [`Console.cs`](Changes/assembly_valheim/Console.md) | `Awake() [Method Body Modified]` |
| 🟡 `MOD` | [`CookingStation.cs`](Changes/assembly_valheim/CookingStation.md) | `Awake() [Method Body Modified]`<br>`GetHoverText() [Method Body Modified]`<br>`RPC_SetCrafterStat() [Method Body Modified]`<br>`SpawnItem() [Method Body Modified]`<br>`private void RPC_SetCrafterStat(long sender, long crafterId, string itemName)` |
| 🟡 `MOD` | [`DungeonDB.cs`](Changes/assembly_valheim/DungeonDB.md) | `GenerateHashList() [Method Body Modified]` |
| 🟡 `MOD` | [`DungeonGenerator.cs`](Changes/assembly_valheim/DungeonGenerator.md) | `PlaceEndCaps() [Method Body Modified]`<br>`PlaceRoom() [Method Body Modified]` |
| 🟡 `MOD` | [`EnvMan.cs`](Changes/assembly_valheim/EnvMan.md) | `GetDayFraction() [Method Body Modified]`<br>`SetEnv() [Method Body Modified]` |
| 🟡 `MOD` | [`FejdStartup.cs`](Changes/assembly_valheim/FejdStartup.md) | `AutoJoinPlayFabServer() [Method Body Modified]`<br>`AutoJoinServer() [Method Body Modified]`<br>`AutoJoinServer() [Method Removed]`<br>`Awake() [Method Body Modified]`<br>`CliAutoJoinServer() [Method Body Modified]`<br>*...and 9 more* |
| 🟡 `MOD` | [`FishingFloat.cs`](Changes/assembly_valheim/FishingFloat.md) | `Catch() [Method Body Modified]` |
| 🟡 `MOD` | [`GameCamera.cs`](Changes/assembly_valheim/GameCamera.md) | `UpdateMouseCapture() [Method Body Modified]` |
| 🟡 `MOD` | [`GlobalKeys.cs`](Changes/assembly_valheim/GlobalKeys.md) | *Class level change* |
| 🟡 `MOD` | [`GraphicsSettingIntExtentions.cs`](Changes/assembly_valheim/GraphicsSettingIntExtentions.md) | `GetRange() [Method Body Modified]` |
| 🟡 `MOD` | [`GraphicsSettingsManager.cs`](Changes/assembly_valheim/GraphicsSettingsManager.md) | `GetLightLimit() [Method Body Modified]` |
| 🟡 `MOD` | [`GrapplingPoint.cs`](Changes/assembly_valheim/GrapplingPoint.md) | `Break() [Method Body Modified]` |
| 🟡 `MOD` | [`GridNavigationUtility.cs`](Changes/assembly_valheim/GridNavigationUtility.md) | `DefaultOrWrap() [Method Body Modified]`<br>`GetChildSelectables() [Method Body Modified]`<br>`GetColumnCountFromLaidOutChildren() [Method Body Modified]`<br>`GetSelectable() [Method Body Modified]`<br>`GetSelectableBelow() [Method Body Modified]`<br>*...and 5 more* |
| 🟡 `MOD` | [`InstanceRenderer.cs`](Changes/assembly_valheim/InstanceRenderer.md) | `AddInstance() [Method Body Modified]`<br>`Clear() [Method Body Modified]`<br>`CustomUpdate() [Method Body Modified]`<br>`Resize() [Method Body Modified]`<br>`SetInstance() [Method Body Modified]`<br>*...and 6 more* |
| 🟡 `MOD` | [`InventoryGui.cs`](Changes/assembly_valheim/InventoryGui.md) | `DoCrafting() [Method Body Modified]` |
| 🟡 `MOD` | [`KeyHints.cs`](Changes/assembly_valheim/KeyHints.md) | `DisableAll() [Method Body Modified]`<br>`DisableAllExcept() [Method Body Modified]`<br>`UpdateHints() [Method Body Modified]`<br>`m_buildMenuHintsGP [Field Removed, was GameObject[]]`<br>`m_buildMenuHintsKB [Field Removed, was GameObject[]]`<br>*...and 2 more* |
| 🟡 `MOD` | [`MasterClient.cs`](Changes/assembly_valheim/MasterClient.md) | `SendStats() [Method Body Modified]` |
| 🟡 `MOD` | [`Menu.cs`](Changes/assembly_valheim/Menu.md) | `UpdateCursor() [Method Body Modified]` |
| 🟡 `MOD` | [`PlayFabManager.cs`](Changes/assembly_valheim/PlayFabManager.md) | `CheckPlayFabWarnings() [Method Body Modified]`<br>`CheckPlayFabWarnings() [Method Removed]`<br>`GetBanDuration() [Method Body Modified]`<br>`GetBanReason() [Method Body Modified]`<br>`OnLoginFinished() [Method Body Modified]`<br>*...and 5 more* |
| 🟡 `MOD` | [`Player.cs`](Changes/assembly_valheim/Player.md) | `GetItemUpgradeChance() [Method Body Modified]` |
| 🟡 `MOD` | [`PlayerProfile.cs`](Changes/assembly_valheim/PlayerProfile.md) | `LoadPlayerFromDisk() [Method Body Modified]`<br>`SavePlayerToDisk() [Method Body Modified]` |
| 🟡 `MOD` | [`ServerListGui.cs`](Changes/assembly_valheim/ServerListGui.md) | `OnPlayFabJoinCodeSuccess() [Method Body Modified]` |
| 🟡 `MOD` | [`ShieldGenerator.cs`](Changes/assembly_valheim/ShieldGenerator.md) | `OnDestroy() [Method Body Modified]` |
| 🟡 `MOD` | [`Sign.cs`](Changes/assembly_valheim/Sign.md) | `UpdateText() [Method Body Modified]` |
| 🟡 `MOD` | [`SlowUpdater.cs`](Changes/assembly_valheim/SlowUpdater.md) | `Awake() [Method Body Modified]`<br>`UpdateLoop() [Method Body Modified]` |
| 🟡 `MOD` | [`Smoke.cs`](Changes/assembly_valheim/Smoke.md) | `Awake() [Method Body Modified]`<br>`CustomUpdate() [Method Body Modified]`<br>`GetAlpha() [Method Body Modified]`<br>`GetAlpha() [Method Removed]`<br>`GetParticleValues() [Method Body Modified]`<br>*...and 9 more* |
| 🟡 `MOD` | [`SmokeRenderer.cs`](Changes/assembly_valheim/SmokeRenderer.md) | `AddSmokeToChunk() [Method Body Modified]`<br>`AddSmokeToChunk() [Method Removed]`<br>`Awake() [Method Body Modified]`<br>`Awake() [Method Removed]`<br>`ChunkToWorld() [Method Body Modified]`<br>*...and 44 more* |
| 🟡 `MOD` | [`SoftReferencePrefabSpawner.cs`](Changes/assembly_valheim/SoftReferencePrefabSpawner.md) | `SpawnPrefab() [Method Body Modified]` |
| 🟡 `MOD` | [`SpawnSystem.cs`](Changes/assembly_valheim/SpawnSystem.md) | `UpdateSpawnList() [Method Body Modified]` |
| 🟡 `MOD` | [`Tameable.cs`](Changes/assembly_valheim/Tameable.md) | `UnsummonMaxInstances() [Method Body Modified]` |
| 🟡 `MOD` | [`Terminal.cs`](Changes/assembly_valheim/Terminal.md) | `InitTerminal() [Method Body Modified]`<br>`static bool TryFixHalfAngle(float angle, out float fixedAngle)` |
| 🟡 `MOD` | [`TerrainComp.cs`](Changes/assembly_valheim/TerrainComp.md) | `Awake() [Method Body Modified]`<br>`CheckSnow() [Method Body Modified]`<br>`ComputePaintMaskHash() [Method Body Modified]`<br>`DoOperation() [Method Body Modified]`<br>`FindTerrainCompiler() [Method Body Modified]`<br>*...and 12 more* |
| 🟡 `MOD` | [`TextsDialog.cs`](Changes/assembly_valheim/TextsDialog.md) | `AddStats() [Method Body Modified]` |
| 🟡 `MOD` | [`Valheim.SettingsGui/AccessibilitySettings.cs`](Changes/assembly_valheim/AccessibilitySettings.md) | `Initialize() [Method Body Modified]`<br>`OnBrightnessChanged() [Method Body Modified]`<br>`OnMotionBlurChanged() [Method Body Modified]`<br>`OnOkAsync() [Method Body Modified]`<br>`OnUIScaleChanged() [Method Body Modified]`<br>*...and 1 more* |
| 🟡 `MOD` | [`Valheim.SettingsGui/GraphicsSettings.cs`](Changes/assembly_valheim/GraphicsSettings.md) | `GetDisplayValue() [Method Body Modified]` |
| 🟡 `MOD` | [`Version.cs`](Changes/assembly_valheim/Version.md) | *Class level change* |
| 🟡 `MOD` | [`Vine.cs`](Changes/assembly_valheim/Vine.md) | `CheckGrowChance() [Method Body Modified]`<br>`Grow() [Method Body Modified]`<br>`UpdateGrow() [Method Body Modified]` |
| 🟡 `MOD` | [`WearNTear.cs`](Changes/assembly_valheim/WearNTear.md) | `UpdateSupport() [Method Body Modified]` |
| 🟡 `MOD` | [`ZDO.cs`](Changes/assembly_valheim/ZDO.md) | `Clone() [Method Body Modified]`<br>`Deserialize() [Method Body Modified]`<br>`InternalSetPosition() [Method Body Modified]`<br>`InvalidateSector() [Method Body Modified]`<br>`Reset() [Method Body Modified]`<br>*...and 15 more* |
| 🟡 `MOD` | [`ZDODataHelper.cs`](Changes/assembly_valheim/ZDODataHelper.md) | `ReadFromDisk() [Method Body Modified]`<br>`WriteData() [Method Body Modified]` |
| 🟢 `ADD` | [`ZDODebugNetworkDataCollecter.cs`](Changes/assembly_valheim/ZDODebugNetworkDataCollecter.md) | *Class level change* |
| 🟡 `MOD` | [`ZDOExtraData.cs`](Changes/assembly_valheim/ZDOExtraData.md) | `GetConnectionType() [Method Body Modified]`<br>`GetData() [Method Body Modified]`<br>`Update() [Method Body Modified]`<br>`Update() [Method Removed]`<br>`public static bool Update(ZDOID zid, int hash, Vector3 value)`<br>*...and 2 more* |
| 🟡 `MOD` | [`ZDOHelper.cs`](Changes/assembly_valheim/ZDOHelper.md) | `GetAllZDOIDsWithHash() [Method Body Modified]`<br>`GetValuesOrEmpty() [Method Body Modified]`<br>`GetValuesOrEmptyFilterSession() [Method Body Modified]`<br>`InitAndReserve() [Method Body Modified]`<br>`InitAndSet() [Method Body Modified]`<br>*...and 5 more* |
| 🟡 `MOD` | [`ZDOMan.cs`](Changes/assembly_valheim/ZDOMan.md) | `PeerZDOInfo() [Method Body Modified]` |
| 🟡 `MOD` | [`ZNet.cs`](Changes/assembly_valheim/ZNet.md) | `OnSteamServerRegistered() [Method Body Modified]`<br>`OpenServer() [Method Body Modified]`<br>`RPC_PeerInfo() [Method Body Modified]`<br>`SaveWorldThread() [Method Body Modified]` |
| 🟡 `MOD` | [`ZNetScene.cs`](Changes/assembly_valheim/ZNetScene.md) | `AddInstance() [Method Body Modified]`<br>`IsPrefabZDOValid() [Method Body Modified]`<br>`private bool IsPrefabZDOValid(ZDO zdo)`<br>`public bool IsPrefabZDOValid(ZDO zdo)` |
| 🟡 `MOD` | [`ZPackage.cs`](Changes/assembly_valheim/ZPackage.md) | `Clear() [Method Body Modified]`<br>`Decompress() [Method Body Modified]`<br>`Flush() [Method Body Modified]`<br>`GetArray() [Method Body Modified]`<br>`GetCompressed() [Method Body Modified]`<br>*...and 16 more* |
| 🟡 `MOD` | [`ZPlayFabLobbySearch.cs`](Changes/assembly_valheim/ZPlayFabLobbySearch.md) | *Class level change* |
| 🟡 `MOD` | [`ZPlayFabMatchmaking.cs`](Changes/assembly_valheim/ZPlayFabMatchmaking.md) | `ListServers() [Method Body Modified]` |
| 🟡 `MOD` | [`ZSteamMatchmaking.cs`](Changes/assembly_valheim/ZSteamMatchmaking.md) | `DecodeTags() [Method Body Modified]` |
| 🟡 `MOD` | [`ZoneSystem.cs`](Changes/assembly_valheim/ZoneSystem.md) | `CheckLocationDuplicates() [Method Body Modified]`<br>`CountNrOfLocation() [Method Body Modified]`<br>`CreateLocationProxy() [Method Body Modified]`<br>`FindClosestLocation() [Method Body Modified]`<br>`FindLocations() [Method Body Modified]`<br>*...and 8 more* |

---

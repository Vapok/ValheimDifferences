# Valheim API & Assembly Diff: `1.0.15` $\rightarrow$ `1.0.16`

> Automated decompilation comparison, mod impact report, and transpiler IL safety audit generated between Valheim version **1.0.15** and **1.0.16**.
>
> 🛡️ **Unity Asset Diff**: [View Detailed Unity Asset Difference Report](Changes/assets/Valheim_Assets_Diff.md)

## 📊 Executive Summary

| Metric | Count |
| :--- | :--- |
| **Assemblies Changed** | `9` / `9` |
| **Game Classes Modified** | `399` |
| **Game Classes Added** | `0` |
| **Game Classes Deleted** | `0` |
| **Total Lines Added** | `+3258` |
| **Total Lines Removed** | `-2859` |
| **High Risk Mod Patches** | `0` mod(s) |
| **Medium Risk Mod Patches** | `12` mod(s) |
| **Transpiler Hooks Audited** | `8` total (`8` safe / `0` caution / `0` critical) |

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
      <td><code>Humanoid.UpdateEquipmentStatusEffects</code></td>
      <td><code>Humanoid.cs:19</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'Humanoid' was modified elsewhere, but method 'UpdateEquipmentStatusEffects' is UNTOUCHED.</em></td>
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
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>AdventureBackpacks</code></strong></td>
      <td><code>InventoryGui.Update</code></td>
      <td><code>InventoryGui.cs:311</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'InventoryGui' was modified elsewhere, but method 'Update' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>NoFogBruh</code></strong></td>
      <td><code>PostProcessingBehaviour.OnPreRender</code></td>
      <td><code>DisableFogComponent.cs:289</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'PostProcessingBehaviour' was modified elsewhere, but method 'OnPreRender' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>Vapok.Common</code></strong></td>
      <td><code>InventoryGui.UpdateRecipe</code></td>
      <td><code>ItemManager.cs:2238</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'InventoryGui' was modified elsewhere, but method 'UpdateRecipe' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>Vapok.Common</code></strong></td>
      <td><code>InventoryGui.SetupRequirementList</code></td>
      <td><code>ItemManager.cs:2239</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'InventoryGui' was modified elsewhere, but method 'SetupRequirementList' is UNTOUCHED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🟢 <code>SAFE</code></td>
      <td><strong><code>Vapok.Common</code></strong></td>
      <td><code>PieceTable.UpdateAvailable</code></td>
      <td><code>PieceManager.cs:1211</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'PieceTable' and method 'UpdateAvailable' are 100% UNCHANGED.</em></td>
    </tr>
    <tr>
      <td align="center" rowspan="2">🛡️ <code>VERIFIED SAFE</code></td>
      <td><strong><code>XPortalNetworks</code></strong></td>
      <td><code>TeleportWorld.UpdatePortal</code></td>
      <td><code>TeleportWorld.cs:87</code></td>
    </tr>
    <tr>
      <td colspan="3"><em>Class 'TeleportWorld' was modified elsewhere, but method 'UpdatePortal' is UNTOUCHED.</em></td>
    </tr>
  </tbody>
</table>

## 🛡️ Mod Impact: Unity Asset Cross-Reference

Scans workspace mods for direct references (prefab names, item drops, status effects, and recipes) against modified Unity assets.

✅ **Verified Safe**: None of the `2` modified Unity assets are referenced by active workspace mods.

## 🎯 Mod Impact Assessment

Scans all workspace mod projects for Harmony patches, transpilers, and references against modified game classes.

| Mod Project | Risk Level | Direct Patches on Changed Methods | Patches on Modified Classes | Touched Game Classes |
| :--- | :---: | :--- | :--- | :--- |
| **`AdventureBackpacks`** | 🟡 MEDIUM | *None* | `InventoryGui.OnRightClickItem`<br>`Humanoid.UseItem`<br>`ArmorStand.UpdateAttach`<br>`ItemStand.UpdateAttach`<br>`Container.TakeAll`<br>`Container.Interact`<br>`Container.Save`<br>`Container.Load`<br>`ZNetView.Awake`<br>`Container.Awake`<br>`Container.IsOwner`<br>`Container.IsInUse`<br>`Container.SetInUse`<br>`Container.CheckAccess`<br>`Container.StackAll`<br>`FejdStartup.Start`<br>`InventoryGrid.UpdateGui`<br>`Door.HaveKey`<br>`Humanoid.UpdateEquipmentStatusEffects`<br>`Humanoid.UnequipItem`<br>`Humanoid.EquipItem`<br>`InventoryGui.OnDropOutside`<br>`Humanoid.DropItem`<br>`InventoryGrid.DropItem`<br>`InventoryGui.DoCrafting`<br>`InventoryGui.OnSelectedItem`<br>`InventoryGui.Update`<br>`InventoryGui.SetupRequirement`<br>`InventoryGui.UpdateRecipeList`<br>`InventoryGui.UpdateRecipe`<br>`InventoryGui.OnCraftPressed`<br>`InventoryGui.Hide`<br>`Player.HaveRequirements`<br>`Player.HaveRequirements`<br>`Player.HaveRequirementItems`<br>`Player.UpdatePlacement`<br>`Player.GetFirstRequiredItem`<br>`Player.OnDestroy`<br>`Player.OnDeath`<br>`Player.UpdateEnvStatusEffects`<br>`Player.ApplyArmorDamageMods`<br>`Hud.SetupPieceInfo` | `ArmorStand`, `Container`, `CraftingStation`, `Demister`, `Door`, `FejdStartup`, `Game`, `Heightmap`, `HitData`, `Hud`, `Humanoid`, `InventoryGrid`, `InventoryGui`, `ItemDrop`, `ItemStand`, `Localize`, `Location`, `Menu`, `MessageHud`, `ObjectDB`, `Odin`, `Piece`, `Player`, `SE_Demister`, `Settings`, `StatusEffect`, `Utils`, `Version`, `VisEquipment`, `ZDO`, `ZInput`, `ZNet`, `ZNetScene`, `ZNetView`, `ZPackage` |
| **`AutoFeedRedux`** | 🟡 MEDIUM | *None* | `Container.Awake`<br>`Container.OnDestroyed`<br>`FejdStartup.Awake`<br>`Game.Awake`<br>`MonsterAI.UpdateConsumeItem`<br>`Tameable.Awake`<br>`WearNTear.Damage` | `Character`, `Container`, `FejdStartup`, `Game`, `HitData`, `Humanoid`, `ItemDrop`, `MonsterAI`, `Player`, `Settings`, `Tameable`, `Version`, `WearNTear`, `ZDO`, `ZNetView` |
| **`BepInEx.ConfigDrawers`** | 🟢 LOW | *None* | *None* | `Container`, `Floating`, `Settings`, `Version` |
| **`BetterSleepBruh`** | 🟡 MEDIUM | *None* | `Player.AttachStart`<br>`Player.AttachStop`<br>`ZNet.UpdateNetTime`<br>`FejdStartup.Awake`<br>`Game.UpdateSleeping` | `AudioMan`, `Bed`, `DungeonDB`, `FejdStartup`, `FileReader`, `Game`, `GameVersion`, `Heightmap`, `Localize`, `MessageHud`, `Minimap`, `MistEmitter`, `MusicMan`, `PlatformPrefs`, `PlayFabManager`, `Player`, `PlayerProfile`, `RandEventSystem`, `ReflectionUpdate`, `SaveSystem`, `Settings`, `Ship`, `SteamManager`, `Terminal`, `UnifiedPopup`, `Utils`, `Version`, `World`, `ZDO`, `ZDOMan`, `ZNet`, `ZNetScene`, `ZPackage`, `ZPlayFabMatchmaking`, `ZPlayFabSocket`, `ZSteamMatchmaking`, `ZSteamSocket`, `ZoneSystem` |
| **`ConsoleBuddy`** | 🟡 MEDIUM | *None* | `Terminal.AddString`<br>`FejdStartup.Awake` | `FejdStartup`, `Game`, `Settings`, `Terminal`, `Version` |
| **`DoorOpenerBruh`** | 🟡 MEDIUM | *None* | `Door.Awake`<br>`FejdStartup.Awake`<br>`Player.SetLocalPlayer`<br>`ZNetScene.Awake` | `Door`, `FejdStartup`, `ItemDrop`, `Piece`, `Player`, `Settings`, `Utils`, `Version`, `World`, `ZNetScene`, `ZNetView` |
| **`FastItemTransfer`** | 🟡 MEDIUM | *None* | `InventoryGui.OnRightClickItem`<br>`Humanoid.UseItem`<br>`FejdStartup.Awake` | `FejdStartup`, `Humanoid`, `InventoryGrid`, `InventoryGui`, `ItemDrop`, `Player`, `Settings`, `Version` |
| **`NoFogBruh`** | 🟡 MEDIUM | *None* | `ParticleMist.Update`<br>`DistantFogEmitter.Update`<br>`PostProcessingBehaviour.OnPreRender`<br>`FejdStartup.Awake` | `AmbientOcclusionComponent`, `DistantFogEmitter`, `FejdStartup`, `FogComponent`, `FollowPlayer`, `Game`, `MistEmitter`, `ParticleMist`, `PostProcessingBehaviour`, `Settings`, `Utils`, `Version` |
| **`RandomSpawnPointBruh`** | 🟡 MEDIUM | *None* | `Game.SpawnPlayer`<br>`Terminal.InitTerminal`<br>`Humanoid.GiveDefaultItem`<br>`Minimap.UpdateExplore` | `Demister`, `EffectArea`, `Game`, `Heightmap`, `Hud`, `Humanoid`, `ItemDrop`, `Location`, `Minimap`, `ObjectDB`, `Player`, `PrivateArea`, `Settings`, `Terminal`, `Utils`, `Valkyrie`, `Version`, `ZNetScene`, `ZoneSystem` |
| **`ShieldMeBruh`** | 🟡 MEDIUM | *None* | `FejdStartup.Awake`<br>`Player.OnDeath`<br>`TombStone.OnTakeAllSuccess`<br>`Humanoid.EquipItem`<br>`Humanoid.UnequipItem`<br>`InventoryGrid.UpdateGui`<br>`InventoryGui.Show`<br>`InventoryGrid.DropItem`<br>`Player.SetLocalPlayer` | `FejdStartup`, `Game`, `Humanoid`, `InventoryElement`, `InventoryGrid`, `InventoryGui`, `ItemDrop`, `Player`, `PlayerProfile`, `TombStone`, `Version` |
| **`TheQueensDeadBruh`** | 🟡 MEDIUM | *None* | `ParticleMist.Update`<br>`FejdStartup.Awake` | `FejdStartup`, `ParticleMist`, `Settings`, `Utils`, `Version`, `ZoneSystem` |
| **`Vapok.Common`** | 🟡 MEDIUM | *None* | `ZNet.OnNewConnection` | `Aoe`, `Attack`, `BaseAI`, `BinarySearchDictionary`, `Character`, `CharacterDrop`, `Container`, `CraftingStation`, `CreatureSpawner`, `Demister`, `EffectArea`, `FejdStartup`, `Fire`, `Game`, `Heightmap`, `HitData`, `Hud`, `InventoryGui`, `ItemDrop`, `Localize`, `Location`, `MessageHud`, `Minimap`, `MonsterAI`, `ObjectDB`, `Piece`, `Player`, `SE_Demister`, `Smelter`, `Smoke`, `SpawnArea`, `SpawnSystem`, `SpawnSystemList`, `StationExtension`, `StatusEffect`, `Tameable`, `Terminal`, `TimedDestruction`, `Trader`, `Utils`, `Version`, `World`, `ZDO`, `ZNet`, `ZNetScene`, `ZNetView`, `ZPackage`, `ZoneSystem` |
| **`XPortalNetworks`** | 🟡 MEDIUM | *None* | `Game.Awake`<br>`Game.Start`<br>`Game.ConnectPortals`<br>`Game.ConnectPortalsCoroutine`<br>`ZNet.RPC_PeerInfo`<br>`TeleportWorld.GetHoverText`<br>`TeleportWorld.Teleport`<br>`TeleportWorld.UpdatePortal`<br>`Piece.SetCreator`<br>`Piece.CanBeRemoved`<br>`WearNTear.OnPlaced`<br>`WearNTear.Destroy`<br>`ZDOMan.ConnectPortals` | `Container`, `Game`, `ItemDrop`, `Localize`, `Location`, `Minimap`, `ObjectDB`, `Odin`, `Piece`, `Player`, `Talker`, `Teleport`, `TeleportWorld`, `UIGamePad`, `UIGroupHandler`, `Utils`, `Version`, `WearNTear`, `ZDO`, `ZDOMan`, `ZInput`, `ZNet`, `ZNetScene`, `ZNetView`, `ZPackage`, `ZoneSystem` |

## 📦 Assemblies Overview

| Assembly | Modified | Added | Deleted | Line Changes |
| :--- | :--- | :--- | :--- | :--- |
| [`Assembly-CSharp.dll`](#assembly-csharp) | `3` | `0` | `0` | `+15` / `-15` |
| [`assembly_googleanalytics.dll`](#assembly_googleanalytics) | `1` | `0` | `0` | `+1` / `-1` |
| [`assembly_guiutils.dll`](#assembly_guiutils) | `8` | `0` | `0` | `+47` / `-16` |
| [`assembly_lux.dll`](#assembly_lux) | `1` | `0` | `0` | `+1` / `-1` |
| [`assembly_postprocessing.dll`](#assembly_postprocessing) | `18` | `0` | `0` | `+67` / `-67` |
| [`assembly_simplemeshcombine.dll`](#assembly_simplemeshcombine) | `1` | `0` | `0` | `+4` / `-4` |
| [`assembly_sunshafts.dll`](#assembly_sunshafts) | `22` | `0` | `0` | `+63` / `-63` |
| [`assembly_utils.dll`](#assembly_utils) | `15` | `0` | `0` | `+54` / `-57` |
| [`assembly_valheim.dll`](#assembly_valheim) | `330` | `0` | `0` | `+3006` / `-2635` |

---

## 🔧 Assembly: `Assembly-CSharp.dll` <a id="assembly-csharp"></a>

**Changes Summary:** `3` modified, `0` added, `0` deleted (`+15` / `-15` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`LuxParticles.Demo/LuxParticles_ExtendedFlycam.cs`](Changes/Assembly-CSharp/LuxParticles_ExtendedFlycam.md) | *Class level change* |
| 🟡 `MOD` | [`Microsoft.Xbox/Gdk.cs`](Changes/Assembly-CSharp/Gdk.md) | *Class level change* |
| 🟡 `MOD` | [`UILineRenderer.cs`](Changes/Assembly-CSharp/UILineRenderer.md) | *Class level change* |

---

## 🔧 Assembly: `assembly_googleanalytics.dll` <a id="assembly_googleanalytics"></a>

**Changes Summary:** `1` modified, `0` added, `0` deleted (`+1` / `-1` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`GoogleAnalyticsV4.cs`](Changes/assembly_googleanalytics/GoogleAnalyticsV4.md) | *Class level change* |

---

## 🔧 Assembly: `assembly_guiutils.dll` <a id="assembly_guiutils"></a>

**Changes Summary:** `8` modified, `0` added, `0` deleted (`+47` / `-16` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`AlphaMotion.cs`](Changes/assembly_guiutils/AlphaMotion.md) | *Class level change* |
| 🟡 `MOD` | [`ButtonSfx.cs`](Changes/assembly_guiutils/ButtonSfx.md) | `private void Awake()`<br>`private void OnDisable()`<br>`private void OnEnable()`<br>`private void Start()` |
| 🟡 `MOD` | [`GuiPixelFix.cs`](Changes/assembly_guiutils/GuiPixelFix.md) | *Class level change* |
| 🟡 `MOD` | [`GuiUtils.cs`](Changes/assembly_guiutils/GuiUtils.md) | `public static void SetNavigationHorizontal(Selectable left, Selectable right)` |
| 🟡 `MOD` | [`Localize.cs`](Changes/assembly_guiutils/Localize.md) | *Class level change* |
| 🟡 `MOD` | [`UIGroupHandler.cs`](Changes/assembly_guiutils/UIGroupHandler.md) | *Class level change* |
| 🟡 `MOD` | [`UITooltip.cs`](Changes/assembly_guiutils/UITooltip.md) | *Class level change* |
| 🟡 `MOD` | [`Uirotate.cs`](Changes/assembly_guiutils/Uirotate.md) | *Class level change* |

---

## 🔧 Assembly: `assembly_lux.dll` <a id="assembly_lux"></a>

**Changes Summary:** `1` modified, `0` added, `0` deleted (`+1` / `-1` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`LuxParticles/LuxParticles_AmbientLighting.cs`](Changes/assembly_lux/LuxParticles_AmbientLighting.md) | *Class level change* |

---

## 🔧 Assembly: `assembly_postprocessing.dll` <a id="assembly_postprocessing"></a>

**Changes Summary:** `18` modified, `0` added, `0` deleted (`+67` / `-67` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/AmbientOcclusionComponent.cs`](Changes/assembly_postprocessing/AmbientOcclusionComponent.md) | *Class level change* |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/BloomComponent.cs`](Changes/assembly_postprocessing/BloomComponent.md) | *Class level change* |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/BuiltinDebugViewsComponent.cs`](Changes/assembly_postprocessing/BuiltinDebugViewsComponent.md) | *Class level change* |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/ChromaticAberrationComponent.cs`](Changes/assembly_postprocessing/ChromaticAberrationComponent.md) | *Class level change* |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/ColorGradingComponent.cs`](Changes/assembly_postprocessing/ColorGradingComponent.md) | *Class level change* |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/DepthOfFieldComponent.cs`](Changes/assembly_postprocessing/DepthOfFieldComponent.md) | *Class level change* |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/DitheringComponent.cs`](Changes/assembly_postprocessing/DitheringComponent.md) | *Class level change* |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/DitheringModel.cs`](Changes/assembly_postprocessing/DitheringModel.md) | *Class level change* |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/EyeAdaptationComponent.cs`](Changes/assembly_postprocessing/EyeAdaptationComponent.md) | *Class level change* |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/FogComponent.cs`](Changes/assembly_postprocessing/FogComponent.md) | *Class level change* |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/FxaaComponent.cs`](Changes/assembly_postprocessing/FxaaComponent.md) | *Class level change* |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/GrainComponent.cs`](Changes/assembly_postprocessing/GrainComponent.md) | *Class level change* |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/MotionBlurComponent.cs`](Changes/assembly_postprocessing/MotionBlurComponent.md) | *Class level change* |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/PostProcessingBehaviour.cs`](Changes/assembly_postprocessing/PostProcessingBehaviour.md) | *Class level change* |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/ScreenSpaceReflectionComponent.cs`](Changes/assembly_postprocessing/ScreenSpaceReflectionComponent.md) | *Class level change* |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/TaaComponent.cs`](Changes/assembly_postprocessing/TaaComponent.md) | *Class level change* |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/UserLutComponent.cs`](Changes/assembly_postprocessing/UserLutComponent.md) | *Class level change* |
| 🟡 `MOD` | [`UnityEngine.PostProcessing/VignetteComponent.cs`](Changes/assembly_postprocessing/VignetteComponent.md) | *Class level change* |

---

## 🔧 Assembly: `assembly_simplemeshcombine.dll` <a id="assembly_simplemeshcombine"></a>

**Changes Summary:** `1` modified, `0` added, `0` deleted (`+4` / `-4` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`SimpleMeshCombine.cs`](Changes/assembly_simplemeshcombine/SimpleMeshCombine.md) | *Class level change* |

---

## 🔧 Assembly: `assembly_sunshafts.dll` <a id="assembly_sunshafts"></a>

**Changes Summary:** `22` modified, `0` added, `0` deleted (`+63` / `-63` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/Bloom.cs`](Changes/assembly_sunshafts/Bloom.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/BloomAndFlares.cs`](Changes/assembly_sunshafts/BloomAndFlares.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/Blur.cs`](Changes/assembly_sunshafts/Blur.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/CameraMotionBlur.cs`](Changes/assembly_sunshafts/CameraMotionBlur.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/ColorCorrectionCurves.cs`](Changes/assembly_sunshafts/ColorCorrectionCurves.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/ColorCorrectionRamp.cs`](Changes/assembly_sunshafts/ColorCorrectionRamp.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/ContrastStretch.cs`](Changes/assembly_sunshafts/ContrastStretch.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/CreaseShading.cs`](Changes/assembly_sunshafts/CreaseShading.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/DepthOfFieldDeprecated.cs`](Changes/assembly_sunshafts/DepthOfFieldDeprecated.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/GlobalFog.cs`](Changes/assembly_sunshafts/GlobalFog.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/Grayscale.cs`](Changes/assembly_sunshafts/Grayscale.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/ImageEffectBase.cs`](Changes/assembly_sunshafts/ImageEffectBase.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/MotionBlur.cs`](Changes/assembly_sunshafts/MotionBlur.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/NoiseAndGrain.cs`](Changes/assembly_sunshafts/NoiseAndGrain.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/NoiseAndScratches.cs`](Changes/assembly_sunshafts/NoiseAndScratches.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/PostEffectsBase.cs`](Changes/assembly_sunshafts/PostEffectsBase.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/ScreenSpaceAmbientOcclusion.cs`](Changes/assembly_sunshafts/ScreenSpaceAmbientOcclusion.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/SepiaTone.cs`](Changes/assembly_sunshafts/SepiaTone.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/Tonemapping.cs`](Changes/assembly_sunshafts/Tonemapping.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/Twirl.cs`](Changes/assembly_sunshafts/Twirl.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/VignetteAndChromaticAberration.cs`](Changes/assembly_sunshafts/VignetteAndChromaticAberration.md) | *Class level change* |
| 🟡 `MOD` | [`UnityStandardAssets.ImageEffects/Vortex.cs`](Changes/assembly_sunshafts/Vortex.md) | *Class level change* |

---

## 🔧 Assembly: `assembly_utils.dll` <a id="assembly_utils"></a>

**Changes Summary:** `15` modified, `0` added, `0` deleted (`+54` / `-57` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`BinarySearchDictionary.cs`](Changes/assembly_utils/BinarySearchDictionary.md) | *Class level change* |
| 🟡 `MOD` | [`CircularBuffer/CircularBuffer.cs`](Changes/assembly_utils/CircularBuffer.md) | *Class level change* |
| 🟡 `MOD` | [`Dynamics/SecondOrderDynamicsBase.cs`](Changes/assembly_utils/SecondOrderDynamicsBase.md) | *Class level change* |
| 🟡 `MOD` | [`FastNoise.cs`](Changes/assembly_utils/FastNoise.md) | *Class level change* |
| 🟡 `MOD` | [`FileReader.cs`](Changes/assembly_utils/FileReader.md) | *Class level change* |
| 🟡 `MOD` | [`HideWhenRunning.cs`](Changes/assembly_utils/HideWhenRunning.md) | *Class level change* |
| 🟡 `MOD` | [`InputDefinition.cs`](Changes/assembly_utils/InputDefinition.md) | *Class level change* |
| 🟡 `MOD` | [`LRUCache.cs`](Changes/assembly_utils/LRUCache.md) | *Class level change* |
| 🟡 `MOD` | [`NetworkingUtils/IPv4Address.cs`](Changes/assembly_utils/IPv4Address.md) | *Class level change* |
| 🟡 `MOD` | [`NetworkingUtils/IPv6Address.cs`](Changes/assembly_utils/IPv6Address.md) | *Class level change* |
| 🟡 `MOD` | [`PlatformPrefs.cs`](Changes/assembly_utils/PlatformPrefs.md) | *Class level change* |
| 🟡 `MOD` | [`StringExtensionMethods.cs`](Changes/assembly_utils/StringExtensionMethods.md) | *Class level change* |
| 🟡 `MOD` | [`Utils.cs`](Changes/assembly_utils/Utils.md) | *Class level change* |
| 🟡 `MOD` | [`ZCursor.cs`](Changes/assembly_utils/ZCursor.md) | *Class level change* |
| 🟡 `MOD` | [`ZInput.cs`](Changes/assembly_utils/ZInput.md) | *Class level change* |

---

## 🔧 Assembly: `assembly_valheim.dll` <a id="assembly_valheim"></a>

**Changes Summary:** `330` modified, `0` added, `0` deleted (`+3006` / `-2635` lines)

| Status | Class / File | Changed Scope / Signatures |
| :---: | :--- | :--- |
| 🟡 `MOD` | [`AchievementUnlockPopup.cs`](Changes/assembly_valheim/AchievementUnlockPopup.md) | *Class level change* |
| 🟡 `MOD` | [`Achievements.cs`](Changes/assembly_valheim/Achievements.md) | *Class level change* |
| 🟡 `MOD` | [`AltBiomeWorldData.cs`](Changes/assembly_valheim/AltBiomeWorldData.md) | *Class level change* |
| 🟡 `MOD` | [`AmplifyOcclusionEffect.cs`](Changes/assembly_valheim/AmplifyOcclusionEffect.md) | *Class level change* |
| 🟡 `MOD` | [`AnimalAI.cs`](Changes/assembly_valheim/AnimalAI.md) | *Class level change* |
| 🟡 `MOD` | [`AnimationObjectToggle.cs`](Changes/assembly_valheim/AnimationObjectToggle.md) | *Class level change* |
| 🟡 `MOD` | [`Aoe.cs`](Changes/assembly_valheim/Aoe.md) | *Class level change* |
| 🟡 `MOD` | [`ArcheryTarget.cs`](Changes/assembly_valheim/ArcheryTarget.md) | *Class level change* |
| 🟡 `MOD` | [`ArmorStand.cs`](Changes/assembly_valheim/ArmorStand.md) | *Class level change* |
| 🟡 `MOD` | [`Attack.cs`](Changes/assembly_valheim/Attack.md) | *Class level change* |
| 🟡 `MOD` | [`AudioMan.cs`](Changes/assembly_valheim/AudioMan.md) | *Class level change* |
| 🟡 `MOD` | [`AutoJumpLedge.cs`](Changes/assembly_valheim/AutoJumpLedge.md) | *Class level change* |
| 🟡 `MOD` | [`BaseAI.cs`](Changes/assembly_valheim/BaseAI.md) | *Class level change* |
| 🟡 `MOD` | [`Bed.cs`](Changes/assembly_valheim/Bed.md) | *Class level change* |
| 🟡 `MOD` | [`Beehive.cs`](Changes/assembly_valheim/Beehive.md) | *Class level change* |
| 🟡 `MOD` | [`Billboard.cs`](Changes/assembly_valheim/Billboard.md) | *Class level change* |
| 🟡 `MOD` | [`BlockCheckHandler.cs`](Changes/assembly_valheim/BlockCheckHandler.md) | *Class level change* |
| 🟡 `MOD` | [`BossStone.cs`](Changes/assembly_valheim/BossStone.md) | *Class level change* |
| 🟡 `MOD` | [`BuildUi.cs`](Changes/assembly_valheim/BuildUi.md) | *Class level change* |
| 🟡 `MOD` | [`BuildUiFavoritesDropdown.cs`](Changes/assembly_valheim/BuildUiFavoritesDropdown.md) | *Class level change* |
| 🟡 `MOD` | [`BuildUiTagButton.cs`](Changes/assembly_valheim/BuildUiTagButton.md) | *Class level change* |
| 🟡 `MOD` | [`ByMaterialPieceList.cs`](Changes/assembly_valheim/ByMaterialPieceList.md) | `private struct RequirementTagData(Piece.Requirement requirement)` |
| 🟡 `MOD` | [`CamShaker.cs`](Changes/assembly_valheim/CamShaker.md) | *Class level change* |
| 🟡 `MOD` | [`CameraEffects.cs`](Changes/assembly_valheim/CameraEffects.md) | *Class level change* |
| 🟡 `MOD` | [`CancelableTaskPopup.cs`](Changes/assembly_valheim/CancelableTaskPopup.md) | *Class level change* |
| 🟡 `MOD` | [`CaptionArrow.cs`](Changes/assembly_valheim/CaptionArrow.md) | *Class level change* |
| 🟡 `MOD` | [`CaptionItem.cs`](Changes/assembly_valheim/CaptionItem.md) | *Class level change* |
| 🟡 `MOD` | [`Catapult.cs`](Changes/assembly_valheim/Catapult.md) | *Class level change* |
| 🟡 `MOD` | [`CensorShittyWords.cs`](Changes/assembly_valheim/CensorShittyWords.md) | *Class level change* |
| 🟡 `MOD` | [`Character.cs`](Changes/assembly_valheim/Character.md) | *Class level change* |
| 🟡 `MOD` | [`CharacterAnimEvent.cs`](Changes/assembly_valheim/CharacterAnimEvent.md) | *Class level change* |
| 🟡 `MOD` | [`CharacterDrop.cs`](Changes/assembly_valheim/CharacterDrop.md) | *Class level change* |
| 🟡 `MOD` | [`CharacterTimedDestruction.cs`](Changes/assembly_valheim/CharacterTimedDestruction.md) | *Class level change* |
| 🟡 `MOD` | [`Chat.cs`](Changes/assembly_valheim/Chat.md) | *Class level change* |
| 🟡 `MOD` | [`ChunkSaveMapping.cs`](Changes/assembly_valheim/ChunkSaveMapping.md) | *Class level change* |
| 🟡 `MOD` | [`Cinder.cs`](Changes/assembly_valheim/Cinder.md) | *Class level change* |
| 🟡 `MOD` | [`CinderSpawner.cs`](Changes/assembly_valheim/CinderSpawner.md) | *Class level change* |
| 🟡 `MOD` | [`CinematicsHider.cs`](Changes/assembly_valheim/CinematicsHider.md) | *Class level change* |
| 🟡 `MOD` | [`CircleProjector.cs`](Changes/assembly_valheim/CircleProjector.md) | *Class level change* |
| 🟡 `MOD` | [`ClosedCaptions.cs`](Changes/assembly_valheim/ClosedCaptions.md) | *Class level change* |
| 🟡 `MOD` | [`ClutterSystem.cs`](Changes/assembly_valheim/ClutterSystem.md) | *Class level change* |
| 🟡 `MOD` | [`ConditionalObject.cs`](Changes/assembly_valheim/ConditionalObject.md) | *Class level change* |
| 🟡 `MOD` | [`Container.cs`](Changes/assembly_valheim/Container.md) | *Class level change* |
| 🟡 `MOD` | [`CookingStation.cs`](Changes/assembly_valheim/CookingStation.md) | *Class level change* |
| 🟡 `MOD` | [`CraftingStation.cs`](Changes/assembly_valheim/CraftingStation.md) | *Class level change* |
| 🟡 `MOD` | [`CreatureSpawner.cs`](Changes/assembly_valheim/CreatureSpawner.md) | *Class level change* |
| 🟡 `MOD` | [`DamageText.cs`](Changes/assembly_valheim/DamageText.md) | *Class level change* |
| 🟡 `MOD` | [`Demister.cs`](Changes/assembly_valheim/Demister.md) | *Class level change* |
| 🟡 `MOD` | [`DepthCamera.cs`](Changes/assembly_valheim/DepthCamera.md) | *Class level change* |
| 🟡 `MOD` | [`Destructible.cs`](Changes/assembly_valheim/Destructible.md) | *Class level change* |
| 🟡 `MOD` | [`DisableInPlacementGhost.cs`](Changes/assembly_valheim/DisableInPlacementGhost.md) | *Class level change* |
| 🟡 `MOD` | [`DistantFogEmitter.cs`](Changes/assembly_valheim/DistantFogEmitter.md) | *Class level change* |
| 🟡 `MOD` | [`DnsResolveRequest.cs`](Changes/assembly_valheim/DnsResolveRequest.md) | *Class level change* |
| 🟡 `MOD` | [`Door.cs`](Changes/assembly_valheim/Door.md) | *Class level change* |
| 🟡 `MOD` | [`DropOnDestroyed.cs`](Changes/assembly_valheim/DropOnDestroyed.md) | *Class level change* |
| 🟡 `MOD` | [`DropProjectileOverDistance.cs`](Changes/assembly_valheim/DropProjectileOverDistance.md) | *Class level change* |
| 🟡 `MOD` | [`DropTable.cs`](Changes/assembly_valheim/DropTable.md) | *Class level change* |
| 🟡 `MOD` | [`DungeonDB.cs`](Changes/assembly_valheim/DungeonDB.md) | *Class level change* |
| 🟡 `MOD` | [`DungeonGenerator.cs`](Changes/assembly_valheim/DungeonGenerator.md) | *Class level change* |
| 🟡 `MOD` | [`EffectArea.cs`](Changes/assembly_valheim/EffectArea.md) | *Class level change* |
| 🟡 `MOD` | [`EffectFade.cs`](Changes/assembly_valheim/EffectFade.md) | *Class level change* |
| 🟡 `MOD` | [`EggGrow.cs`](Changes/assembly_valheim/EggGrow.md) | *Class level change* |
| 🟡 `MOD` | [`EggHatch.cs`](Changes/assembly_valheim/EggHatch.md) | *Class level change* |
| 🟡 `MOD` | [`EmitterRotation.cs`](Changes/assembly_valheim/EmitterRotation.md) | *Class level change* |
| 🟡 `MOD` | [`EnemyHud.cs`](Changes/assembly_valheim/EnemyHud.md) | *Class level change* |
| 🟡 `MOD` | [`FavoritePieceList.cs`](Changes/assembly_valheim/FavoritePieceList.md) | *Class level change* |
| 🟡 `MOD` | [`Feast.cs`](Changes/assembly_valheim/Feast.md) | *Class level change* |
| 🟡 `MOD` | [`Feedback.cs`](Changes/assembly_valheim/Feedback.md) | *Class level change* |
| 🟡 `MOD` | [`FejdStartup.cs`](Changes/assembly_valheim/FejdStartup.md) | *Class level change* |
| 🟡 `MOD` | [`Fermenter.cs`](Changes/assembly_valheim/Fermenter.md) | *Class level change* |
| 🟡 `MOD` | [`Fire.cs`](Changes/assembly_valheim/Fire.md) | *Class level change* |
| 🟡 `MOD` | [`Fireplace.cs`](Changes/assembly_valheim/Fireplace.md) | *Class level change* |
| 🟡 `MOD` | [`Fish.cs`](Changes/assembly_valheim/Fish.md) | *Class level change* |
| 🟡 `MOD` | [`FishingFloat.cs`](Changes/assembly_valheim/FishingFloat.md) | *Class level change* |
| 🟡 `MOD` | [`Floating.cs`](Changes/assembly_valheim/Floating.md) | *Class level change* |
| 🟡 `MOD` | [`FloatingTerrain.cs`](Changes/assembly_valheim/FloatingTerrain.md) | *Class level change* |
| 🟡 `MOD` | [`FollowPlayer.cs`](Changes/assembly_valheim/FollowPlayer.md) | *Class level change* |
| 🟡 `MOD` | [`FootStep.cs`](Changes/assembly_valheim/FootStep.md) | *Class level change* |
| 🟡 `MOD` | [`FriendsServerList.cs`](Changes/assembly_valheim/FriendsServerList.md) | *Class level change* |
| 🟡 `MOD` | [`Game.cs`](Changes/assembly_valheim/Game.md) | *Class level change* |
| 🟡 `MOD` | [`GameCamera.cs`](Changes/assembly_valheim/GameCamera.md) | *Class level change* |
| 🟡 `MOD` | [`GameVersion.cs`](Changes/assembly_valheim/GameVersion.md) | *Class level change* |
| 🟡 `MOD` | [`GamepadMotionSensor.cs`](Changes/assembly_valheim/GamepadMotionSensor.md) | *Class level change* |
| 🟡 `MOD` | [`GamepadRumble.cs`](Changes/assembly_valheim/GamepadRumble.md) | *Class level change* |
| 🟡 `MOD` | [`Gibber.cs`](Changes/assembly_valheim/Gibber.md) | *Class level change* |
| 🟡 `MOD` | [`GlobalGraphicsConfiguration.cs`](Changes/assembly_valheim/GlobalGraphicsConfiguration.md) | *Class level change* |
| 🟡 `MOD` | [`GlobalWind.cs`](Changes/assembly_valheim/GlobalWind.md) | *Class level change* |
| 🟡 `MOD` | [`GraphicsSettingsManager.cs`](Changes/assembly_valheim/GraphicsSettingsManager.md) | *Class level change* |
| 🟡 `MOD` | [`GraphicsSettingsPreset.cs`](Changes/assembly_valheim/GraphicsSettingsPreset.md) | *Class level change* |
| 🟡 `MOD` | [`GraphicsSettingsState.cs`](Changes/assembly_valheim/GraphicsSettingsState.md) | *Class level change* |
| 🟡 `MOD` | [`GrapplingPoint.cs`](Changes/assembly_valheim/GrapplingPoint.md) | *Class level change* |
| 🟡 `MOD` | [`Growup.cs`](Changes/assembly_valheim/Growup.md) | *Class level change* |
| 🟡 `MOD` | [`Heightmap.cs`](Changes/assembly_valheim/Heightmap.md) | *Class level change* |
| 🟡 `MOD` | [`HitData.cs`](Changes/assembly_valheim/HitData.md) | *Class level change* |
| 🟡 `MOD` | [`HotkeyBar.cs`](Changes/assembly_valheim/HotkeyBar.md) | *Class level change* |
| 🟡 `MOD` | [`Hud.cs`](Changes/assembly_valheim/Hud.md) | *Class level change* |
| 🟡 `MOD` | [`Humanoid.cs`](Changes/assembly_valheim/Humanoid.md) | *Class level change* |
| 🟡 `MOD` | [`ImpactEffect.cs`](Changes/assembly_valheim/ImpactEffect.md) | *Class level change* |
| 🟡 `MOD` | [`Incinerator.cs`](Changes/assembly_valheim/Incinerator.md) | *Class level change* |
| 🟡 `MOD` | [`InstanceRenderer.cs`](Changes/assembly_valheim/InstanceRenderer.md) | *Class level change* |
| 🟡 `MOD` | [`InstantiatePrefab.cs`](Changes/assembly_valheim/InstantiatePrefab.md) | *Class level change* |
| 🟡 `MOD` | [`Interpolate.cs`](Changes/assembly_valheim/Interpolate.md) | *Class level change* |
| 🟡 `MOD` | [`InventoryElement.cs`](Changes/assembly_valheim/InventoryElement.md) | *Class level change* |
| 🟡 `MOD` | [`InventoryGrid.cs`](Changes/assembly_valheim/InventoryGrid.md) | *Class level change* |
| 🟡 `MOD` | [`InventoryGui.cs`](Changes/assembly_valheim/InventoryGui.md) | *Class level change* |
| 🟡 `MOD` | [`ItemDrop.cs`](Changes/assembly_valheim/ItemDrop.md) | *Class level change* |
| 🟡 `MOD` | [`ItemStand.cs`](Changes/assembly_valheim/ItemStand.md) | *Class level change* |
| 🟡 `MOD` | [`ItemStyle.cs`](Changes/assembly_valheim/ItemStyle.md) | *Class level change* |
| 🟡 `MOD` | [`KeyButton.cs`](Changes/assembly_valheim/KeyButton.md) | *Class level change* |
| 🟡 `MOD` | [`KeySlider.cs`](Changes/assembly_valheim/KeySlider.md) | *Class level change* |
| 🟡 `MOD` | [`KeyToggle.cs`](Changes/assembly_valheim/KeyToggle.md) | *Class level change* |
| 🟡 `MOD` | [`KeyUI.cs`](Changes/assembly_valheim/KeyUI.md) | *Class level change* |
| 🟡 `MOD` | [`Ladder.cs`](Changes/assembly_valheim/Ladder.md) | *Class level change* |
| 🟡 `MOD` | [`Ledge.cs`](Changes/assembly_valheim/Ledge.md) | *Class level change* |
| 🟡 `MOD` | [`LevelEffects.cs`](Changes/assembly_valheim/LevelEffects.md) | *Class level change* |
| 🟡 `MOD` | [`Leviathan.cs`](Changes/assembly_valheim/Leviathan.md) | *Class level change* |
| 🟡 `MOD` | [`LightFlicker.cs`](Changes/assembly_valheim/LightFlicker.md) | *Class level change* |
| 🟡 `MOD` | [`LightLod.cs`](Changes/assembly_valheim/LightLod.md) | *Class level change* |
| 🟡 `MOD` | [`LineConnect.cs`](Changes/assembly_valheim/LineConnect.md) | *Class level change* |
| 🟡 `MOD` | [`LiquidVolume.cs`](Changes/assembly_valheim/LiquidVolume.md) | *Class level change* |
| 🟡 `MOD` | [`LocalServerList.cs`](Changes/assembly_valheim/LocalServerList.md) | *Class level change* |
| 🟡 `MOD` | [`Location.cs`](Changes/assembly_valheim/Location.md) | *Class level change* |
| 🟡 `MOD` | [`LocationProxy.cs`](Changes/assembly_valheim/LocationProxy.md) | *Class level change* |
| 🟡 `MOD` | [`LodFadeInOut.cs`](Changes/assembly_valheim/LodFadeInOut.md) | *Class level change* |
| 🟡 `MOD` | [`LootSpawner.cs`](Changes/assembly_valheim/LootSpawner.md) | *Class level change* |
| 🟡 `MOD` | [`LuredWisp.cs`](Changes/assembly_valheim/LuredWisp.md) | *Class level change* |
| 🟡 `MOD` | [`ManageSavesMenu.cs`](Changes/assembly_valheim/ManageSavesMenu.md) | *Class level change* |
| 🟡 `MOD` | [`ManageSavesMenuElement.cs`](Changes/assembly_valheim/ManageSavesMenuElement.md) | *Class level change* |
| 🟡 `MOD` | [`MapTable.cs`](Changes/assembly_valheim/MapTable.md) | *Class level change* |
| 🟡 `MOD` | [`MatchmakingManager.cs`](Changes/assembly_valheim/MatchmakingManager.md) | *Class level change* |
| 🟡 `MOD` | [`MaterialManNotifier.cs`](Changes/assembly_valheim/MaterialManNotifier.md) | *Class level change* |
| 🟡 `MOD` | [`MaterialVariation.cs`](Changes/assembly_valheim/MaterialVariation.md) | *Class level change* |
| 🟡 `MOD` | [`MaterialVariationWorld.cs`](Changes/assembly_valheim/MaterialVariationWorld.md) | *Class level change* |
| 🟡 `MOD` | [`MeleeWeaponTrail.cs`](Changes/assembly_valheim/MeleeWeaponTrail.md) | *Class level change* |
| 🟡 `MOD` | [`Menu.cs`](Changes/assembly_valheim/Menu.md) | *Class level change* |
| 🟡 `MOD` | [`MenuShipMovement.cs`](Changes/assembly_valheim/MenuShipMovement.md) | *Class level change* |
| 🟡 `MOD` | [`MessageHud.cs`](Changes/assembly_valheim/MessageHud.md) | *Class level change* |
| 🟡 `MOD` | [`MeteorSmash.cs`](Changes/assembly_valheim/MeteorSmash.md) | *Class level change* |
| 🟡 `MOD` | [`MineRock.cs`](Changes/assembly_valheim/MineRock.md) | *Class level change* |
| 🟡 `MOD` | [`MineRock5.cs`](Changes/assembly_valheim/MineRock5.md) | *Class level change* |
| 🟡 `MOD` | [`Minimap.cs`](Changes/assembly_valheim/Minimap.md) | *Class level change* |
| 🟡 `MOD` | [`MistEmitter.cs`](Changes/assembly_valheim/MistEmitter.md) | *Class level change* |
| 🟡 `MOD` | [`Mister.cs`](Changes/assembly_valheim/Mister.md) | *Class level change* |
| 🟡 `MOD` | [`MonsterAI.cs`](Changes/assembly_valheim/MonsterAI.md) | *Class level change* |
| 🟡 `MOD` | [`MovementTest.cs`](Changes/assembly_valheim/MovementTest.md) | *Class level change* |
| 🟡 `MOD` | [`MultiBackendMatchmaking.cs`](Changes/assembly_valheim/MultiBackendMatchmaking.md) | *Class level change* |
| 🟡 `MOD` | [`MusicLocation.cs`](Changes/assembly_valheim/MusicLocation.md) | *Class level change* |
| 🟡 `MOD` | [`MusicMan.cs`](Changes/assembly_valheim/MusicMan.md) | *Class level change* |
| 🟡 `MOD` | [`MusicVolume.cs`](Changes/assembly_valheim/MusicVolume.md) | *Class level change* |
| 🟡 `MOD` | [`NavmeshTest.cs`](Changes/assembly_valheim/NavmeshTest.md) | *Class level change* |
| 🟡 `MOD` | [`NpcTalk.cs`](Changes/assembly_valheim/NpcTalk.md) | *Class level change* |
| 🟡 `MOD` | [`ObjectDB.cs`](Changes/assembly_valheim/ObjectDB.md) | `public List<ItemDrop> GetAllFoodItems()`<br>`public List<ItemDrop> GetAllFoodItems(List<GameObject> itemsExcluded)` |
| 🟡 `MOD` | [`ObjectFlicker.cs`](Changes/assembly_valheim/ObjectFlicker.md) | *Class level change* |
| 🟡 `MOD` | [`Odin.cs`](Changes/assembly_valheim/Odin.md) | *Class level change* |
| 🟡 `MOD` | [`OfferingBowl.cs`](Changes/assembly_valheim/OfferingBowl.md) | *Class level change* |
| 🟡 `MOD` | [`OpenRadialConfig.cs`](Changes/assembly_valheim/OpenRadialConfig.md) | *Class level change* |
| 🟡 `MOD` | [`ParticleIntensityScaler.cs`](Changes/assembly_valheim/ParticleIntensityScaler.md) | *Class level change* |
| 🟡 `MOD` | [`ParticleMist.cs`](Changes/assembly_valheim/ParticleMist.md) | *Class level change* |
| 🟡 `MOD` | [`Pet.cs`](Changes/assembly_valheim/Pet.md) | *Class level change* |
| 🟡 `MOD` | [`Petable.cs`](Changes/assembly_valheim/Petable.md) | *Class level change* |
| 🟡 `MOD` | [`Pickable.cs`](Changes/assembly_valheim/Pickable.md) | *Class level change* |
| 🟡 `MOD` | [`PickableItem.cs`](Changes/assembly_valheim/PickableItem.md) | *Class level change* |
| 🟡 `MOD` | [`Piece.cs`](Changes/assembly_valheim/Piece.md) | *Class level change* |
| 🟡 `MOD` | [`Plant.cs`](Changes/assembly_valheim/Plant.md) | *Class level change* |
| 🟡 `MOD` | [`PlatformEnable.cs`](Changes/assembly_valheim/PlatformEnable.md) | *Class level change* |
| 🟡 `MOD` | [`PlatformInitializer.cs`](Changes/assembly_valheim/PlatformInitializer.md) | *Class level change* |
| 🟡 `MOD` | [`PlayFabAuthWithSteam.cs`](Changes/assembly_valheim/PlayFabAuthWithSteam.md) | *Class level change* |
| 🟡 `MOD` | [`PlayFabManager.cs`](Changes/assembly_valheim/PlayFabManager.md) | *Class level change* |
| 🟡 `MOD` | [`Player.cs`](Changes/assembly_valheim/Player.md) | *Class level change* |
| 🟡 `MOD` | [`PlayerClothWindShelter.cs`](Changes/assembly_valheim/PlayerClothWindShelter.md) | *Class level change* |
| 🟡 `MOD` | [`PlayerController.cs`](Changes/assembly_valheim/PlayerController.md) | *Class level change* |
| 🟡 `MOD` | [`PlayerProfile.cs`](Changes/assembly_valheim/PlayerProfile.md) | *Class level change* |
| 🟡 `MOD` | [`PresentManager.cs`](Changes/assembly_valheim/PresentManager.md) | *Class level change* |
| 🟡 `MOD` | [`PrivateArea.cs`](Changes/assembly_valheim/PrivateArea.md) | *Class level change* |
| 🟡 `MOD` | [`PrivilegeManager.cs`](Changes/assembly_valheim/PrivilegeManager.md) | *Class level change* |
| 🟡 `MOD` | [`Procreation.cs`](Changes/assembly_valheim/Procreation.md) | *Class level change* |
| 🟡 `MOD` | [`Projectile.cs`](Changes/assembly_valheim/Projectile.md) | *Class level change* |
| 🟡 `MOD` | [`ProximityState.cs`](Changes/assembly_valheim/ProximityState.md) | *Class level change* |
| 🟡 `MOD` | [`Radiator.cs`](Changes/assembly_valheim/Radiator.md) | *Class level change* |
| 🟡 `MOD` | [`Ragdoll.cs`](Changes/assembly_valheim/Ragdoll.md) | *Class level change* |
| 🟡 `MOD` | [`RandEventSystem.cs`](Changes/assembly_valheim/RandEventSystem.md) | *Class level change* |
| 🟡 `MOD` | [`RandomFlyingBird.cs`](Changes/assembly_valheim/RandomFlyingBird.md) | *Class level change* |
| 🟡 `MOD` | [`RandomMaterialValues.cs`](Changes/assembly_valheim/RandomMaterialValues.md) | *Class level change* |
| 🟡 `MOD` | [`RandomMovement.cs`](Changes/assembly_valheim/RandomMovement.md) | *Class level change* |
| 🟡 `MOD` | [`RandomObject.cs`](Changes/assembly_valheim/RandomObject.md) | *Class level change* |
| 🟡 `MOD` | [`RandomPieceRotation.cs`](Changes/assembly_valheim/RandomPieceRotation.md) | *Class level change* |
| 🟡 `MOD` | [`RandomSpawn.cs`](Changes/assembly_valheim/RandomSpawn.md) | *Class level change* |
| 🟡 `MOD` | [`RandomSpeak.cs`](Changes/assembly_valheim/RandomSpeak.md) | *Class level change* |
| 🟡 `MOD` | [`Raven.cs`](Changes/assembly_valheim/Raven.md) | *Class level change* |
| 🟡 `MOD` | [`ReflectionUpdate.cs`](Changes/assembly_valheim/ReflectionUpdate.md) | *Class level change* |
| 🟡 `MOD` | [`ReportUser.cs`](Changes/assembly_valheim/ReportUser.md) | *Class level change* |
| 🟡 `MOD` | [`ResourceRoot.cs`](Changes/assembly_valheim/ResourceRoot.md) | *Class level change* |
| 🟡 `MOD` | [`Room.cs`](Changes/assembly_valheim/Room.md) | *Class level change* |
| 🟡 `MOD` | [`RoomConnection.cs`](Changes/assembly_valheim/RoomConnection.md) | *Class level change* |
| 🟡 `MOD` | [`RopeAttachment.cs`](Changes/assembly_valheim/RopeAttachment.md) | *Class level change* |
| 🟡 `MOD` | [`RuneStone.cs`](Changes/assembly_valheim/RuneStone.md) | *Class level change* |
| 🟡 `MOD` | [`SE_Demister.cs`](Changes/assembly_valheim/SE_Demister.md) | *Class level change* |
| 🟡 `MOD` | [`SE_React.cs`](Changes/assembly_valheim/SE_React.md) | *Class level change* |
| 🟡 `MOD` | [`Sadle.cs`](Changes/assembly_valheim/Sadle.md) | *Class level change* |
| 🟡 `MOD` | [`SapCollector.cs`](Changes/assembly_valheim/SapCollector.md) | *Class level change* |
| 🟡 `MOD` | [`SaveSystem.cs`](Changes/assembly_valheim/SaveSystem.md) | *Class level change* |
| 🟡 `MOD` | [`ServerData.cs`](Changes/assembly_valheim/ServerData.md) | *Class level change* |
| 🟡 `MOD` | [`ServerJoinData.cs`](Changes/assembly_valheim/ServerJoinData.md) | *Class level change* |
| 🟡 `MOD` | [`ServerListEntryData.cs`](Changes/assembly_valheim/ServerListEntryData.md) | *Class level change* |
| 🟡 `MOD` | [`ServerListGui.cs`](Changes/assembly_valheim/ServerListGui.md) | *Class level change* |
| 🟡 `MOD` | [`ServerMatchmakingData.cs`](Changes/assembly_valheim/ServerMatchmakingData.md) | *Class level change* |
| 🟡 `MOD` | [`ServerOptionsGUI.cs`](Changes/assembly_valheim/ServerOptionsGUI.md) | *Class level change* |
| 🟡 `MOD` | [`Settings.cs`](Changes/assembly_valheim/Settings.md) | *Class level change* |
| 🟡 `MOD` | [`ShieldDomeImageEffect.cs`](Changes/assembly_valheim/ShieldDomeImageEffect.md) | *Class level change* |
| 🟡 `MOD` | [`ShieldDomeParticleColor.cs`](Changes/assembly_valheim/ShieldDomeParticleColor.md) | *Class level change* |
| 🟡 `MOD` | [`ShieldGenerator.cs`](Changes/assembly_valheim/ShieldGenerator.md) | *Class level change* |
| 🟡 `MOD` | [`Ship.cs`](Changes/assembly_valheim/Ship.md) | *Class level change* |
| 🟡 `MOD` | [`ShipControlls.cs`](Changes/assembly_valheim/ShipControlls.md) | *Class level change* |
| 🟡 `MOD` | [`ShipEffects.cs`](Changes/assembly_valheim/ShipEffects.md) | *Class level change* |
| 🟡 `MOD` | [`SiegeMachine.cs`](Changes/assembly_valheim/SiegeMachine.md) | *Class level change* |
| 🟡 `MOD` | [`Sign.cs`](Changes/assembly_valheim/Sign.md) | *Class level change* |
| 🟡 `MOD` | [`SkillsDialog.cs`](Changes/assembly_valheim/SkillsDialog.md) | *Class level change* |
| 🟡 `MOD` | [`Smelter.cs`](Changes/assembly_valheim/Smelter.md) | *Class level change* |
| 🟡 `MOD` | [`Smoke.cs`](Changes/assembly_valheim/Smoke.md) | *Class level change* |
| 🟡 `MOD` | [`SmokeRenderer.cs`](Changes/assembly_valheim/SmokeRenderer.md) | *Class level change* |
| 🟡 `MOD` | [`SmokeSpawner.cs`](Changes/assembly_valheim/SmokeSpawner.md) | *Class level change* |
| 🟡 `MOD` | [`SnapToGround.cs`](Changes/assembly_valheim/SnapToGround.md) | *Class level change* |
| 🟡 `MOD` | [`SnowDestruction.cs`](Changes/assembly_valheim/SnowDestruction.md) | *Class level change* |
| 🟡 `MOD` | [`SnowRoller.cs`](Changes/assembly_valheim/SnowRoller.md) | *Class level change* |
| 🟡 `MOD` | [`SoftReferencePrefabSpawner.cs`](Changes/assembly_valheim/SoftReferencePrefabSpawner.md) | *Class level change* |
| 🟡 `MOD` | [`SpawnAbility.cs`](Changes/assembly_valheim/SpawnAbility.md) | *Class level change* |
| 🟡 `MOD` | [`SpawnArea.cs`](Changes/assembly_valheim/SpawnArea.md) | *Class level change* |
| 🟡 `MOD` | [`SpawnOnDamaged.cs`](Changes/assembly_valheim/SpawnOnDamaged.md) | *Class level change* |
| 🟡 `MOD` | [`SpawnPrefab.cs`](Changes/assembly_valheim/SpawnPrefab.md) | *Class level change* |
| 🟡 `MOD` | [`SpawnSystem.cs`](Changes/assembly_valheim/SpawnSystem.md) | *Class level change* |
| 🟡 `MOD` | [`SpawnSystemList.cs`](Changes/assembly_valheim/SpawnSystemList.md) | *Class level change* |
| 🟡 `MOD` | [`SplitDialog.cs`](Changes/assembly_valheim/SplitDialog.md) | *Class level change* |
| 🟡 `MOD` | [`StartupMessages.cs`](Changes/assembly_valheim/StartupMessages.md) | *Class level change* |
| 🟡 `MOD` | [`StaticPhysics.cs`](Changes/assembly_valheim/StaticPhysics.md) | *Class level change* |
| 🟡 `MOD` | [`StaticRotation.cs`](Changes/assembly_valheim/StaticRotation.md) | *Class level change* |
| 🟡 `MOD` | [`StaticTarget.cs`](Changes/assembly_valheim/StaticTarget.md) | *Class level change* |
| 🟡 `MOD` | [`StationExtension.cs`](Changes/assembly_valheim/StationExtension.md) | *Class level change* |
| 🟡 `MOD` | [`StatusEffect.cs`](Changes/assembly_valheim/StatusEffect.md) | *Class level change* |
| 🟡 `MOD` | [`SteamManager.cs`](Changes/assembly_valheim/SteamManager.md) | *Class level change* |
| 🟡 `MOD` | [`SteamManager2.cs`](Changes/assembly_valheim/SteamManager2.md) | *Class level change* |
| 🟡 `MOD` | [`StoreGui.cs`](Changes/assembly_valheim/StoreGui.md) | *Class level change* |
| 🟡 `MOD` | [`SuspendManager.cs`](Changes/assembly_valheim/SuspendManager.md) | *Class level change* |
| 🟡 `MOD` | [`SystemResourceManager.cs`](Changes/assembly_valheim/SystemResourceManager.md) | *Class level change* |
| 🟡 `MOD` | [`TabHandler.cs`](Changes/assembly_valheim/TabHandler.md) | *Class level change* |
| 🟡 `MOD` | [`Talker.cs`](Changes/assembly_valheim/Talker.md) | *Class level change* |
| 🟡 `MOD` | [`Tameable.cs`](Changes/assembly_valheim/Tameable.md) | *Class level change* |
| 🟡 `MOD` | [`Teleport.cs`](Changes/assembly_valheim/Teleport.md) | *Class level change* |
| 🟡 `MOD` | [`TeleportAbility.cs`](Changes/assembly_valheim/TeleportAbility.md) | *Class level change* |
| 🟡 `MOD` | [`TeleportWorld.cs`](Changes/assembly_valheim/TeleportWorld.md) | *Class level change* |
| 🟡 `MOD` | [`Terminal.cs`](Changes/assembly_valheim/Terminal.md) | *Class level change* |
| 🟡 `MOD` | [`TerrainComp.cs`](Changes/assembly_valheim/TerrainComp.md) | `private void Start()`<br>`private void TryCleanInvalidTCs()`<br>`public static List<TerrainComp> FindAllTerrainCompilers(Vector3 pos)`<br>`public static bool ValidTCForAllAffectedHeightmaps(Vector3 pos, float radius)` |
| 🟡 `MOD` | [`TerrainLod.cs`](Changes/assembly_valheim/TerrainLod.md) | *Class level change* |
| 🟡 `MOD` | [`TerrainModifier.cs`](Changes/assembly_valheim/TerrainModifier.md) | *Class level change* |
| 🟡 `MOD` | [`TerrainOp.cs`](Changes/assembly_valheim/TerrainOp.md) | *Class level change* |
| 🟡 `MOD` | [`TestSceneCharacter.cs`](Changes/assembly_valheim/TestSceneCharacter.md) | *Class level change* |
| 🟡 `MOD` | [`TextsDialog.cs`](Changes/assembly_valheim/TextsDialog.md) | *Class level change* |
| 🟡 `MOD` | [`ThorFly.cs`](Changes/assembly_valheim/ThorFly.md) | *Class level change* |
| 🟡 `MOD` | [`Thunder.cs`](Changes/assembly_valheim/Thunder.md) | *Class level change* |
| 🟡 `MOD` | [`TimedDestruction.cs`](Changes/assembly_valheim/TimedDestruction.md) | *Class level change* |
| 🟡 `MOD` | [`TombStone.cs`](Changes/assembly_valheim/TombStone.md) | *Class level change* |
| 🟡 `MOD` | [`Tracker.cs`](Changes/assembly_valheim/Tracker.md) | *Class level change* |
| 🟡 `MOD` | [`Trader.cs`](Changes/assembly_valheim/Trader.md) | *Class level change* |
| 🟡 `MOD` | [`Trap.cs`](Changes/assembly_valheim/Trap.md) | *Class level change* |
| 🟡 `MOD` | [`TreeBase.cs`](Changes/assembly_valheim/TreeBase.md) | *Class level change* |
| 🟡 `MOD` | [`TreeLog.cs`](Changes/assembly_valheim/TreeLog.md) | *Class level change* |
| 🟡 `MOD` | [`TriggerPersistentEventOnDestroy.cs`](Changes/assembly_valheim/TriggerPersistentEventOnDestroy.md) | *Class level change* |
| 🟡 `MOD` | [`TriggerSpawnAbility.cs`](Changes/assembly_valheim/TriggerSpawnAbility.md) | *Class level change* |
| 🟡 `MOD` | [`TriggerSpawner.cs`](Changes/assembly_valheim/TriggerSpawner.md) | *Class level change* |
| 🟡 `MOD` | [`Turret.cs`](Changes/assembly_valheim/Turret.md) | *Class level change* |
| 🟡 `MOD` | [`UIGamePad.cs`](Changes/assembly_valheim/UIGamePad.md) | *Class level change* |
| 🟡 `MOD` | [`UnifiedPopup.cs`](Changes/assembly_valheim/UnifiedPopup.md) | *Class level change* |
| 🟡 `MOD` | [`UpscaledFrameBuffer.cs`](Changes/assembly_valheim/UpscaledFrameBuffer.md) | *Class level change* |
| 🟡 `MOD` | [`UserManagement/PlayerListManagement.cs`](Changes/assembly_valheim/PlayerListManagement.md) | *Class level change* |
| 🟡 `MOD` | [`Vagon.cs`](Changes/assembly_valheim/Vagon.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.SettingsGui/GamepadSettings.cs`](Changes/assembly_valheim/GamepadSettings.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.SettingsGui/GameplaySettings.cs`](Changes/assembly_valheim/GameplaySettings.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.SettingsGui/GraphicsSettings.cs`](Changes/assembly_valheim/GraphicsSettings.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.SettingsGui/KeyboardMouseSettings.cs`](Changes/assembly_valheim/KeyboardMouseSettings.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.SettingsGui/ResolutionSwitchDialogTimedRemoval.cs`](Changes/assembly_valheim/ResolutionSwitchDialogTimedRemoval.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.SettingsGui/SettingsTooltip.cs`](Changes/assembly_valheim/SettingsTooltip.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/BackElement.cs`](Changes/assembly_valheim/BackElement.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/EasingFunctions.cs`](Changes/assembly_valheim/EasingFunctions.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/ElementInfo.cs`](Changes/assembly_valheim/ElementInfo.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/EmoteElement.cs`](Changes/assembly_valheim/EmoteElement.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/EmptyElement.cs`](Changes/assembly_valheim/EmptyElement.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/GroupElement.cs`](Changes/assembly_valheim/GroupElement.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/HammerItemElement.cs`](Changes/assembly_valheim/HammerItemElement.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/ItemElement.cs`](Changes/assembly_valheim/ItemElement.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/ItemGroupConfig.cs`](Changes/assembly_valheim/ItemGroupConfig.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/RadialArray.cs`](Changes/assembly_valheim/RadialArray.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/RadialBase.cs`](Changes/assembly_valheim/RadialBase.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/RadialConfigHelper.cs`](Changes/assembly_valheim/RadialConfigHelper.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/RadialInventoryInfo.cs`](Changes/assembly_valheim/RadialInventoryInfo.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/RadialMenuAnimationManager.cs`](Changes/assembly_valheim/RadialMenuAnimationManager.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/RadialMenuElement.cs`](Changes/assembly_valheim/RadialMenuElement.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/ScrollRectExtensions.cs`](Changes/assembly_valheim/ScrollRectExtensions.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/SessionPlayerList.cs`](Changes/assembly_valheim/SessionPlayerList.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/SessionPlayerListEntry.cs`](Changes/assembly_valheim/SessionPlayerListEntry.md) | `private void OnDestroy()` |
| 🟡 `MOD` | [`Valheim.UI/ThrowElement.cs`](Changes/assembly_valheim/ThrowElement.md) | *Class level change* |
| 🟡 `MOD` | [`Valheim.UI/ThrowGroupConfig.cs`](Changes/assembly_valheim/ThrowGroupConfig.md) | *Class level change* |
| 🟡 `MOD` | [`Valkyrie.cs`](Changes/assembly_valheim/Valkyrie.md) | *Class level change* |
| 🟡 `MOD` | [`VariantDialog.cs`](Changes/assembly_valheim/VariantDialog.md) | *Class level change* |
| 🟡 `MOD` | [`Vegvisir.cs`](Changes/assembly_valheim/Vegvisir.md) | *Class level change* |
| 🟡 `MOD` | [`Version.cs`](Changes/assembly_valheim/Version.md) | *Class level change* |
| 🟡 `MOD` | [`Vine.cs`](Changes/assembly_valheim/Vine.md) | *Class level change* |
| 🟡 `MOD` | [`VisEquipment.cs`](Changes/assembly_valheim/VisEquipment.md) | *Class level change* |
| 🟡 `MOD` | [`VortexParticles.cs`](Changes/assembly_valheim/VortexParticles.md) | *Class level change* |
| 🟡 `MOD` | [`WarriorNames.cs`](Changes/assembly_valheim/WarriorNames.md) | *Class level change* |
| 🟡 `MOD` | [`WaterVolume.cs`](Changes/assembly_valheim/WaterVolume.md) | *Class level change* |
| 🟡 `MOD` | [`WayStone.cs`](Changes/assembly_valheim/WayStone.md) | *Class level change* |
| 🟡 `MOD` | [`WearNTear.cs`](Changes/assembly_valheim/WearNTear.md) | *Class level change* |
| 🟡 `MOD` | [`World.cs`](Changes/assembly_valheim/World.md) | *Class level change* |
| 🟡 `MOD` | [`WrapParticles.cs`](Changes/assembly_valheim/WrapParticles.md) | *Class level change* |
| 🟡 `MOD` | [`ZDO.cs`](Changes/assembly_valheim/ZDO.md) | *Class level change* |
| 🟡 `MOD` | [`ZDODataHelper.cs`](Changes/assembly_valheim/ZDODataHelper.md) | *Class level change* |
| 🟡 `MOD` | [`ZDOHelper.cs`](Changes/assembly_valheim/ZDOHelper.md) | *Class level change* |
| 🟡 `MOD` | [`ZDOMan.cs`](Changes/assembly_valheim/ZDOMan.md) | *Class level change* |
| 🟡 `MOD` | [`ZNet.cs`](Changes/assembly_valheim/ZNet.md) | *Class level change* |
| 🟡 `MOD` | [`ZNetScene.cs`](Changes/assembly_valheim/ZNetScene.md) | *Class level change* |
| 🟡 `MOD` | [`ZNetView.cs`](Changes/assembly_valheim/ZNetView.md) | *Class level change* |
| 🟡 `MOD` | [`ZPackage.cs`](Changes/assembly_valheim/ZPackage.md) | *Class level change* |
| 🟡 `MOD` | [`ZPlayFabLobbySearch.cs`](Changes/assembly_valheim/ZPlayFabLobbySearch.md) | *Class level change* |
| 🟡 `MOD` | [`ZPlayFabMatchmaking.cs`](Changes/assembly_valheim/ZPlayFabMatchmaking.md) | *Class level change* |
| 🟡 `MOD` | [`ZPlayFabSocket.cs`](Changes/assembly_valheim/ZPlayFabSocket.md) | *Class level change* |
| 🟡 `MOD` | [`ZSFX.cs`](Changes/assembly_valheim/ZSFX.md) | *Class level change* |
| 🟡 `MOD` | [`ZSteamMatchmaking.cs`](Changes/assembly_valheim/ZSteamMatchmaking.md) | *Class level change* |
| 🟡 `MOD` | [`ZSteamSocket.cs`](Changes/assembly_valheim/ZSteamSocket.md) | *Class level change* |
| 🟡 `MOD` | [`ZSyncAnimation.cs`](Changes/assembly_valheim/ZSyncAnimation.md) | *Class level change* |
| 🟡 `MOD` | [`ZSyncTransform.cs`](Changes/assembly_valheim/ZSyncTransform.md) | *Class level change* |
| 🟡 `MOD` | [`ZoneSystem.cs`](Changes/assembly_valheim/ZoneSystem.md) | *Class level change* |

---

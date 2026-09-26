# `Player.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+112/-113` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Player.cs
+++ b/Player.cs
@@ -721,7 +721,7 @@
 			m_localPlayer = this;
 			m_localPlayerExists = true;
 			Game.instance.IncrementPlayerStat(PlayerStatType.WorldLoads);
-			ZNet.instance.SetReferencePosition(base.transform.position);
+			ZNet.instance.SetReferencePosition(transform.position);
 			EnvMan.instance.SetForceEnvironment("");
 			AddQueuedKeys();
 		}
@@ -788,7 +788,7 @@
 		ZDO zDO = m_nview.GetZDO();
 		if (zDO != null && ZNet.instance != null)
 		{
-			ZLog.LogWarning("Player destroyed sec:" + zDO.GetSector().ToString() + "  pos:" + base.transform.position.ToString() + "  zdopos:" + zDO.GetPosition().ToString() + "  ref " + ZNet.instance.GetReferencePosition().ToString());
+			ZLog.LogWarning("Player destroyed sec:" + zDO.GetSector().ToString() + "  pos:" + transform.position.ToString() + "  zdopos:" + zDO.GetPosition().ToString() + "  ref " + ZNet.instance.GetReferencePosition().ToString());
 		}
 		if ((bool)m_placementGhost)
 		{
@@ -822,7 +822,7 @@
 		if (m_localPlayer != this)
 		{
 			ZLog.Log("Destroying old local player");
-			ZNetScene.instance.Destroy(base.gameObject);
+			ZNetScene.instance.Destroy(gameObject);
 		}
 		else if (!IsDead())
 		{
@@ -842,11 +842,11 @@
 			EdgeOfWorldKill(fixedDeltaTime);
 			UpdateBiome(fixedDeltaTime);
 			UpdateStealth(fixedDeltaTime);
-			if ((bool)GameCamera.instance && m_attachPointCamera == null && Vector3.Distance(GameCamera.instance.transform.position, base.transform.position) < 2f)
+			if ((bool)GameCamera.instance && m_attachPointCamera == null && Vector3.Distance(GameCamera.instance.transform.position, transform.position) < 2f)
 			{
 				SetVisible(visible: false);
 			}
-			AudioMan.instance.SetIndoor(InShelter() || ShieldGenerator.IsInsideShield(base.transform.position));
+			AudioMan.instance.SetIndoor(InShelter() || ShieldGenerator.IsInsideShield(transform.position));
 		}
 	}
 
@@ -866,7 +866,7 @@
 		UpdateClothFix();
 		if (Terminal.m_showTests)
 		{
-			Terminal.m_testList["Player Deepnorth Fade"] = WorldGenerator.DeepNorthWaveFade(base.transform.position.x, base.transform.position.z).ToString("0.00") + " / " + WorldGenerator.CreateDeepNorthGap(base.transform.position.x, base.transform.position.z).ToString("0.00");
+			Terminal.m_testList["Player Deepnorth Fade"] = WorldGenerator.DeepNorthWaveFade(transform.position.x, transform.position.z).ToString("0.00") + " / " + WorldGenerator.CreateDeepNorthGap(transform.position.x, transform.position.z).ToString("0.00");
 		}
 		if (!m_nview.IsValid() || !m_nview.IsOwner())
 		{
@@ -1181,7 +1181,7 @@
 		m_statCheck = 0f;
 		PlayerProfile playerProfile = Game.instance.GetPlayerProfile();
 		m_timeSinceLastCheck += 2.5f;
-		float num = Vector3.Distance(base.transform.position, m_lastDistCheck);
+		float num = Vector3.Distance(transform.position, m_lastDistCheck);
 		if (!(num > 1f))
 		{
 			return;
@@ -1207,7 +1207,7 @@
 				playerProfile.IncrementStat(PlayerStatType.DistanceAir, num);
 			}
 		}
-		if (base.transform.position.z > 10350f)
+		if (transform.position.z > 10350f)
 		{
 			Game.instance.IncrementPlayerStat(PlayerStatType.ExploreNorth, m_timeSinceLastCheck);
 			if (Achievements.IsCleanNoMap())
@@ -1215,7 +1215,7 @@
 				Game.instance.IncrementPlayerStat(PlayerStatType.ExploreNorthNoMap, m_timeSinceLastCheck);
 			}
 		}
-		if (base.transform.position.z < -10350f)
+		if (transform.position.z < -10350f)
 		{
 			Game.instance.IncrementPlayerStat(PlayerStatType.ExploreSouth, m_timeSinceLastCheck);
 			if (Achievements.IsCleanNoMap())
@@ -1223,7 +1223,7 @@
 				Game.instance.IncrementPlayerStat(PlayerStatType.ExploreSouthNoMap, m_timeSinceLastCheck);
 			}
 		}
-		if (base.transform.position.x < -10350f)
+		if (transform.position.x < -10350f)
 		{
 			Game.instance.IncrementPlayerStat(PlayerStatType.ExploreEast, m_timeSinceLastCheck);
 			if (Achievements.IsCleanNoMap())
@@ -1231,7 +1231,7 @@
 				Game.instance.IncrementPlayerStat(PlayerStatType.ExploreEastNoMap, m_timeSinceLastCheck);
 			}
 		}
-		if (base.transform.position.x > 10350f)
+		if (transform.position.x > 10350f)
 		{
 			Game.instance.IncrementPlayerStat(PlayerStatType.ExploreWest, m_timeSinceLastCheck);
 			if (Achievements.IsCleanNoMap())
@@ -1240,7 +1240,7 @@
 			}
 		}
 		m_timeSinceLastCheck = 0f;
-		m_lastDistCheck = base.transform.position;
+		m_lastDistCheck = transform.position;
 	}
 
 	private float GetBuildStamina()
@@ -1419,7 +1419,7 @@
 									{
 										rightItem.m_durability -= GetPlaceDurability(rightItem) * Game.m_durabilityRate;
 									}
-									rightItem.m_shared.m_buildEffect.Create(base.transform.position, Quaternion.identity, null, 1f, -1, GetZDOID());
+									rightItem.m_shared.m_buildEffect.Create(transform.position, Quaternion.identity, null, 1f, -1, GetZDOID());
 								}
 							}
 							else
@@ -1658,7 +1658,7 @@
 			UpdateEmote();
 			if (m_nview.IsOwner())
 			{
-				ZNet.instance.SetReferencePosition(base.transform.position);
+				ZNet.instance.SetReferencePosition(transform.position);
 				UpdatePlacementGhost(flashGuardStone: false);
 			}
 		}
@@ -1722,15 +1722,15 @@
 	{
 		if (!IsDead())
 		{
-			float num = Utils.DistanceXZ(Vector3.zero, base.transform.position);
+			float num = Utils.DistanceXZ(Vector3.zero, transform.position);
 			float num2 = 10420f;
-			if (num > num2 && (IsSwimming() || base.transform.position.y < 30f))
-			{
-				Vector3 vector = Vector3.Normalize(base.transform.position);
+			if (num > num2 && (IsSwimming() || transform.position.y < 30f))
+			{
+				Vector3 vector = Vector3.Normalize(transform.position);
 				float num3 = Utils.LerpStep(num2, 10500f, num) * 10f;
 				m_body.MovePosition(m_body.position + vector * num3 * dt);
 			}
-			if (num > num2 && base.transform.position.y < -10f)
+			if (num > num2 && transform.position.y < -10f)
 			{
 				HitData hitData = new HitData();
 				hitData.m_damage.m_damage = 99999f;
@@ -1746,7 +1746,7 @@
 		{
 			return;
 		}
-		Vector3 vector = base.transform.position + Vector3.up;
+		Vector3 vector = transform.position + Vector3.up;
 		int num = Physics.OverlapSphereNonAlloc(vector, m_autoPickupRange, m_colliders, m_autoPickupMask);
 		for (int i = 0; i < num; i++)
 		{
@@ -1939,7 +1939,7 @@
 					m_attackDrawTime = -1f;
 					return;
 				}
-				weapon.m_shared.m_holdStartEffect.Create(base.transform.position, Quaternion.identity, base.transform);
+				weapon.m_shared.m_holdStartEffect.Create(transform.position, Quaternion.identity, transform);
 			}
 			m_attackDrawTime += Time.fixedDeltaTime;
 			if (!string.IsNullOrEmpty(weapon.m_shared.m_attack.m_drawAnimationState))
@@ -1976,24 +1976,23 @@
 	private void UpdateBaseValue(float dt)
 	{
 		m_baseValueUpdateTimer += dt;
-		if (!(m_baseValueUpdateTimer > 2f))
-		{
-			return;
-		}
-		m_baseValueUpdateTimer = 0f;
-		m_baseValue = EffectArea.GetBaseValue(base.transform.position, 20f);
-		m_comfortLevel = SE_Rested.CalculateComfortLevel(this);
-		if (m_baseValueOld != m_baseValue)
-		{
-			m_baseValueOld = m_baseValue;
-			ZNet.instance.m_serverSyncedPlayerData["baseValue"] = m_baseValue.ToString();
-			m_nview.GetZDO().Set(ZDOVars.s_baseValue, m_baseValue);
-			RandEventSystem.SetRandomEventsNeedsRefresh();
+		if (m_baseValueUpdateTimer > 2f)
+		{
+			m_baseValueUpdateTimer = 0f;
+			m_baseValue = EffectArea.GetBaseValue(transform.position, 20f);
+			m_comfortLevel = SE_Rested.CalculateComfortLevel(this);
 			float stat = Game.instance.GetPlayerProfile().GetStat(PlayerStatType.MaxComfort);
 			if ((float)m_comfortLevel > stat)
 			{
 				Game.instance.GetPlayerProfile().SetStat(PlayerStatType.MaxComfort, m_comfortLevel);
 			}
+			if (m_baseValueOld != m_baseValue)
+			{
+				m_baseValueOld = m_baseValue;
+				ZNet.instance.m_serverSyncedPlayerData["baseValue"] = m_baseValue.ToString();
+				m_nview.GetZDO().Set(ZDOVars.s_baseValue, m_baseValue);
+				RandEventSystem.SetRandomEventsNeedsRefresh();
+			}
 		}
 	}
 
@@ -2032,7 +2031,7 @@
 		}
 		if (m_biomeTimer == 0f)
 		{
-			Location location = Location.GetLocation(base.transform.position, checkDungeons: false);
+			Location location = Location.GetLocation(transform.position, checkDungeons: false);
 			if ((object)location != null && !string.IsNullOrEmpty(location.m_discoverLabel))
 			{
 				AddKnownLocationName(location.m_discoverLabel);
@@ -2042,15 +2041,15 @@
 		if (m_biomeTimer > 1f)
 		{
 			m_biomeTimer = 0f;
-			BiomeSector biomeSector = WorldGenerator.instance.GetBiomeSector(base.transform.position);
-			Heightmap.Biome biome = WorldGenerator.instance.GetBiome(base.transform.position);
+			BiomeSector biomeSector = WorldGenerator.instance.GetBiomeSector(transform.position);
+			Heightmap.Biome biome = WorldGenerator.instance.GetBiome(transform.position);
 			int num = Minimap.instance.m_textureSize / 2;
 			float num2 = Minimap.instance.m_pixelSize / 2f;
-			int num3 = (int)((base.transform.position.x - num2) / Minimap.instance.m_pixelSize + (float)num);
-			int num4 = (int)((base.transform.position.y - num2) / Minimap.instance.m_pixelSize + (float)num);
+			int num3 = (int)((transform.position.x - num2) / Minimap.instance.m_pixelSize + (float)num);
+			int num4 = (int)((transform.position.y - num2) / Minimap.instance.m_pixelSize + (float)num);
 			if (biomeSector.Biome != biome)
 			{
-				ZLog.LogWarning($"GetBiome error {biomeSector.Biome} -> {biome} {base.transform.position} -> {num3}, {num4}");
+				ZLog.LogWarning($"GetBiome error {biomeSector.Biome} -> {biome} {transform.position} -> {num3}, {num4}");
 			}
 			if (m_currentBiomeData != biomeSector)
 			{
@@ -2214,21 +2213,21 @@
 		bool flag3 = InShelter();
 		HitData.DamageModifier modifier = damageModifiers.GetModifier(HitData.DamageType.Frost);
 		bool flag4 = EnvMan.IsFreezing();
-		bool num = EnvMan.IsCold();
-		bool flag5 = EnvMan.IsWet();
-		bool flag6 = IsSensed();
-		bool flag7 = m_seman.HaveStatusEffect(SEMan.s_statusEffectWet);
-		bool flag8 = IsSitting();
-		bool flag9 = EffectArea.IsPointInsideArea(base.transform.position, EffectArea.Type.WarmCozyArea, 1f);
-		bool flag10 = ShieldGenerator.IsInsideShield(base.transform.position);
-		bool flag11 = flag4 && !flag && !flag3;
-		bool flag12 = (num && !flag) || ((flag4 & flag) && !flag3) || ((flag4 && !flag) & flag3);
-		if ((modifier == HitData.DamageModifier.Resistant || modifier == HitData.DamageModifier.VeryResistant || modifier == HitData.DamageModifier.SlightlyResistant) | flag9)
-		{
-			flag11 = false;
+		bool flag5 = EnvMan.IsCold();
+		bool flag6 = EnvMan.IsWet();
+		bool flag7 = IsSensed();
+		bool flag8 = m_seman.HaveStatusEffect(SEMan.s_statusEffectWet);
+		bool flag9 = IsSitting();
+		bool flag10 = EffectArea.IsPointInsideArea(transform.position, EffectArea.Type.WarmCozyArea, 1f);
+		bool flag11 = ShieldGenerator.IsInsideShield(transform.position);
+		bool flag12 = flag4 && !flag && !flag3;
+		bool flag13 = (flag5 && !flag) || ((flag4 & flag) && !flag3) || ((flag4 && !flag) & flag3);
+		if ((modifier == HitData.DamageModifier.Resistant || modifier == HitData.DamageModifier.VeryResistant || modifier == HitData.DamageModifier.SlightlyResistant) | flag10)
+		{
 			flag12 = false;
-		}
-		if (flag5 && !m_underRoof && !flag10)
+			flag13 = false;
+		}
+		if (flag6 && !m_underRoof && !flag11)
 		{
 			m_seman.AddStatusEffect(SEMan.s_statusEffectWet, resetTime: true, 0, 0f, -1);
 		}
@@ -2248,8 +2247,8 @@
 		{
 			m_seman.RemoveStatusEffect(SEMan.s_statusEffectCampFire);
 		}
-		bool flag13 = (!flag6 && (flag8 | flag3) && !flag12 && !flag11 && (!flag7 || flag9) && !flag2) & flag;
-		if (flag13)
+		bool flag14 = (!flag7 && (flag9 | flag3) && !flag13 && !flag12 && (!flag8 || flag10) && !flag2) & flag;
+		if (flag14)
 		{
 			m_seman.AddStatusEffect(SEMan.s_statusEffectResting, resetTime: false, 0, 0f, -1);
 		}
@@ -2257,15 +2256,15 @@
 		{
 			m_seman.RemoveStatusEffect(SEMan.s_statusEffectResting);
 		}
-		m_safeInHome = (flag13 & flag3) && (float)GetBaseValue() >= 1f;
-		if (flag11)
+		m_safeInHome = (flag14 & flag3) && (float)GetBaseValue() >= 1f;
+		if (flag12)
 		{
 			if (!m_seman.RemoveStatusEffect(SEMan.s_statusEffectCold, quiet: true))
 			{
 				m_seman.AddStatusEffect(SEMan.s_statusEffectFreezing, resetTime: false, 0, 0f, -1);
 			}
 		}
-		else if (flag12)
+		else if (flag13)
 		{
 			if (!m_seman.RemoveStatusEffect(SEMan.s_statusEffectFreezing, quiet: true) && (bool)m_seman.AddStatusEffect(SEMan.s_statusEffectCold, resetTime: false, 0, 0f, -1))
 			{
@@ -2491,7 +2490,7 @@
 
 	public void OnSpawned(bool spawnValkyrie)
 	{
-		m_spawnEffects.Create(base.transform.position, Quaternion.identity);
+		m_spawnEffects.Create(transform.position, Quaternion.identity);
 		if (spawnValkyrie)
 		{
 			SetIntro(intro: true);
@@ -2510,7 +2509,7 @@
 	private void SpawnValkyrie()
 	{
 		m_valkyrie.Load();
-		UnityEngine.Object.Instantiate(m_valkyrie.Asset, base.transform.position, Quaternion.identity).GetComponent<ZNetView>().HoldReferenceTo(m_valkyrie);
+		UnityEngine.Object.Instantiate(m_valkyrie.Asset, transform.position, Quaternion.identity).GetComponent<ZNetView>().HoldReferenceTo(m_valkyrie);
 		m_valkyrie.Release();
 	}
 
@@ -2658,9 +2657,9 @@
 				hitData.m_pushForce = 10f;
 				hitData.m_hitType = HitData.HitType.Drowning;
 				Damage(hitData);
-				Vector3 position = base.transform.position;
+				Vector3 position = transform.position;
 				position.y = GetLiquidLevel();
-				m_drownEffects.Create(position, base.transform.rotation);
+				m_drownEffects.Create(position, transform.rotation);
 			}
 		}
 	}
@@ -2836,7 +2835,7 @@
 					return false;
 				}
 			}
-			else if (!CraftingStation.HaveBuildStationInRange(piece.m_craftingStation.m_name, base.transform.position) && !ZoneSystem.instance.GetGlobalKey(GlobalKeys.NoWorkbench))
+			else if (!CraftingStation.HaveBuildStationInRange(piece.m_craftingStation.m_name, transform.position) && !ZoneSystem.instance.GetGlobalKey(GlobalKeys.NoWorkbench))
 			{
 				return false;
 			}
@@ -2917,7 +2916,7 @@
 
 	private bool CheckCanRemovePiece(Piece piece)
 	{
-		if (!m_noPlacementCost && piece.m_craftingStation != null && !CraftingStation.HaveBuildStationInRange(piece.m_craftingStation.m_name, base.transform.position) && !ZoneSystem.instance.GetGlobalKey(GlobalKeys.NoWorkbench))
+		if (!m_noPlacementCost && piece.m_craftingStation != null && !CraftingStation.HaveBuildStationInRange(piece.m_craftingStation.m_name, transform.position) && !ZoneSystem.instance.GetGlobalKey(GlobalKeys.NoWorkbench))
 		{
 			Message(MessageHud.MessageType.Center, "$msg_missingstation");
 			return false;
@@ -3024,7 +3023,7 @@
 
 	public void FaceLookDirection()
 	{
-		base.transform.rotation = GetLookYaw();
+		transform.rotation = GetLookYaw();
 		Physics.SyncTransforms();
 	}
 
@@ -3234,7 +3233,7 @@
 
 	private void CreateDeathEffects()
 	{
-		GameObject[] array = m_deathEffects.Create(base.transform.position, base.transform.rotation, base.transform);
+		GameObject[] array = m_deathEffects.Create(transform.position, transform.rotation, transform);
 		for (int i = 0; i < array.Length; i++)
 		{
 			Ragdoll component = array[i].GetComponent<Ragdoll>();
@@ -3292,9 +3291,9 @@
 			{
 				UnequipAllItems();
 			}
-			GameObject obj = UnityEngine.Object.Instantiate(m_tombstone, GetCenterPoint(), base.transform.rotation);
-			obj.GetComponent<Container>().GetInventory().MoveInventoryToGrave(m_inventory);
-			TombStone component = obj.GetComponent<TombStone>();
+			GameObject gameObject = UnityEngine.Object.Instantiate(m_tombstone, GetCenterPoint(), transform.rotation);
+			gameObject.GetComponent<Container>().GetInventory().MoveInventoryToGrave(m_inventory);
+			TombStone component = gameObject.GetComponent<TombStone>();
 			PlayerProfile playerProfile = Game.instance.GetPlayerProfile();
 			component.Setup(playerProfile.GetName(), playerProfile.GetPlayerID());
 		}
@@ -3418,7 +3417,7 @@
 			ZLog.LogWarning("Not implemented death type " + m_lastHit.m_hitType);
 			break;
 		}
-		Game.instance.GetPlayerProfile().SetDeathPoint(base.transform.position);
+		Game.instance.GetPlayerProfile().SetDeathPoint(transform.position);
 		CreateDeathEffects();
 		CreateTombStone();
 		m_foods.Clear();
@@ -3439,7 +3438,7 @@
 		}
 		Message(MessageHud.MessageType.Center, "$msg_youdied");
 		ShowTutorial("death");
-		Minimap.instance.AddPin(base.transform.position, Minimap.PinType.Death, $"$hud_mapday {EnvMan.instance.GetDay(ZNet.instance.GetTimeSeconds())}", save: true, isChecked: false, 0L);
+		Minimap.instance.AddPin(transform.position, Minimap.PinType.Death, $"$hud_mapday {EnvMan.instance.GetDay(ZNet.instance.GetTimeSeconds())}", save: true, isChecked: false, 0L);
 		if (m_onDeath != null)
 		{
 			m_onDeath();
@@ -4095,7 +4094,7 @@
 		IL_077d:
 		if (num)
 		{
-			float groundHeight = ZoneSystem.instance.GetGroundHeight(base.transform.position);
+			float groundHeight = ZoneSystem.instance.GetGroundHeight(transform.position);
 			point.y = groundHeight;
 		}
 		goto IL_079f;
@@ -4189,7 +4188,7 @@
 			return false;
 		}
 		List<Character> list = new List<Character>();
-		Character.GetCharactersInRange(base.transform.position, 30f, list);
+		Character.GetCharactersInRange(transform.position, 30f, list);
 		Collider[] componentsInChildren = m_placementGhost.GetComponentsInChildren<Collider>();
 		foreach (Collider collider in componentsInChildren)
 		{
@@ -4266,7 +4265,7 @@
 		for (int i = 0; i < num; i++)
 		{
 			RaycastHit raycastHit = m_raycastHoverHits[i];
-			if ((bool)raycastHit.collider.attachedRigidbody && raycastHit.collider.attachedRigidbody.gameObject == base.gameObject)
+			if ((bool)raycastHit.collider.attachedRigidbody && raycastHit.collider.attachedRigidbody.gameObject == gameObject)
 			{
 				continue;
 			}
@@ -4339,11 +4338,11 @@
 			m_currentStation.PokeInUse();
 			if (!AlwaysRotateCamera())
 			{
-				Vector3 normalized = (m_currentStation.transform.position - base.transform.position).normalized;
+				Vector3 normalized = (m_currentStation.transform.position - transform.position).normalized;
 				normalized.y = 0f;
 				normalized.Normalize();
 				Quaternion to = Quaternion.LookRotation(normalized);
-				base.transform.rotation = Quaternion.RotateTowards(base.transform.rotation, to, m_turnSpeed * dt);
+				transform.rotation = Quaternion.RotateTowards(transform.rotation, to, m_turnSpeed * dt);
 			}
 			m_zanim.SetInt("crafting", m_currentStation.m_useAnimation);
 			m_inCraftingStation = true;
@@ -4563,7 +4562,7 @@
 			m_adrenaline = (flag ? 0f : maxAdrenaline);
 			if (flag)
 			{
-				m_adrenalinePopEffects.Create(base.transform.position, Quaternion.identity);
+				m_adrenalinePopEffects.Create(transform.position, Quaternion.identity);
 			}
 		}
 		if (m_adrenaline < 0f)
@@ -5085,7 +5084,7 @@
 	{
 		key = key.ToLower();
 		int count = m_uniques.Count;
-		m_uniques.RemoveWhere(delegate(string x)
+		m_uniques.RemoveWhere((string x) =>
 		{
 			string[] array = x.Split(' ');
 			return (array.Length >= 2 && array[0].ToLower() == key) ? true : false;
@@ -5703,11 +5702,11 @@
 		Quaternion quaternion = m_lookYaw * Quaternion.Euler(0f, mouseLook.x, 0f);
 		if (PlayerCustomizaton.IsBarberGuiVisible())
 		{
-			if (Vector3.Dot(base.transform.rotation * Vector3.forward, m_lookYaw * Vector3.forward) > 0f)
+			if (Vector3.Dot(transform.rotation * Vector3.forward, m_lookYaw * Vector3.forward) > 0f)
 			{
 				SetMouseLookBackward();
 			}
-			if (Vector3.Dot(base.transform.rotation * Vector3.forward, quaternion * Vector3.forward) < 0f)
+			if (Vector3.Dot(transform.rotation * Vector3.forward, quaternion * Vector3.forward) < 0f)
 			{
 				m_lookYaw = quaternion;
 			}
@@ -5727,7 +5726,7 @@
 
 	public void SetMouseLookForward(bool includePitch = true)
 	{
-		m_lookYaw = Quaternion.Euler(0f, base.transform.rotation.eulerAngles.y, 0f);
+		m_lookYaw = Quaternion.Euler(0f, transform.rotation.eulerAngles.y, 0f);
 		if (includePitch)
 		{
 			m_lookPitch = 0f;
@@ -5736,7 +5735,7 @@
 
 	public void SetMouseLookBackward(bool includePitch = true)
 	{
-		m_lookYaw = Quaternion.Euler(0f, base.transform.rotation.eulerAngles.y + 180f, 0f);
+		m_lookYaw = Quaternion.Euler(0f, transform.rotation.eulerAngles.y + 180f, 0f);
 		if (includePitch)
 		{
 			m_lookPitch = 0f;
@@ -5778,12 +5777,12 @@
 				ClearActionQueue();
 				m_queuedDodgeTimer = 0f;
 				m_dodgeInvincible = true;
-				base.transform.rotation = Quaternion.LookRotation(m_queuedDodgeDir);
-				m_body.rotation = base.transform.rotation;
+				transform.rotation = Quaternion.LookRotation(m_queuedDodgeDir);
+				m_body.rotation = transform.rotation;
 				m_zanim.SetTrigger("dodge");
 				AddNoise(5f);
 				UseStamina(dodgeStaminaUse);
-				m_dodgeEffects.Create(base.transform.position, Quaternion.identity, base.transform, 1f, -1, GetZDOID());
+				m_dodgeEffects.Create(transform.position, Quaternion.identity, transform, 1f, -1, GetZDOID());
 			}
 			else
 			{
@@ -5851,7 +5850,7 @@
 		if (m_nview.IsOwner() && !m_beenHitWhileDodging)
 		{
 			m_beenHitWhileDodging = true;
-			m_perfectDodgeEffects.Create(base.transform.position, Quaternion.identity, base.transform, 1f, -1, GetZDOID());
+			m_perfectDodgeEffects.Create(transform.position, Quaternion.identity, transform, 1f, -1, GetZDOID());
 			float dodgeStaminaUse = GetDodgeStaminaUse();
 			AddStamina(dodgeStaminaUse * m_perfectDodgeStaminaReturnMultiplier);
 			AddAdrenaline(m_perfectDodgeAdrenaline);
@@ -5877,7 +5876,7 @@
 		if (InPlaceMode())
 		{
 			Vector3 vector = GetLookYaw() * Vector3.forward;
-			Vector3 forward = base.transform.forward;
+			Vector3 forward = transform.forward;
 			if (Vector3.Angle(vector, forward) > 95f)
 			{
 				return true;
@@ -5906,8 +5905,8 @@
 		m_teleportTimer = 0f;
 		m_teleportCooldown = 0f;
 		InvalidateCachedLiquidDepth();
-		m_teleportFromPos = base.transform.position;
-		m_teleportFromRot = base.transform.rotation;
+		m_teleportFromPos = transform.position;
+		m_teleportFromRot = transform.rotation;
 		m_teleportTargetPos = pos;
 		m_teleportTargetRot = rot;
 		return true;
@@ -5927,10 +5926,10 @@
 			return;
 		}
 		Vector3 dir = m_teleportTargetRot * Vector3.forward;
-		base.transform.position = m_teleportTargetPos;
-		base.transform.rotation = m_teleportTargetRot;
+		transform.position = m_teleportTargetPos;
+		transform.rotation = m_teleportTargetRot;
 		m_body.linearVelocity = Vector3.zero;
-		m_maxAirAltitude = base.transform.position.y;
+		m_maxAirAltitude = transform.position.y;
 		EnvMan.instance.ForceInstantEnvironmentSwitch();
 		SetLookDir(dir);
 		if ((!(m_teleportTimer > 8f) && m_distantTeleport) || !ZNetScene.instance.IsAreaReady(m_teleportTargetPos))
@@ -5948,15 +5947,15 @@
 		{
 			if (m_distantTeleport)
 			{
-				Vector3 position = base.transform.position;
+				Vector3 position = transform.position;
 				position.y = ZoneSystem.instance.GetSolidHeight(m_teleportTargetPos) + 0.5f;
-				base.transform.position = position;
+				transform.position = position;
 			}
 			else
 			{
-				base.transform.rotation = m_teleportFromRot;
-				base.transform.position = m_teleportFromPos;
-				m_maxAirAltitude = base.transform.position.y;
+				transform.rotation = m_teleportFromRot;
+				transform.position = m_teleportFromPos;
+				m_maxAirAltitude = transform.position.y;
 				Message(MessageHud.MessageType.Center, "$msg_portal_blocked");
 			}
 			m_teleportTimer = 0f;
@@ -6216,9 +6215,9 @@
 		string text = m_nview.GetZDO().GetString(ZDOVars.s_emote);
 		if (!string.IsNullOrEmpty(text))
 		{
-			bool num2 = m_nview.GetZDO().GetBool(ZDOVars.s_emoteOneshot);
+			bool flag = m_nview.GetZDO().GetBool(ZDOVars.s_emoteOneshot);
 			m_animator.ResetTrigger("emote_stop");
-			if (num2)
+			if (flag)
 			{
 				m_animator.SetTrigger("emote_" + text);
 				return;
@@ -6348,7 +6347,7 @@
 			return false;
 		}
 		List<Player> list = new List<Player>();
-		GetPlayersInRange(base.transform.position, 10f, list);
+		GetPlayersInRange(transform.position, 10f, list);
 		foreach (Player item in list)
 		{
 			item.GetSEMan().AddStatusEffect(m_guardianSE.NameHash(), resetTime: true, 0, 0f, -1);
@@ -6408,13 +6407,13 @@
 		{
 			if (m_attachPoint != null)
 			{
-				base.transform.position = m_attachPoint.position;
-				base.transform.rotation = m_attachPoint.rotation;
+				transform.position = m_attachPoint.position;
+				transform.rotation = m_attachPoint.rotation;
 				Rigidbody componentInParent = m_attachPoint.GetComponentInParent<Rigidbody>();
 				m_body.useGravity = false;
-				m_body.linearVelocity = (componentInParent ? componentInParent.GetPointVelocity(base.transform.position) : Vector3.zero);
+				m_body.linearVelocity = (componentInParent ? componentInParent.GetPointVelocity(transform.position) : Vector3.zero);
 				m_body.angularVelocity = Vector3.zero;
-				m_maxAirAltitude = base.transform.position.y;
+				m_maxAirAltitude = transform.position.y;
 			}
 			else
 			{
@@ -6482,7 +6481,7 @@
 		}
 		if (m_attachPoint != null)
 		{
-			base.transform.position = m_attachPoint.TransformPoint(m_detachOffset);
+			transform.position = m_attachPoint.TransformPoint(m_detachOffset);
 		}
 		if (m_attachColliders != null)
 		{
@@ -6564,8 +6563,8 @@
 		forward.y = 0f;
 		forward.Normalize();
 		Quaternion to = Quaternion.LookRotation(forward);
-		base.transform.rotation = Quaternion.RotateTowards(base.transform.rotation, to, 100f * dt);
-		if (Vector3.Distance(m_doodadController.GetPosition(), base.transform.position) > m_maxInteractDistance)
+		transform.rotation = Quaternion.RotateTowards(transform.rotation, to, 100f * dt);
+		if (Vector3.Distance(m_doodadController.GetPosition(), transform.position) > m_maxInteractDistance)
 		{
 			StopDoodadControl();
 		}
@@ -6954,7 +6953,7 @@
 			m_stealthFactorTarget = 0f;
 			if (IsCrouching())
 			{
-				m_lastStealthPosition = base.transform.position;
+				m_lastStealthPosition = transform.position;
 				float skillFactor = m_skills.GetSkillFactor(Skills.SkillType.Sneak);
 				float lightFactor = StealthSystem.instance.GetLightFactor(GetCenterPoint());
 				m_stealthFactorTarget = Mathf.Lerp(0.5f + lightFactor * 0.5f, 0.2f + lightFactor * 0.4f, skillFactor);
@@ -7166,8 +7165,8 @@
 				else
 				{
 					attachJoint = "";
-					relativePos = componentInParent.transform.InverseTransformPoint(base.transform.position);
-					relativeRot = Quaternion.Inverse(componentInParent.transform.rotation) * base.transform.rotation;
+					relativePos = componentInParent.transform.InverseTransformPoint(transform.position);
+					relativeRot = Quaternion.Inverse(componentInParent.transform.rotation) * transform.rotation;
 				}
 				relativeVel = Vector3.zero;
 				return true;
@@ -7197,7 +7196,7 @@
 		if ((bool)GameCamera.instance && totalStaggerDamage > 0f)
 		{
 			float num = Mathf.Clamp01(totalStaggerDamage / GetMaxHealth());
-			GameCamera.instance.AddShake(base.transform.position, 50f, m_baseCameraShake * num, continous: false);
+			GameCamera.instance.AddShake(transform.position, 50f, m_baseCameraShake * num, continous: false);
 		}
 	}
 
@@ -7346,7 +7345,7 @@
 		m_actionAnimation = minorActionData.m_animation;
 		if (minorActionData.m_time == 0f && minorActionData.m_startEffect != null)
 		{
-			minorActionData.m_startEffect.Create(base.transform.position, Quaternion.identity);
+			minorActionData.m_startEffect.Create(transform.position, Quaternion.identity);
 		}
 		if (minorActionData.m_staminaDrain > 0f)
 		{
```

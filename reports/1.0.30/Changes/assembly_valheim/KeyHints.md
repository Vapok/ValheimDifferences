# `KeyHints.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+47/-94` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `DisableAll() [Method Body Modified]`
- `DisableAllExcept() [Method Body Modified]`
- `UpdateHints() [Method Body Modified]`
- `m_buildMenuHintsGP [Field Removed, was GameObject[]]`
- `m_buildMenuHintsKB [Field Removed, was GameObject[]]`
- `private void DisableAll()`
- `private void DisableAllExcept(GameObject selected)`

---

## 📝 Code Diff

```diff
--- a/KeyHints.cs
+++ b/KeyHints.cs
@@ -9,6 +9,8 @@
 	[Header("Key hints")]
 	public GameObject m_buildHints;
 
+	public GameObject m_buildUIHints;
+
 	public GameObject m_combatHints;
 
 	public GameObject m_inventoryHints;
@@ -30,10 +32,6 @@
 	public GameObject m_secondaryAttackGP;
 
 	public GameObject m_secondaryAttackKB;
-
-	public GameObject[] m_buildMenuHintsKB;
-
-	public GameObject[] m_buildMenuHintsGP;
 
 	public GameObject m_bowDrawGP;
 
@@ -162,17 +160,9 @@
 		Player localPlayer = Player.m_localPlayer;
 		if (!m_keyHintsEnabled || localPlayer == null || localPlayer.IsDead() || Chat.instance.IsChatDialogWindowVisible() || Game.IsPaused() || (InventoryGui.instance != null && (InventoryGui.instance.IsSkillsPanelOpen || InventoryGui.instance.IsTrophisPanelOpen || InventoryGui.instance.IsAchievementsPanelOpen || InventoryGui.instance.IsTextPanelOpen)))
 		{
-			m_buildHints.SetActive(value: false);
-			m_combatHints.SetActive(value: false);
-			m_inventoryHints.SetActive(value: false);
-			m_inventoryWithContainerHints.SetActive(value: false);
-			m_fishingHints.SetActive(value: false);
-			m_barberHints.SetActive(value: false);
-			m_radialHints.SetActive(value: false);
+			DisableAll();
 			return;
 		}
-		_ = m_buildHints.activeSelf;
-		_ = m_buildHints.activeSelf;
 		ItemDrop.ItemData currentWeapon = localPlayer.GetCurrentWeapon();
 		if (InventoryGui.IsVisible())
 		{
@@ -181,103 +171,44 @@
 			ItemDrop.ItemData itemData = (flag2 ? InventoryGui.instance.ContainerGrid.GetGamepadSelectedItem() : InventoryGui.instance.m_playerGrid.GetGamepadSelectedItem());
 			bool flag3 = itemData?.IsEquipable() ?? false;
 			bool flag4 = itemData != null && itemData.m_shared.m_itemType == ItemDrop.ItemData.ItemType.Consumable;
-			m_buildHints.SetActive(value: false);
-			m_combatHints.SetActive(value: false);
-			m_inventoryHints.SetActive(!flag);
-			m_inventoryWithContainerHints.SetActive(flag);
+			DisableAllExcept(flag ? m_inventoryWithContainerHints : m_inventoryHints);
 			for (int i = 0; i < m_equipButtons.Length; i++)
 			{
 				m_equipButtons[i].SetActive(flag4 || (flag3 && !flag2));
 			}
-			m_fishingHints.SetActive(value: false);
-			m_barberHints.SetActive(value: false);
-			m_radialHints.SetActive(value: false);
 		}
 		else if (Hud.instance.m_radialMenu.Active)
 		{
-			m_buildHints.SetActive(value: false);
-			m_combatHints.SetActive(value: false);
-			m_inventoryHints.SetActive(value: false);
-			m_inventoryWithContainerHints.SetActive(value: false);
-			m_fishingHints.SetActive(value: false);
-			m_barberHints.SetActive(value: false);
-			m_radialHints.SetActive(value: true);
+			DisableAllExcept(m_radialHints);
 		}
 		else if (localPlayer.InPlaceMode())
 		{
-			if (ZInput.IsNonClassicFunctionality())
-			{
-				string text = Localization.instance.Localize("$hud_altplacement <mspace=0.6em> $KEY_AltKeys + $KEY_AltPlace ");
-				string text2 = (localPlayer.AlternativePlacementActive ? Localization.instance.Localize("$hud_off") : Localization.instance.Localize("$hud_on"));
-				m_buildAlternativePlacingKey.text = text + " " + text2 + "</mspace>";
-			}
 			if (Hud.IsPieceSelectionVisible())
 			{
-				GameObject[] array = (ZInput.IsGamepadActive() ? m_buildMenuHintsGP : m_buildMenuHintsKB);
-				for (int j = 0; j < array.Length; j++)
+				DisableAllExcept(m_buildUIHints);
+			}
+			else
+			{
+				if (ZInput.IsNonClassicFunctionality())
 				{
-					array[j].SetActive(value: true);
+					string text = Localization.instance.Localize("$hud_altplacement <mspace=0.6em> $KEY_AltKeys + $KEY_AltPlace ");
+					string text2 = (localPlayer.AlternativePlacementActive ? Localization.instance.Localize("$hud_off") : Localization.instance.Localize("$hud_on"));
+					m_buildAlternativePlacingKey.text = text + " " + text2 + "</mspace>";
 				}
-			}
-			else
-			{
-				GameObject[] array = m_buildMenuHintsGP;
-				for (int j = 0; j < array.Length; j++)
-				{
-					array[j].SetActive(value: false);
-				}
-				array = m_buildMenuHintsKB;
-				for (int j = 0; j < array.Length; j++)
-				{
-					array[j].SetActive(value: false);
-				}
-			}
-			m_buildHints.SetActive(value: true);
-			m_combatHints.SetActive(value: false);
-			m_inventoryHints.SetActive(value: false);
-			m_inventoryWithContainerHints.SetActive(value: false);
-			m_fishingHints.SetActive(value: false);
-			m_barberHints.SetActive(value: false);
-			m_radialHints.SetActive(value: false);
+				DisableAllExcept(m_buildHints);
+			}
 		}
 		else if (PlayerCustomizaton.IsBarberGuiVisible())
 		{
-			m_buildHints.SetActive(value: false);
-			m_combatHints.SetActive(value: false);
-			m_inventoryHints.SetActive(value: false);
-			m_inventoryWithContainerHints.SetActive(value: false);
-			m_fishingHints.SetActive(value: false);
-			m_barberHints.SetActive(value: true);
-			m_radialHints.SetActive(value: false);
-		}
-		else if (localPlayer.GetDoodadController() != null)
-		{
-			m_buildHints.SetActive(value: false);
-			m_combatHints.SetActive(value: false);
-			m_inventoryHints.SetActive(value: false);
-			m_inventoryWithContainerHints.SetActive(value: false);
-			m_fishingHints.SetActive(value: false);
-			m_barberHints.SetActive(value: false);
-			m_radialHints.SetActive(value: false);
+			DisableAllExcept(m_barberHints);
 		}
 		else if (currentWeapon != null && currentWeapon.m_shared.m_animationState == ItemDrop.ItemData.AnimationState.FishingRod)
 		{
-			m_buildHints.SetActive(value: false);
-			m_combatHints.SetActive(value: false);
-			m_inventoryHints.SetActive(value: false);
-			m_inventoryWithContainerHints.SetActive(value: false);
-			m_fishingHints.SetActive(value: true);
-			m_radialHints.SetActive(value: false);
+			DisableAllExcept(m_fishingHints);
 		}
 		else if (currentWeapon != null && (currentWeapon != localPlayer.m_unarmedWeapon.m_itemData || localPlayer.IsTargeted()))
 		{
-			m_buildHints.SetActive(value: false);
-			m_combatHints.SetActive(value: true);
-			m_inventoryHints.SetActive(value: false);
-			m_inventoryWithContainerHints.SetActive(value: false);
-			m_fishingHints.SetActive(value: false);
-			m_barberHints.SetActive(value: false);
-			m_radialHints.SetActive(value: false);
+			DisableAllExcept(m_combatHints);
 			bool flag5 = currentWeapon.m_shared.m_itemType == ItemDrop.ItemData.ItemType.Bow && currentWeapon.m_shared.m_skillType != Skills.SkillType.Crossbows;
 			bool active = !flag5 && currentWeapon.HavePrimaryAttack();
 			bool active2 = !flag5 && currentWeapon.HaveSecondaryAttack();
@@ -290,17 +221,39 @@
 		}
 		else
 		{
-			m_buildHints.SetActive(value: false);
-			m_combatHints.SetActive(value: false);
-			m_inventoryHints.SetActive(value: false);
-			m_inventoryWithContainerHints.SetActive(value: false);
-			m_fishingHints.SetActive(value: false);
-			m_barberHints.SetActive(value: false);
-			m_radialHints.SetActive(value: false);
+			DisableAll();
 		}
 		if (m_radialKeyHints.isActiveAndEnabled)
 		{
 			m_radialKeyHints.UpdateRadialHints(Hud.instance.m_radialMenu);
 		}
 	}
+
+	private void DisableAll()
+	{
+		DisableAllExcept(null);
+	}
+
+	private void DisableAllExcept(GameObject selected)
+	{
+		DisableIfNotSelected(m_buildHints);
+		DisableIfNotSelected(m_buildUIHints);
+		DisableIfNotSelected(m_combatHints);
+		DisableIfNotSelected(m_inventoryHints);
+		DisableIfNotSelected(m_inventoryWithContainerHints);
+		DisableIfNotSelected(m_fishingHints);
+		DisableIfNotSelected(m_barberHints);
+		DisableIfNotSelected(m_radialHints);
+		if (selected != null)
+		{
+			selected.SetActive(value: true);
+		}
+		void DisableIfNotSelected(GameObject current)
+		{
+			if (current != selected)
+			{
+				current.SetActive(value: false);
+			}
+		}
+	}
 }
```

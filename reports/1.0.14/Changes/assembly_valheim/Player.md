# `Player.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+58/-54` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Player.cs
+++ b/Player.cs
@@ -455,6 +455,8 @@
 
 	private Dictionary<Material, float> m_ghostRippleDistance = new Dictionary<Material, float>();
 
+	private bool m_toggleBlock;
+
 	private bool m_attackTowardsPlayerLookDir;
 
 	public float m_blockReload;
@@ -621,6 +623,18 @@
 		set
 		{
 			m_attackTowardsPlayerLookDir = value;
+		}
+	}
+
+	public bool ToggleBlock
+	{
+		get
+		{
+			return m_toggleBlock;
+		}
+		set
+		{
+			m_toggleBlock = value;
 		}
 	}
 
@@ -687,6 +701,7 @@
 		AddQueuedKeys();
 		UpdateCurrentSeason();
 		m_attackTowardsPlayerLookDir = PlatformPrefs.GetInt("AttackTowardsPlayerLookDir", 1) == 1;
+		m_toggleBlock = PlayerPrefs.GetInt("ToggleBlock", 0) == 1;
 	}
 
 	protected override void OnEnable()
@@ -903,29 +918,29 @@
 			{
 				if (ZInput.GetButtonDown("Hide"))
 				{
-					goto IL_031d;
+					goto IL_0320;
 				}
 				if (flag3 && !ZInput.GetButton("JoyAltKeys"))
 				{
 					num = !InPlaceMode();
-					goto IL_031b;
+					goto IL_031e;
 				}
 			}
 			else if (!InPlaceMode() & flag3)
 			{
-				num = ZInput.GetButton("JoyAltKeys");
-				goto IL_031b;
-			}
-			goto IL_0368;
-		}
-		goto IL_052b;
-		IL_031b:
+				num = !ZInput.GetButton("JoyAltKeys");
+				goto IL_031e;
+			}
+			goto IL_036b;
+		}
+		goto IL_04de;
+		IL_031e:
 		if (num)
 		{
-			goto IL_031d;
-		}
-		goto IL_0368;
-		IL_052b:
+			goto IL_0320;
+		}
+		goto IL_036b;
+		IL_04de:
 		UpdateControllerTriggerFeedback(flag2);
 		UpdateGyro(flag2);
 		if (m_blockReload > 0f)
@@ -943,7 +958,7 @@
 		UpdatePlacement(flag2, Time.deltaTime);
 		UpdateStats();
 		return;
-		IL_031d:
+		IL_0320:
 		if (GetRightItem() != null || GetLeftItem() != null)
 		{
 			if (!InAttack() && !InDodge())
@@ -955,8 +970,8 @@
 		{
 			ShowHandItems();
 		}
-		goto IL_0368;
-		IL_0368:
+		goto IL_036b;
+		IL_036b:
 		if (ZInput.GetButtonDown("ToggleWalk") && !Hud.InRadial())
 		{
 			SetWalk(!GetWalk());
@@ -983,39 +998,14 @@
 			m_enableAutoPickup = !m_enableAutoPickup;
 			Message(MessageHud.MessageType.TopLeft, "$hud_autopickup:" + (m_enableAutoPickup ? "$hud_on" : "$hud_off"));
 		}
-		if (ZInput.GetButtonDown("Hotbar1"))
-		{
-			UseHotbarItem(1);
-		}
-		if (ZInput.GetButtonDown("Hotbar2"))
-		{
-			UseHotbarItem(2);
-		}
-		if (ZInput.GetButtonDown("Hotbar3"))
-		{
-			UseHotbarItem(3);
-		}
-		if (ZInput.GetButtonDown("Hotbar4"))
-		{
-			UseHotbarItem(4);
-		}
-		if (ZInput.GetButtonDown("Hotbar5"))
-		{
-			UseHotbarItem(5);
-		}
-		if (ZInput.GetButtonDown("Hotbar6"))
-		{
-			UseHotbarItem(6);
-		}
-		if (ZInput.GetButtonDown("Hotbar7"))
-		{
-			UseHotbarItem(7);
-		}
-		if (ZInput.GetButtonDown("Hotbar8"))
-		{
-			UseHotbarItem(8);
-		}
-		goto IL_052b;
+		for (int i = 1; i <= 8; i++)
+		{
+			if (ZInput.GetButtonDown($"Hotbar{i}") || ZInput.GetButtonDown($"Hotbar{i}Alt"))
+			{
+				UseHotbarItem(i);
+			}
+		}
+		goto IL_04de;
 	}
 
 	private void UpdateControllerTriggerFeedback(bool takeInput)
@@ -6646,6 +6636,7 @@
 			lookDir.Normalize();
 			m_moveDir = movedir.z * lookDir + movedir.x * Vector3.Cross(Vector3.up, lookDir);
 		}
+		bool flag = false;
 		if ((!m_autoRun & autoRun) && !InPlaceMode())
 		{
 			m_autoRun = true;
@@ -6665,23 +6656,36 @@
 				m_moveDir = m_lookDir;
 				m_moveDir.y = 0f;
 				m_moveDir.Normalize();
-				blockHold = false;
-				block = false;
+				flag = true;
 			}
 		}
 		m_attack = attack;
 		m_attackHold = attackHold;
 		m_secondaryAttack = secondaryAttack;
 		m_secondaryAttackHold = secondaryAttackHold;
-		m_blocking = blockHold;
 		m_run = run;
+		if (m_toggleBlock)
+		{
+			if (block)
+			{
+				m_blocking = !m_blocking;
+			}
+		}
+		else
+		{
+			m_blocking = blockHold;
+		}
+		if (flag)
+		{
+			m_blocking = false;
+		}
 		if (crouch)
 		{
 			SetCrouch(!m_crouchToggled);
 		}
 		if (ZInput.InputLayout == InputLayout.Default || !ZInput.IsGamepadActive())
 		{
-			if (!jump)
+			if (!(jump | dodge))
 			{
 				return;
 			}
@@ -6696,7 +6700,7 @@
 				}
 				Dodge(dodgeDir);
 			}
-			else if (IsCrouching() || m_crouchToggled)
+			else if ((IsCrouching() || m_crouchToggled) | dodge)
 			{
 				Vector3 dodgeDir2 = m_moveDir;
 				if (dodgeDir2.magnitude < 0.1f)
```

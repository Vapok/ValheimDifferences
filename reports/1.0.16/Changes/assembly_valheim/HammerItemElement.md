# `Valheim.UI/HammerItemElement.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+16/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/HammerItemElement.cs
+++ b/Valheim.UI/HammerItemElement.cs
@@ -24,11 +24,21 @@
 		if (list.Count > 0)
 		{
 			m_hammerRef = list.FirstOrDefault((ItemDrop.ItemData i) => i.m_equipped) ?? list[0];
-			base.Icon.sprite = m_hammerIcon;
+			Icon.sprite = m_hammerIcon;
 			SetInteraction();
-			base.CloseOnInteract = () => true;
-			base.Activated = ((!m_hammerRef.m_equipped) ? 0f : ((localPlayer.GetActionQueueCount() > 0) ? 0f : 1f));
-			base.Name = Localization.instance.Localize("$radial_hammer");
+			CloseOnInteract = () => true;
+			HammerItemElement hammerItemElement = this;
+			float activated;
+			if (m_hammerRef.m_equipped)
+			{
+				activated = ((localPlayer.GetActionQueueCount() > 0) ? 0f : 1f);
+			}
+			else
+			{
+				activated = 0f;
+			}
+			hammerItemElement.Activated = activated;
+			Name = Localization.instance.Localize("$radial_hammer");
 		}
 	}
 
@@ -43,7 +53,7 @@
 
 	private void SetInteraction()
 	{
-		base.Interact = delegate
+		Interact = () =>
 		{
 			if ((bool)Player.m_localPlayer)
 			{
@@ -76,7 +86,7 @@
 					}
 				}
 			}
-			base.Activated = (m_hammerRef.m_equipped ? 1f : 0f);
+			Activated = (m_hammerRef.m_equipped ? 1f : 0f);
 			return true;
 		};
 	}
```

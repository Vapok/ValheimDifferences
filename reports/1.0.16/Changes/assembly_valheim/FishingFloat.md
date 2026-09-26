# `FishingFloat.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/FishingFloat.cs
+++ b/FishingFloat.cs
@@ -93,7 +93,7 @@
 			return;
 		}
 		m_rodLine.SetPeer(owner.GetZDOID());
-		m_lineLength = Vector3.Distance(rodTop.position, base.transform.position);
+		m_lineLength = Vector3.Distance(rodTop.position, transform.position);
 		owner.Message(MessageHud.MessageType.Center, m_lineLength.ToString("0m"));
 	}
 
@@ -163,7 +163,7 @@
 			m_nview.Destroy();
 			return;
 		}
-		float magnitude = (rodTop.transform.position - base.transform.position).magnitude;
+		float magnitude = (rodTop.transform.position - transform.position).magnitude;
 		ItemDrop itemDrop = (fish ? fish.gameObject.GetComponent<ItemDrop>() : null);
 		if (!owner.HaveStamina() && fish != null)
 		{
@@ -239,7 +239,7 @@
 				fish.OnHooked(null);
 			}
 			m_nview.Destroy();
-			m_lineBreakEffect.Create(base.transform.position, Quaternion.identity);
+			m_lineBreakEffect.Create(transform.position, Quaternion.identity);
 		}
 		else
 		{
@@ -378,7 +378,7 @@
 		}
 		if (correctBait)
 		{
-			m_nibbleEffect.Create(base.transform.position, Quaternion.identity, base.transform);
+			m_nibbleEffect.Create(transform.position, Quaternion.identity, transform);
 			m_body.AddForce(Vector3.down * m_nibbleForce, ForceMode.VelocityChange);
 			GameObject gameObject = ZNetScene.instance.FindInstance(fishID);
 			if ((bool)gameObject)
```

# `Bed.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Bed.cs
+++ b/Bed.cs
@@ -94,7 +94,7 @@
 				{
 					return false;
 				}
-				human.AttachStart(m_spawnPoint, base.gameObject, hideWeapons: true, isBed: true, onShip: false, "attach_bed", new Vector3(0f, 0.5f, 0f));
+				human.AttachStart(m_spawnPoint, gameObject, hideWeapons: true, isBed: true, onShip: false, "attach_bed", new Vector3(0f, 0.5f, 0f));
 				return false;
 			}
 			ZLog.Log("Not current spawn point");
@@ -147,7 +147,7 @@
 
 	private bool CheckFire(Player human)
 	{
-		if (!EffectArea.IsPointInsideArea(base.transform.position, EffectArea.Type.Heat))
+		if (!EffectArea.IsPointInsideArea(transform.position, EffectArea.Type.Heat))
 		{
 			human.Message(MessageHud.MessageType.Center, "$msg_bednofire");
 			return false;
```

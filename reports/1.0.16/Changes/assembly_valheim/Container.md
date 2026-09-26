# `Container.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+11/-11` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Container.cs
+++ b/Container.cs
@@ -115,7 +115,7 @@
 	{
 		while (m_inventory.NrOfItems() > 0)
 		{
-			Vector3 position = base.transform.position + UnityEngine.Random.insideUnitSphere * 1f;
+			Vector3 position = transform.position + UnityEngine.Random.insideUnitSphere * 1f;
 			UnityEngine.Object.Instantiate(lootContainerPrefab, position, UnityEngine.Random.rotation).GetComponent<Container>().GetInventory()
 				.MoveAll(m_inventory);
 		}
@@ -127,7 +127,7 @@
 		int num = 1;
 		foreach (ItemDrop.ItemData item in allItems)
 		{
-			Vector3 position = base.transform.position + Vector3.up * 0.5f + UnityEngine.Random.insideUnitSphere * 0.3f;
+			Vector3 position = transform.position + Vector3.up * 0.5f + UnityEngine.Random.insideUnitSphere * 0.3f;
 			Quaternion rotation = Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f);
 			ItemDrop.DropItem(item, 0, position, rotation);
 			num++;
@@ -201,7 +201,7 @@
 
 	public string GetHoverText()
 	{
-		if (m_checkGuardStone && !PrivateArea.CheckAccess(base.transform.position, 0f, flash: false))
+		if (m_checkGuardStone && !PrivateArea.CheckAccess(transform.position, 0f, flash: false))
 		{
 			return Localization.instance.Localize(m_name + "\n$piece_noaccess");
 		}
@@ -221,7 +221,7 @@
 		{
 			return false;
 		}
-		if (m_checkGuardStone && !PrivateArea.CheckAccess(base.transform.position))
+		if (m_checkGuardStone && !PrivateArea.CheckAccess(transform.position))
 		{
 			return true;
 		}
@@ -293,11 +293,11 @@
 			ZDOID gamepadEffectsExclusiveToPlayer = (IsOwner() ? Player.m_localPlayer.GetZDOID() : ZDOID.None);
 			if (inUse)
 			{
-				m_openEffects.Create(base.transform.position, base.transform.rotation, null, 1f, -1, gamepadEffectsExclusiveToPlayer);
+				m_openEffects.Create(transform.position, transform.rotation, null, 1f, -1, gamepadEffectsExclusiveToPlayer);
 			}
 			else
 			{
-				m_closeEffects.Create(base.transform.position, base.transform.rotation, null, 1f, -1, gamepadEffectsExclusiveToPlayer);
+				m_closeEffects.Create(transform.position, transform.rotation, null, 1f, -1, gamepadEffectsExclusiveToPlayer);
 			}
 		}
 	}
@@ -309,7 +309,7 @@
 
 	private void RPC_RequestOpen(long uid, long playerID)
 	{
-		ZLog.Log($"Player {uid} wants to open {base.gameObject.name}   im: {ZDOMan.GetSessionID()}");
+		ZLog.Log($"Player {uid} wants to open {gameObject.name}   im: {ZDOMan.GetSessionID()}");
 		if (!m_nview.IsOwner())
 		{
 			ZLog.Log("  but im not the owner");
@@ -355,7 +355,7 @@
 
 	private void RPC_RequestStack(long uid, long playerID)
 	{
-		ZLog.Log("Player " + uid + " wants to stack all in " + base.gameObject.name + "   im: " + ZDOMan.GetSessionID());
+		ZLog.Log("Player " + uid + " wants to stack all in " + gameObject.name + "   im: " + ZDOMan.GetSessionID());
 		if (!m_nview.IsOwner())
 		{
 			ZLog.Log("  but im not the owner");
@@ -388,7 +388,7 @@
 		{
 			if (m_inventory.StackAll(Player.m_localPlayer.GetInventory(), message: true) > 0)
 			{
-				InventoryGui.instance.m_moveItemEffects.Create(base.transform.position, Quaternion.identity);
+				InventoryGui.instance.m_moveItemEffects.Create(transform.position, Quaternion.identity);
 			}
 		}
 		else
@@ -399,7 +399,7 @@
 
 	public bool TakeAll(Humanoid character)
 	{
-		if (m_checkGuardStone && !PrivateArea.CheckAccess(base.transform.position))
+		if (m_checkGuardStone && !PrivateArea.CheckAccess(transform.position))
 		{
 			return false;
 		}
@@ -415,7 +415,7 @@
 
 	private void RPC_RequestTakeAll(long uid, long playerID)
 	{
-		ZLog.Log($"Player {uid} wants to takeall from {base.gameObject.name}   im: {ZDOMan.GetSessionID()}");
+		ZLog.Log($"Player {uid} wants to takeall from {gameObject.name}   im: {ZDOMan.GetSessionID()}");
 		if (!m_nview.IsOwner())
 		{
 			ZLog.Log("  but im not the owner");
```

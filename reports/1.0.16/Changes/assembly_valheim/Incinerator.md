# `Incinerator.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Incinerator.cs
+++ b/Incinerator.cs
@@ -131,7 +131,7 @@
 
 	public string GetLeverHoverText()
 	{
-		if (!PrivateArea.CheckAccess(base.transform.position))
+		if (!PrivateArea.CheckAccess(transform.position))
 		{
 			return Localization.instance.Localize("$piece_incinerator\n$piece_noaccess");
 		}
@@ -144,7 +144,7 @@
 		{
 			return false;
 		}
-		if (!PrivateArea.CheckAccess(base.transform.position))
+		if (!PrivateArea.CheckAccess(transform.position))
 		{
 			return false;
 		}
@@ -155,7 +155,7 @@
 
 	private void RPC_RequestIncinerate(long uid, long playerID)
 	{
-		ZLog.Log("Player " + uid + " wants to incinerate " + base.gameObject.name + "   im: " + ZDOMan.GetSessionID());
+		ZLog.Log("Player " + uid + " wants to incinerate " + gameObject.name + "   im: " + ZDOMan.GetSessionID());
 		if (!m_nview.IsOwner())
 		{
 			ZLog.Log("  but im not the owner");
@@ -180,7 +180,7 @@
 	{
 		isInUse = true;
 		m_nview.InvokeRPC(ZNetView.Everybody, "RPC_AnimateLever");
-		m_leverEffects.Create(base.transform.position, base.transform.rotation);
+		m_leverEffects.Create(transform.position, transform.rotation);
 		yield return new WaitForSeconds(UnityEngine.Random.Range(m_effectDelayMin, m_effectDelayMax));
 		m_nview.InvokeRPC(ZNetView.Everybody, "RPC_AnimateLeverReturn");
 		if (!m_nview.IsValid() || !m_nview.IsOwner() || m_container.IsInUse())
@@ -189,7 +189,7 @@
 			yield break;
 		}
 		Invoke("StopAOE", 4f);
-		UnityEngine.Object.Instantiate(m_lightingAOEs, base.transform.position, base.transform.rotation);
+		UnityEngine.Object.Instantiate(m_lightingAOEs, transform.position, transform.rotation);
 		Inventory inventory = m_container.GetInventory();
 		List<ItemDrop> list = new List<ItemDrop>();
 		int num = 0;
```

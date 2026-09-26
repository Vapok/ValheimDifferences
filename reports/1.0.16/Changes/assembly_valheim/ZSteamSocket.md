# `ZSteamSocket.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZSteamSocket.cs
+++ b/ZSteamSocket.cs
@@ -350,8 +350,8 @@
 		{
 			num += item.Length;
 		}
-		SteamNetConnectionRealTimeStatus_t pStatus = default(SteamNetConnectionRealTimeStatus_t);
-		SteamNetConnectionRealTimeLaneStatus_t pLanes = default(SteamNetConnectionRealTimeLaneStatus_t);
+		SteamNetConnectionRealTimeStatus_t pStatus = default;
+		SteamNetConnectionRealTimeLaneStatus_t pLanes = default;
 		if (SteamNetworkingSockets.GetConnectionRealTimeStatus(m_con, ref pStatus, 0, ref pLanes) == EResult.k_EResultOK)
 		{
 			num += pStatus.m_cbPendingReliable + pStatus.m_cbPendingUnreliable + pStatus.m_cbSentUnackedReliable;
@@ -361,8 +361,8 @@
 
 	public int GetCurrentSendRate()
 	{
-		SteamNetConnectionRealTimeStatus_t pStatus = default(SteamNetConnectionRealTimeStatus_t);
-		SteamNetConnectionRealTimeLaneStatus_t pLanes = default(SteamNetConnectionRealTimeLaneStatus_t);
+		SteamNetConnectionRealTimeStatus_t pStatus = default;
+		SteamNetConnectionRealTimeLaneStatus_t pLanes = default;
 		if (SteamNetworkingSockets.GetConnectionRealTimeStatus(m_con, ref pStatus, 0, ref pLanes) != EResult.k_EResultOK)
 		{
 			return 0;
@@ -377,8 +377,8 @@
 
 	public void GetConnectionQuality(out float localQuality, out float remoteQuality, out int ping, out float outByteSec, out float inByteSec)
 	{
-		SteamNetConnectionRealTimeStatus_t pStatus = default(SteamNetConnectionRealTimeStatus_t);
-		SteamNetConnectionRealTimeLaneStatus_t pLanes = default(SteamNetConnectionRealTimeLaneStatus_t);
+		SteamNetConnectionRealTimeStatus_t pStatus = default;
+		SteamNetConnectionRealTimeLaneStatus_t pLanes = default;
 		if (SteamNetworkingSockets.GetConnectionRealTimeStatus(m_con, ref pStatus, 0, ref pLanes) == EResult.k_EResultOK)
 		{
 			localQuality = pStatus.m_flConnectionQualityLocal;
```

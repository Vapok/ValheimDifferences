# `ZDOMan.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `PeerZDOInfo() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/ZDOMan.cs
+++ b/ZDOMan.cs
@@ -7,7 +7,7 @@
 
 public class ZDOMan
 {
-	private class ZDOPeer
+	public class ZDOPeer
 	{
 		public struct PeerZDOInfo(uint dataRevision, ushort ownerRevision, float syncTime)
 		{
```

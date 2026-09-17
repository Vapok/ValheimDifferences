# `Leviathan.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Leviathan.cs
+++ b/Leviathan.cs
@@ -48,10 +48,10 @@
 			MineRock mineRock = m_mineRock;
 			mineRock.m_onHit = (Action)Delegate.Combine(mineRock.m_onHit, new Action(OnHit));
 		}
-		if (m_nview.IsValid() && m_nview.IsOwner())
+		if (m_nview.IsValid())
 		{
 			m_nview.Register("RPC_Left", RPC_Left);
-			if (m_nview.GetZDO().GetBool(ZDOVars.s_dead))
+			if (m_nview.GetZDO().GetBool(ZDOVars.s_dead) && m_nview.IsOwner())
 			{
 				m_nview.Destroy();
 			}
```

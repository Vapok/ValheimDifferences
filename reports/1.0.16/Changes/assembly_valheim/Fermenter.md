# `Fermenter.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Fermenter.cs
+++ b/Fermenter.cs
@@ -129,7 +129,7 @@
 
 	private void drop(ItemDrop item)
 	{
-		Vector3 position = base.transform.position + Vector3.up + UnityEngine.Random.insideUnitSphere * 0.3f;
+		Vector3 position = transform.position + Vector3.up + UnityEngine.Random.insideUnitSphere * 0.3f;
 		Quaternion rotation = Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f);
 		ItemDrop.OnCreateNew(UnityEngine.Object.Instantiate(item.gameObject, position, rotation));
 	}
@@ -146,7 +146,7 @@
 
 	public string GetHoverText()
 	{
-		if (!PrivateArea.CheckAccess(base.transform.position, 0f, flash: false))
+		if (!PrivateArea.CheckAccess(transform.position, 0f, flash: false))
 		{
 			return Localization.instance.Localize(m_name + "\n$piece_noaccess");
 		}
@@ -195,7 +195,7 @@
 			return false;
 		}
 		UpdateCover(0f, forceUpdate: true);
-		if (!PrivateArea.CheckAccess(base.transform.position))
+		if (!PrivateArea.CheckAccess(transform.position))
 		{
 			return true;
 		}
@@ -232,7 +232,7 @@
 
 	public bool UseItem(Humanoid user, ItemDrop.ItemData item)
 	{
-		if (!PrivateArea.CheckAccess(base.transform.position))
+		if (!PrivateArea.CheckAccess(transform.position))
 		{
 			return false;
 		}
@@ -304,7 +304,7 @@
 				ZLog.DevLog("Item not allowed");
 				return;
 			}
-			m_addedEffects.Create(base.transform.position, base.transform.rotation);
+			m_addedEffects.Create(transform.position, transform.rotation);
 			m_nview.GetZDO().Set(ZDOVars.s_content, nameHash);
 			m_nview.GetZDO().Set(ZDOVars.s_startTime, ZNet.instance.GetTime().Ticks);
 			m_nview.GetZDO().Set(ZDOVars.s_cheatedQueued, cheated);
@@ -318,7 +318,7 @@
 			m_delayedTapItem = GetContent();
 			m_delayedTapItemCheated = m_nview.GetZDO().GetBool(ZDOVars.s_cheatedQueued);
 			Invoke("DelayedTap", m_tapDelay);
-			m_tapEffects.Create(base.transform.position, base.transform.rotation);
+			m_tapEffects.Create(transform.position, transform.rotation);
 			m_nview.GetZDO().Set(ZDOVars.s_content, 0);
 			m_nview.GetZDO().Set(ZDOVars.s_startTime, 0);
 			m_nview.GetZDO().Set(ZDOVars.s_cheatedQueued, value: false);
```

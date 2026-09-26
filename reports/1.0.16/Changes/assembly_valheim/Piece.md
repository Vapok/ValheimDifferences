# `Piece.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+12/-12` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Piece.cs
+++ b/Piece.cs
@@ -294,7 +294,7 @@
 		}
 		float skillFactor = Player.m_localPlayer.GetSkillFactor(Skills.SkillType.Farming);
 		float radius = Mathf.Lerp(m_harvestRadius, m_harvestRadiusMaxLevel, skillFactor);
-		int num = Physics.OverlapSphereNonAlloc(base.transform.position, radius, s_pieceColliders, s_harvestRayMask);
+		int num = Physics.OverlapSphereNonAlloc(transform.position, radius, s_pieceColliders, s_harvestRayMask);
 		for (int i = 0; i < num; i++)
 		{
 			Pickable component = s_pieceColliders[i].gameObject.GetComponent<Pickable>();
@@ -303,7 +303,7 @@
 				component.Interact(Player.m_localPlayer, repeat: false, alt: false);
 			}
 		}
-		ZNetScene.instance.Destroy(base.gameObject);
+		ZNetScene.instance.Destroy(gameObject);
 	}
 
 	private void OnDestroy()
@@ -343,7 +343,7 @@
 			return;
 		}
 		Container container = null;
-		Feast component = base.gameObject.GetComponent<Feast>();
+		Feast component = gameObject.GetComponent<Feast>();
 		Requirement[] resources = m_resources;
 		foreach (Requirement requirement in resources)
 		{
@@ -376,7 +376,7 @@
 					dropCount -= itemData.m_stack;
 					if (container == null || !container.GetInventory().HaveEmptySlot())
 					{
-						container = UnityEngine.Object.Instantiate(m_destroyedLootPrefab, base.transform.position + Vector3.up * m_returnResourceHeightOffset, Quaternion.identity).GetComponent<Container>();
+						container = UnityEngine.Object.Instantiate(m_destroyedLootPrefab, transform.position + Vector3.up * m_returnResourceHeightOffset, Quaternion.identity).GetComponent<Container>();
 					}
 					if (m_nview.GetZDO().GetBool(ZDOVars.s_cheated) && !PlayerProfile.s_bypassCheatChecks)
 					{
@@ -388,7 +388,7 @@
 			}
 			while (dropCount > 0)
 			{
-				ItemDrop component2 = UnityEngine.Object.Instantiate(itemPrefab, base.transform.position + Vector3.up * m_returnResourceHeightOffset, Quaternion.identity).GetComponent<ItemDrop>();
+				ItemDrop component2 = UnityEngine.Object.Instantiate(itemPrefab, transform.position + Vector3.up * m_returnResourceHeightOffset, Quaternion.identity).GetComponent<ItemDrop>();
 				component2.SetStack(Mathf.Min(dropCount, component2.m_itemData.m_shared.m_maxStackSize));
 				ItemDrop.OnCreateNew(component2);
 				if (m_nview.GetZDO().GetBool(ZDOVars.s_cheated) && !PlayerProfile.s_bypassCheatChecks)
@@ -463,13 +463,13 @@
 	{
 		if (enabled)
 		{
-			MaterialMan.instance.SetValue(base.gameObject, ShaderProps._Color, Color.red);
-			MaterialMan.instance.SetValue(base.gameObject, ShaderProps._EmissionColor, Color.red * 0.7f);
+			MaterialMan.instance.SetValue(gameObject, ShaderProps._Color, Color.red);
+			MaterialMan.instance.SetValue(gameObject, ShaderProps._EmissionColor, Color.red * 0.7f);
 		}
 		else
 		{
-			MaterialMan.instance.ResetValue(base.gameObject, ShaderProps._Color);
-			MaterialMan.instance.ResetValue(base.gameObject, ShaderProps._EmissionColor);
+			MaterialMan.instance.ResetValue(gameObject, ShaderProps._Color);
+			MaterialMan.instance.ResetValue(gameObject, ShaderProps._EmissionColor);
 		}
 	}
 
@@ -617,9 +617,9 @@
 
 	public void GetSnapPoints(List<Transform> points)
 	{
-		for (int i = 0; i < base.transform.childCount; i++)
-		{
-			Transform child = base.transform.GetChild(i);
+		for (int i = 0; i < transform.childCount; i++)
+		{
+			Transform child = transform.GetChild(i);
 			if (child.CompareTag("snappoint"))
 			{
 				points.Add(child);
```

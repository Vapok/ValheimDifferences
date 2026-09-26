# `CraftingStation.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CraftingStation.cs
+++ b/CraftingStation.cs
@@ -234,7 +234,7 @@
 
 	private void CheckFire()
 	{
-		m_haveFire = EffectArea.IsPointPlus025InsideBurningArea(base.transform.position);
+		m_haveFire = EffectArea.IsPointPlus025InsideBurningArea(transform.position);
 		if ((bool)m_haveFireObject)
 		{
 			m_haveFireObject.SetActive(m_haveFire);
@@ -321,7 +321,7 @@
 		{
 			m_updateExtensionTimer = 0f;
 			m_attachedExtensions.Clear();
-			StationExtension.FindExtensions(this, base.transform.position, m_attachedExtensions);
+			StationExtension.FindExtensions(this, transform.position, m_attachedExtensions);
 			m_buildRange = m_rangeBuild + (float)GetExtentionCount(checkExtensions: false) * m_extraRangePerLevel;
 			if ((bool)m_areaMarker)
 			{
@@ -365,7 +365,7 @@
 		{
 			return m_connectionPoint.position;
 		}
-		return base.transform.position;
+		return transform.position;
 	}
 
 	public int GetLevel(bool checkExtensions = true)
@@ -390,7 +390,7 @@
 
 	public bool InUseDistance(Humanoid human)
 	{
-		return Vector3.Distance(human.transform.position, base.transform.position) < m_useDistance;
+		return Vector3.Distance(human.transform.position, transform.position) < m_useDistance;
 	}
 
 	public float GetHoverOffset()
```

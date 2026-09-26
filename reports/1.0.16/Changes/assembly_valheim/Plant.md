# `Plant.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+14/-14` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Plant.cs
+++ b/Plant.cs
@@ -92,7 +92,7 @@
 	public override void Awake()
 	{
 		base.Awake();
-		m_nview = base.gameObject.GetComponent<ZNetView>();
+		m_nview = gameObject.GetComponent<ZNetView>();
 		if (m_nview.GetZDO() != null)
 		{
 			m_seed = m_nview.GetZDO().GetInt(ZDOVars.s_seed);
@@ -191,8 +191,8 @@
 		float num = 11.25f;
 		GameObject original = m_grownPrefabs[UnityEngine.Random.Range(0, m_grownPrefabs.Length)];
 		GameObject gameObject = null;
-		Vector3 position = ((m_attachDistance > 0f) ? m_attachPos : base.transform.position);
-		Quaternion quaternion = ((m_attachDistance > 0f) ? m_attachRot : Quaternion.Euler(base.transform.rotation.eulerAngles.x, base.transform.rotation.eulerAngles.y + UnityEngine.Random.Range(0f - num, num), base.transform.rotation.eulerAngles.z));
+		Vector3 position = ((m_attachDistance > 0f) ? m_attachPos : transform.position);
+		Quaternion quaternion = ((m_attachDistance > 0f) ? m_attachRot : Quaternion.Euler(transform.rotation.eulerAngles.x, transform.rotation.eulerAngles.y + UnityEngine.Random.Range(0f - num, num), transform.rotation.eulerAngles.z));
 		gameObject = UnityEngine.Object.Instantiate(original, position, quaternion);
 		if (m_attachDistance > 0f)
 		{
@@ -207,7 +207,7 @@
 		if ((bool)m_nview)
 		{
 			m_nview.Destroy();
-			m_growEffect.Create(base.transform.position, quaternion, null, num2);
+			m_growEffect.Create(transform.position, quaternion, null, num2);
 		}
 		return gameObject;
 	}
@@ -219,26 +219,26 @@
 			m_status = Status.Healthy;
 			return;
 		}
-		Heightmap heightmap = Heightmap.FindHeightmap(base.transform.position);
+		Heightmap heightmap = Heightmap.FindHeightmap(transform.position);
 		if ((bool)heightmap)
 		{
-			Heightmap.Biome biome = heightmap.GetBiome(base.transform.position);
+			Heightmap.Biome biome = heightmap.GetBiome(transform.position);
 			if ((biome & m_biome) == 0)
 			{
 				m_status = Status.WrongBiome;
 				return;
 			}
-			if (m_needCultivatedGround && !heightmap.IsCultivated(base.transform.position))
+			if (m_needCultivatedGround && !heightmap.IsCultivated(transform.position))
 			{
 				m_status = Status.NotCultivated;
 				return;
 			}
-			if (!m_tolerateHeat && biome == Heightmap.Biome.AshLands && !ShieldGenerator.IsInsideShield(base.transform.position))
+			if (!m_tolerateHeat && biome == Heightmap.Biome.AshLands && !ShieldGenerator.IsInsideShield(transform.position))
 			{
 				m_status = Status.TooHot;
 				return;
 			}
-			if (!m_tolerateCold && (biome == Heightmap.Biome.DeepNorth || biome == Heightmap.Biome.Mountain) && !ShieldGenerator.IsInsideShield(base.transform.position))
+			if (!m_tolerateCold && (biome == Heightmap.Biome.DeepNorth || biome == Heightmap.Biome.Mountain) && !ShieldGenerator.IsInsideShield(transform.position))
 			{
 				m_status = Status.TooCold;
 				return;
@@ -264,7 +264,7 @@
 
 	public Collider GetClosestAttachObject()
 	{
-		return GetClosestAttachObject(base.transform.position);
+		return GetClosestAttachObject(transform.position);
 	}
 
 	public Collider GetClosestAttachObject(Vector3 from)
@@ -295,7 +295,7 @@
 
 	public bool GetClosestAttachPosRot(out Vector3 pos, out Quaternion rot, out Vector3 normal)
 	{
-		return GetClosestAttachPosRot(base.transform.position, out pos, out rot, out normal);
+		return GetClosestAttachPosRot(transform.position, out pos, out rot, out normal);
 	}
 
 	public bool GetClosestAttachPosRot(Vector3 from, out Vector3 pos, out Quaternion rot, out Vector3 normal)
@@ -379,7 +379,7 @@
 		{
 			m_roofMask = LayerMask.GetMask("Default", "static_solid", "piece");
 		}
-		if (Physics.Raycast(base.transform.position, Vector3.up, 100f, m_roofMask))
+		if (Physics.Raycast(transform.position, Vector3.up, 100f, m_roofMask))
 		{
 			return true;
 		}
@@ -392,7 +392,7 @@
 		{
 			m_spaceMask = LayerMask.GetMask("Default", "static_solid", "Default_small", "piece", "piece_nonsolid");
 		}
-		int num = Physics.OverlapSphereNonAlloc(base.transform.position, m_growRadius, s_colliders, m_spaceMask);
+		int num = Physics.OverlapSphereNonAlloc(transform.position, m_growRadius, s_colliders, m_spaceMask);
 		for (int i = 0; i < num; i++)
 		{
 			Plant component = s_colliders[i].GetComponent<Plant>();
@@ -403,7 +403,7 @@
 		}
 		if (m_growRadiusVines > 0f)
 		{
-			num = Physics.OverlapSphereNonAlloc(base.transform.position, m_growRadiusVines, s_colliders, m_spaceMask);
+			num = Physics.OverlapSphereNonAlloc(transform.position, m_growRadiusVines, s_colliders, m_spaceMask);
 			for (int j = 0; j < num; j++)
 			{
 				if (s_colliders[j].GetComponentInParent<Vine>() != null)
```

# `ItemDrop.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+18/-18` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ItemDrop.cs
+++ b/ItemDrop.cs
@@ -1256,13 +1256,13 @@
 
 	private void Awake()
 	{
-		if (!string.IsNullOrEmpty(base.name))
-		{
-			m_nameHash = base.name.GetStableHashCode();
+		if (!string.IsNullOrEmpty(name))
+		{
+			m_nameHash = name.GetStableHashCode();
 		}
 		m_myIndex = s_instances.Count;
 		s_instances.Add(this);
-		string prefabName = GetPrefabName(base.gameObject.name);
+		string prefabName = GetPrefabName(gameObject.name);
 		GameObject itemPrefab = ObjectDB.instance.GetItemPrefab(prefabName);
 		m_itemData.m_dropPrefab = itemPrefab;
 		if (Application.isEditor)
@@ -1315,7 +1315,7 @@
 	private void Start()
 	{
 		Save();
-		base.gameObject.GetComponentInChildren<IEquipmentVisual>()?.Setup(m_itemData.m_variant);
+		gameObject.GetComponentInChildren<IEquipmentVisual>()?.Setup(m_itemData.m_variant);
 	}
 
 	public static void OnCreateNew(GameObject go, bool cheated = false)
@@ -1357,12 +1357,12 @@
 
 	private void TerrainCheck()
 	{
-		float groundHeight = ZoneSystem.instance.GetGroundHeight(base.transform.position);
-		if (base.transform.position.y - groundHeight < -0.5f)
-		{
-			Vector3 position = base.transform.position;
+		float groundHeight = ZoneSystem.instance.GetGroundHeight(transform.position);
+		if (transform.position.y - groundHeight < -0.5f)
+		{
+			Vector3 position = transform.position;
 			position.y = groundHeight + 0.5f;
-			base.transform.position = position;
+			transform.position = position;
 			Rigidbody component = GetComponent<Rigidbody>();
 			if ((bool)component)
 			{
@@ -1373,7 +1373,7 @@
 
 	private void TimedDestruction()
 	{
-		if (!(GetTimeSinceSpawned() < 3600.0) && !IsInsideBase() && !Player.IsPlayerInRange(base.transform.position, 25f) && !InTar() && !IsPiece())
+		if (!(GetTimeSinceSpawned() < 3600.0) && !IsInsideBase() && !Player.IsPlayerInRange(transform.position, 25f) && !InTar() && !IsPiece())
 		{
 			m_nview.Destroy();
 		}
@@ -1392,7 +1392,7 @@
 	{
 		if (!m_piece)
 		{
-			ZLog.LogError("Missing piece script to make piece out of " + base.name);
+			ZLog.LogError("Missing piece script to make piece out of " + name);
 		}
 		if ((bool)m_body)
 		{
@@ -1435,7 +1435,7 @@
 
 	private bool IsInsideBase()
 	{
-		if (base.transform.position.y > 28f && (bool)EffectArea.IsPointInsideArea(base.transform.position, EffectArea.Type.PlayerBase))
+		if (transform.position.y > 28f && (bool)EffectArea.IsPointInsideArea(transform.position, EffectArea.Type.PlayerBase))
 		{
 			return true;
 		}
@@ -1454,7 +1454,7 @@
 			s_itemMask = LayerMask.GetMask("item");
 		}
 		bool flag = false;
-		Collider[] array = Physics.OverlapSphere(base.transform.position, 4f, s_itemMask);
+		Collider[] array = Physics.OverlapSphere(transform.position, 4f, s_itemMask);
 		foreach (Collider collider in array)
 		{
 			if (!collider.attachedRigidbody)
@@ -1587,7 +1587,7 @@
 			if (CanPickup())
 			{
 				Load();
-				character.Pickup(base.gameObject);
+				character.Pickup(gameObject);
 				Save();
 			}
 			else
@@ -1698,7 +1698,7 @@
 
 	private void RPC_RequestOwn(long uid)
 	{
-		ZLog.Log("Player " + uid + " wants to pickup " + base.gameObject.name + "   im: " + ZDOMan.GetSessionID());
+		ZLog.Log("Player " + uid + " wants to pickup " + gameObject.name + "   im: " + ZDOMan.GetSessionID());
 		if (m_nview.IsOwner())
 		{
 			m_nview.GetZDO().SetOwner(uid);
@@ -1722,7 +1722,7 @@
 				ZLog.Log("Im finally the owner");
 				CancelInvoke("PickupUpdate");
 				Load();
-				(m_pickupRequester as Player).Pickup(base.gameObject);
+				(m_pickupRequester as Player).Pickup(gameObject);
 				Save();
 			}
 			else
@@ -1818,7 +1818,7 @@
 	public void SetQuality(int quality)
 	{
 		m_itemData.m_quality = quality;
-		base.transform.localScale = m_itemData.GetScale();
+		transform.localScale = m_itemData.GetScale();
 	}
 
 	public int NameHash()
```

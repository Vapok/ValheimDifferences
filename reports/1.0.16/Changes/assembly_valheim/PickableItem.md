# `PickableItem.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+9/-9` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/PickableItem.cs
+++ b/PickableItem.cs
@@ -64,7 +64,7 @@
 			GameObject itemPrefab = ObjectDB.instance.GetItemPrefab(num);
 			if (itemPrefab == null)
 			{
-				ZLog.LogError("Failed to find saved prefab " + num + " in PickableItem " + base.gameObject.name);
+				ZLog.LogError("Failed to find saved prefab " + num + " in PickableItem " + gameObject.name);
 				return;
 			}
 			m_itemPrefab = itemPrefab.GetComponent<ItemDrop>();
@@ -115,7 +115,7 @@
 		if (m_nview.IsOwner() && !m_picked)
 		{
 			m_picked = true;
-			m_pickEffector.Create(base.transform.position, Quaternion.identity);
+			m_pickEffector.Create(transform.position, Quaternion.identity);
 			Drop();
 			m_nview.Destroy();
 		}
@@ -123,15 +123,15 @@
 
 	private void Drop()
 	{
-		Vector3 position = base.transform.position + Vector3.up * 0.2f;
-		GameObject obj = UnityEngine.Object.Instantiate(m_itemPrefab.gameObject, position, base.transform.rotation);
-		ItemDrop component = obj.GetComponent<ItemDrop>();
+		Vector3 position = transform.position + Vector3.up * 0.2f;
+		GameObject gameObject = UnityEngine.Object.Instantiate(m_itemPrefab.gameObject, position, transform.rotation);
+		ItemDrop component = gameObject.GetComponent<ItemDrop>();
 		if ((object)component != null)
 		{
 			component.m_itemData.m_stack = GetStackSize();
 			ItemDrop.OnCreateNew(component);
 		}
-		obj.GetComponent<Rigidbody>().linearVelocity = Vector3.up * 4f;
+		gameObject.GetComponent<Rigidbody>().linearVelocity = Vector3.up * 4f;
 	}
 
 	private int GetStackSize()
@@ -167,7 +167,7 @@
 				ZLog.LogWarning("Failed to get attach prefab for item " + m_itemPrefab.name);
 				return;
 			}
-			m_instance = UnityEngine.Object.Instantiate(attachPrefab, base.transform.position, base.transform.rotation, base.transform);
+			m_instance = UnityEngine.Object.Instantiate(attachPrefab, transform.position, transform.rotation, transform);
 			m_instance.transform.localPosition = attachPrefab.transform.localPosition;
 			m_instance.transform.localRotation = attachPrefab.transform.localRotation;
 		}
@@ -189,9 +189,9 @@
 				Vector3 position = prefab.transform.position;
 				Quaternion quaternion = Quaternion.Inverse(prefab.transform.rotation);
 				Vector3 vector = meshFilter.transform.position - position;
-				Vector3 position2 = base.transform.position + base.transform.rotation * vector;
+				Vector3 position2 = transform.position + transform.rotation * vector;
 				Quaternion quaternion2 = quaternion * meshFilter.transform.rotation;
-				Quaternion rotation = base.transform.rotation * quaternion2;
+				Quaternion rotation = transform.rotation * quaternion2;
 				Gizmos.DrawMesh(meshFilter.sharedMesh, position2, rotation, meshFilter.transform.lossyScale);
 				result = true;
 			}
```

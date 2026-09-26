# `PrivateArea.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+13/-13` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/PrivateArea.cs
+++ b/PrivateArea.cs
@@ -182,7 +182,7 @@
 		if (permittedPlayers.RemoveAll((KeyValuePair<long, string> x) => x.Key == playerID) > 0)
 		{
 			SetPermittedPlayers(permittedPlayers);
-			m_removedPermittedEffect.Create(base.transform.position, base.transform.rotation);
+			m_removedPermittedEffect.Create(transform.position, transform.rotation);
 		}
 	}
 
@@ -210,7 +210,7 @@
 		}
 		permittedPlayers.Add(new KeyValuePair<long, string>(playerID, playerName));
 		SetPermittedPlayers(permittedPlayers);
-		m_addPermittedEffect.Create(base.transform.position, base.transform.rotation);
+		m_addPermittedEffect.Create(transform.position, transform.rotation);
 	}
 
 	private void SetPermittedPlayers(List<KeyValuePair<long, string>> users)
@@ -313,11 +313,11 @@
 		UpdateStatus();
 		if (enabled)
 		{
-			m_activateEffect.Create(base.transform.position, base.transform.rotation);
+			m_activateEffect.Create(transform.position, transform.rotation);
 		}
 		else
 		{
-			m_deactivateEffect.Create(base.transform.position, base.transform.rotation);
+			m_deactivateEffect.Create(transform.position, transform.rotation);
 		}
 	}
 
@@ -369,13 +369,13 @@
 				list.Add(allArea);
 			}
 		}
-		Vector3 vector = base.transform.position + Vector3.up * 1.4f;
+		Vector3 vector = transform.position + Vector3.up * 1.4f;
 		if (m_connectionInstances.Count != list.Count)
 		{
 			StopConnectionEffects();
 			for (int i = 0; i < list.Count; i++)
 			{
-				GameObject item = UnityEngine.Object.Instantiate(m_connectEffect, vector, Quaternion.identity, base.transform);
+				GameObject item = UnityEngine.Object.Instantiate(m_connectEffect, vector, Quaternion.identity, transform);
 				m_connectionInstances.Add(item);
 			}
 		}
@@ -385,10 +385,10 @@
 			{
 				Vector3 vector2 = list[j].transform.position + Vector3.up * 1.4f - vector;
 				Quaternion rotation = Quaternion.LookRotation(vector2.normalized);
-				GameObject obj = m_connectionInstances[j];
-				obj.transform.position = vector;
-				obj.transform.rotation = rotation;
-				obj.transform.localScale = new Vector3(1f, 1f, vector2.magnitude);
+				GameObject gameObject = m_connectionInstances[j];
+				gameObject.transform.position = vector;
+				gameObject.transform.rotation = rotation;
+				gameObject.transform.localScale = new Vector3(1f, 1f, vector2.magnitude);
 			}
 			CancelInvoke("StopConnectionEffects");
 			Invoke("StopConnectionEffects", 0.3f);
@@ -525,7 +525,7 @@
 			return;
 		}
 		List<Character> list = new List<Character>();
-		Character.GetCharactersInRange(base.transform.position, m_radius * 2f, list);
+		Character.GetCharactersInRange(transform.position, m_radius * 2f, list);
 		foreach (Character item in list)
 		{
 			if (item.GetFaction() == m_ownerFaction)
@@ -567,7 +567,7 @@
 
 	private void RPC_FlashShield(long uid)
 	{
-		m_flashEffect.Create(base.transform.position, Quaternion.identity);
+		m_flashEffect.Create(transform.position, Quaternion.identity);
 	}
 
 	public static bool InsideFactionArea(Vector3 point, Character.Faction faction)
@@ -584,7 +584,7 @@
 
 	private bool IsInside(Vector3 point, float radius)
 	{
-		return Utils.DistanceXZ(base.transform.position, point) < m_radius + radius;
+		return Utils.DistanceXZ(transform.position, point) < m_radius + radius;
 	}
 
 	public void ShowAreaMarker()
```

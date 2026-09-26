# `Ragdoll.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Ragdoll.cs
+++ b/Ragdoll.cs
@@ -60,7 +60,7 @@
 	{
 		if (m_bodies.Length == 0)
 		{
-			return base.transform.position;
+			return transform.position;
 		}
 		Vector3 zero = Vector3.zero;
 		Rigidbody[] bodies = m_bodies;
@@ -83,7 +83,7 @@
 				vector = m_lootSpawnJoint.transform.position;
 			}
 			SpawnLoot(vector);
-			ZNetScene.instance.Destroy(base.gameObject);
+			ZNetScene.instance.Destroy(gameObject);
 		}
 	}
 
```

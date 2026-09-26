# `Room.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Room.cs
+++ b/Room.cs
@@ -65,21 +65,21 @@
 	{
 		if ((bool)m_musicPrefab)
 		{
-			UnityEngine.Object.Instantiate(m_musicPrefab, base.transform).m_sizeFromRoom = this;
+			UnityEngine.Object.Instantiate(m_musicPrefab, transform).m_sizeFromRoom = this;
 		}
 	}
 
 	private void OnDrawGizmos()
 	{
 		Gizmos.color = new Color(0.5f, 0.5f, 0.5f, 0.5f);
-		Gizmos.matrix = Matrix4x4.TRS(base.transform.position, base.transform.rotation, new Vector3(1f, 1f, 1f));
+		Gizmos.matrix = Matrix4x4.TRS(transform.position, transform.rotation, new Vector3(1f, 1f, 1f));
 		Gizmos.DrawWireCube(Vector3.zero, new Vector3(m_size.x, m_size.y, m_size.z));
 		Gizmos.matrix = Matrix4x4.identity;
 	}
 
 	public int GetHash()
 	{
-		return Utils.GetPrefabName(base.gameObject).GetStableHashCode();
+		return Utils.GetPrefabName(gameObject).GetStableHashCode();
 	}
 
 	private void OnEnable()
@@ -145,6 +145,6 @@
 
 	public override string ToString()
 	{
-		return string.Format("{0}, Enabled: {1}, {2}, {3}", base.name, m_enabled, m_theme, m_entrance ? "Entrance" : (m_endCap ? "EndCap" : "Room"));
+		return string.Format("{0}, Enabled: {1}, {2}, {3}", name, m_enabled, m_theme, m_entrance ? "Entrance" : (m_endCap ? "EndCap" : "Room"));
 	}
 }
```

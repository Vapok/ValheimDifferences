# `SmokeRenderer.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+10/-148` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `AddSmokeToChunk() [Method Body Modified]`
- `AddSmokeToChunk() [Method Removed]`
- `Awake() [Method Body Modified]`
- `Awake() [Method Removed]`
- `ChunkToWorld() [Method Body Modified]`
- `ChunkToWorld() [Method Removed]`
- `CleanupChunk() [Method Body Modified]`
- `CleanupChunk() [Method Removed]`
- `Instance [Field Removed, was SmokeRenderer]`
- `LateUpdate() [Method Body Modified]`
- `LateUpdate() [Method Removed]`
- `OnDrawGizmosSelected() [Method Body Modified]`
- `OnDrawGizmosSelected() [Method Removed]`
- `PositionToChunk() [Method Body Modified]`
- `PositionToChunk() [Method Removed]`
- `RegisterSmoke() [Method Body Modified]`
- `RegisterSmoke() [Method Removed]`
- `RemoveSmokeFromChunk() [Method Body Modified]`
- `RemoveSmokeFromChunk() [Method Removed]`
- `Start() [Method Body Modified]`
- `TransferSmokeBetweenChunks() [Method Body Modified]`
- `TransferSmokeBetweenChunks() [Method Removed]`
- `UnregisterSmoke() [Method Body Modified]`
- `UnregisterSmoke() [Method Removed]`
- `Update() [Method Body Modified]`
- `UpdateInstances() [Method Body Modified]`
- `_particleSystemPrefab [Field Removed, was ParticleSystem]`
- `c_MaxChunkParticleCount [Field Removed, was int]`
- `m_chunkSize [Field Removed, was float]`
- `m_chunkedParticleSystems [Field Removed, was Dictionary<Vector3Int, ParticleSystem>]`
- `m_chunkedParticles [Field Removed, was Dictionary<Vector3Int, ParticleSystem.Particle[]>]`
- `m_chunkedSmoke [Field Removed, was Dictionary<Vector3Int, List<Smoke>>]`
- `m_chunkedSmokeToMove [Field Removed, was List<Tuple<Vector3Int, Vector3Int, Smoke>>]`
- `m_smokeBallSize [Field Removed, was float]`
- `m_smokeColor [Field Removed, was Color]`
- `private Vector3 ChunkToWorld(Vector3Int chunk)`
- `private Vector3Int PositionToChunk(Vector3 pos)`
- `private void AddSmokeToChunk(Vector3Int chunk, Smoke smoke)`
- `private void Awake()`
- `private void CleanupChunk(Vector3Int chunk)`
- `private void LateUpdate()`
- `private void OnDrawGizmosSelected()`
- `private void RemoveSmokeFromChunk(Vector3Int chunk, Smoke smoke)`
- `private void Start()`
- `private void TransferSmokeBetweenChunks()`
- `private void Update()`
- `private void UpdateInstances()`
- `public void RegisterSmoke(Smoke smoke)`
- `public void UnregisterSmoke(Smoke smoke)`

---

## 📝 Code Diff

```diff
--- a/SmokeRenderer.cs
+++ b/SmokeRenderer.cs
@@ -1,164 +1,26 @@
-using System;
 using System.Collections.Generic;
 using UnityEngine;
 
 public class SmokeRenderer : MonoBehaviour
 {
-	[SerializeField]
-	private ParticleSystem _particleSystemPrefab;
+	private InstanceRenderer m_instanceRenderer;
 
-	[SerializeField]
-	private Color m_smokeColor;
+	private List<Vector4> tempTransforms = new List<Vector4>();
 
-	[SerializeField]
-	private float m_smokeBallSize = 4f;
+	private void Start()
+	{
+		m_instanceRenderer = GetComponent<InstanceRenderer>();
+	}
 
-	[Header("Chunking")]
-	[SerializeField]
-	private float m_chunkSize = 10f;
-
-	private Dictionary<Vector3Int, ParticleSystem> m_chunkedParticleSystems = new Dictionary<Vector3Int, ParticleSystem>();
-
-	private Dictionary<Vector3Int, List<Smoke>> m_chunkedSmoke = new Dictionary<Vector3Int, List<Smoke>>();
-
-	private Dictionary<Vector3Int, ParticleSystem.Particle[]> m_chunkedParticles = new Dictionary<Vector3Int, ParticleSystem.Particle[]>();
-
-	private List<Tuple<Vector3Int, Vector3Int, Smoke>> m_chunkedSmokeToMove = new List<Tuple<Vector3Int, Vector3Int, Smoke>>();
-
-	public static SmokeRenderer Instance;
-
-	private const int c_MaxChunkParticleCount = 100;
-
-	private void Awake()
+	private void Update()
 	{
-		if (Instance == null)
+		if (!(Utils.GetMainCamera() == null))
 		{
-			Instance = this;
-		}
-		else
-		{
-			UnityEngine.Object.Destroy(gameObject);
+			UpdateInstances();
 		}
 	}
 
-	public void RegisterSmoke(Smoke smoke)
+	private void UpdateInstances()
 	{
-		AddSmokeToChunk(PositionToChunk(smoke.transform.position), smoke);
-	}
-
-	public void UnregisterSmoke(Smoke smoke)
-	{
-		RemoveSmokeFromChunk(smoke.RenderChunk, smoke);
-	}
-
-	private Vector3Int PositionToChunk(Vector3 pos)
-	{
-		int x = Mathf.FloorToInt(pos.x / m_chunkSize);
-		int y = Mathf.FloorToInt(pos.y / m_chunkSize);
-		int z = Mathf.FloorToInt(pos.z / m_chunkSize);
-		return new Vector3Int(x, y, z);
-	}
-
-	private Vector3 ChunkToWorld(Vector3Int chunk)
-	{
-		return new Vector3((float)chunk.x * m_chunkSize, (float)chunk.y * m_chunkSize, (float)chunk.z * m_chunkSize);
-	}
-
-	private void AddSmokeToChunk(Vector3Int chunk, Smoke smoke)
-	{
-		if (!m_chunkedSmoke.ContainsKey(chunk))
-		{
-			m_chunkedSmoke.Add(chunk, new List<Smoke>());
-			m_chunkedParticleSystems.Add(chunk, UnityEngine.Object.Instantiate(_particleSystemPrefab, ChunkToWorld(chunk), Quaternion.identity));
-			m_chunkedParticles.Add(chunk, new ParticleSystem.Particle[100]);
-		}
-		if (!m_chunkedSmoke[chunk].Contains(smoke))
-		{
-			m_chunkedSmoke[chunk].Add(smoke);
-		}
-		smoke.RenderChunk = chunk;
-	}
-
-	private void RemoveSmokeFromChunk(Vector3Int chunk, Smoke smoke)
-	{
-		if (m_chunkedSmoke.ContainsKey(chunk))
-		{
-			m_chunkedSmoke[chunk].Remove(smoke);
-			if (m_chunkedSmoke[chunk].Count == 0)
-			{
-				CleanupChunk(chunk);
-			}
-		}
-	}
-
-	private void CleanupChunk(Vector3Int chunk)
-	{
-		m_chunkedParticles.Remove(chunk);
-		m_chunkedSmoke.Remove(chunk);
-		m_chunkedParticleSystems.Remove(chunk, out var value);
-		if (value != null)
-		{
-			UnityEngine.Object.Destroy(value.gameObject);
-		}
-	}
-
-	private void TransferSmokeBetweenChunks()
-	{
-		m_chunkedSmokeToMove.Clear();
-		foreach (Vector3Int key in m_chunkedSmoke.Keys)
-		{
-			foreach (Smoke item in m_chunkedSmoke[key])
-			{
-				Vector3Int vector3Int = PositionToChunk(item.transform.position);
-				if (vector3Int != key)
-				{
-					m_chunkedSmokeToMove.Add(new Tuple<Vector3Int, Vector3Int, Smoke>(key, vector3Int, item));
-				}
-			}
-		}
-		foreach (Tuple<Vector3Int, Vector3Int, Smoke> item2 in m_chunkedSmokeToMove)
-		{
-			RemoveSmokeFromChunk(item2.Item1, item2.Item3);
-			AddSmokeToChunk(item2.Item2, item2.Item3);
-		}
-	}
-
-	private void LateUpdate()
-	{
-		TransferSmokeBetweenChunks();
-		foreach (Vector3Int key in m_chunkedParticleSystems.Keys)
-		{
-			ParticleSystem particleSystem = m_chunkedParticleSystems[key];
-			List<Smoke> list = m_chunkedSmoke[key];
-			ParticleSystem.Particle[] array = m_chunkedParticles[key];
-			if (list.Count > particleSystem.particleCount)
-			{
-				particleSystem.Emit(list.Count - particleSystem.particleCount);
-			}
-			for (int i = 0; i < list.Count; i++)
-			{
-				Smoke smoke = list[i];
-				array[i] = smoke.GetParticleValues();
-				array[i].startColor = m_smokeColor * new Color(1f, 1f, 1f, smoke.GetAlpha());
-				array[i].startSize = m_smokeBallSize;
-			}
-			for (int j = list.Count; j < particleSystem.particleCount; j++)
-			{
-				array[j].remainingLifetime = -1f;
-			}
-			particleSystem.SetParticles(array, particleSystem.particleCount);
-		}
-	}
-
-	private void OnDrawGizmosSelected()
-	{
-		foreach (Vector3Int key in m_chunkedSmoke.Keys)
-		{
-			Vector3 vector = ChunkToWorld(key);
-			Color a = new Color(0.43f, 1f, 0f, 0.26f);
-			Color red = Color.red;
-			Gizmos.color = Color.Lerp(a, red, (float)m_chunkedSmoke[key].Count / 100f * 0.33f);
-			Gizmos.DrawWireCube(vector + Vector3.one * m_chunkSize * 0.5f, m_chunkSize * Vector3.one);
-		}
 	}
 }
```

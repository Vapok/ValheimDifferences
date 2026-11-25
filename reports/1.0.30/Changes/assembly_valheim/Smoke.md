# `Smoke.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+22/-47` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Awake() [Method Body Modified]`
- `CustomUpdate() [Method Body Modified]`
- `GetAlpha() [Method Body Modified]`
- `GetAlpha() [Method Removed]`
- `GetParticleValues() [Method Body Modified]`
- `GetParticleValues() [Method Removed]`
- `OnDisable() [Method Body Modified]`
- `OnEnable() [Method Body Modified]`
- `SetupParticle() [Method Body Modified]`
- `SetupParticle() [Method Removed]`
- `StartFadeOut() [Method Body Modified]`
- `m_renderParticle [Field Removed, was ParticleSystem.Particle]`
- `private void SetupParticle()`
- `public float GetAlpha()`

---

## 📝 Code Diff

```diff
--- a/Smoke.cs
+++ b/Smoke.cs
@@ -21,11 +21,15 @@
 
 	private bool m_added;
 
-	private ParticleSystem.Particle m_renderParticle;
+	private float m_alpha = 1f;
+
+	private MeshRenderer m_mr;
+
+	private MaterialPropertyBlock m_propertyBlock;
 
 	private static readonly List<Smoke> s_smoke = new List<Smoke>();
 
-	public Vector3Int RenderChunk { get; set; } = Vector3Int.zero;
+	private static readonly int m_colorProp = Shader.PropertyToID("_Color");
 
 	public static List<IMonoUpdater> Instances { get; } = new List<IMonoUpdater>();
 
@@ -34,59 +38,23 @@
 		s_smoke.Add(this);
 		m_added = true;
 		m_body = GetComponent<Rigidbody>();
+		m_mr = GetComponent<MeshRenderer>();
+		m_propertyBlock = new MaterialPropertyBlock();
+		Color color = m_mr.sharedMaterial.color;
+		color.a = 0f;
+		m_propertyBlock.SetColor(m_colorProp, color);
+		m_mr.SetPropertyBlock(m_propertyBlock);
 		m_body.maxDepenetrationVelocity = 1f;
 		m_vel = Vector3.up + Quaternion.Euler(0f, Random.Range(0, 360), 0f) * Vector3.forward * m_randomVel;
-		SetupParticle();
-	}
-
-	private void SetupParticle()
-	{
-		float num = Random.Range(0f, 360f);
-		m_renderParticle = new ParticleSystem.Particle
-		{
-			angularVelocity = 0f,
-			angularVelocity3D = Vector3.zero,
-			axisOfRotation = new Vector3(0f, 0f, 1f),
-			position = transform.position,
-			randomSeed = (uint)Random.Range(int.MinValue, int.MaxValue),
-			remainingLifetime = m_ttl + m_fadetime,
-			startLifetime = m_ttl,
-			rotation = num,
-			rotation3D = new Vector3(0f, 0f, num),
-			velocity = Vector3.zero
-		};
-	}
-
-	public ParticleSystem.Particle GetParticleValues()
-	{
-		if (m_fadeTimer < 0f)
-		{
-			m_renderParticle.remainingLifetime = m_ttl - m_time;
-		}
-		else
-		{
-			m_renderParticle.remainingLifetime = m_fadetime - m_fadeTimer;
-		}
-		m_renderParticle.position = transform.position;
-		return m_renderParticle;
-	}
-
-	public float GetAlpha()
-	{
-		float a = Utils.SmoothStep(0f, 1f, Mathf.Clamp01(m_time / 2f));
-		float b = Utils.SmoothStep(0f, 1f, 1f - Mathf.Clamp01(m_fadeTimer / m_fadetime));
-		return Mathf.Min(a, b);
 	}
 
 	private void OnEnable()
 	{
 		Instances.Add(this);
-		SmokeRenderer.Instance.RegisterSmoke(this);
 	}
 
 	private void OnDisable()
 	{
-		SmokeRenderer.Instance.UnregisterSmoke(this);
 		Instances.Remove(this);
 	}
 
@@ -108,7 +76,6 @@
 				s_smoke.Remove(this);
 				m_added = false;
 			}
-			m_renderParticle.startLifetime = m_time + m_fadetime;
 			m_fadeTimer = 0f;
 		}
 	}
@@ -157,13 +124,13 @@
 
 	public void CustomUpdate(float deltaTime, float time)
 	{
+		m_alpha = Mathf.Clamp01(m_time);
 		m_time += deltaTime;
 		if (m_time > m_ttl && m_fadeTimer < 0f)
 		{
 			StartFadeOut();
 		}
 		float num = 1f - Mathf.Clamp01(m_time / m_ttl);
-		m_body.mass = num * num;
 		Vector3 linearVelocity = m_body.linearVelocity;
 		Vector3 vel = m_vel;
 		vel.y *= num;
@@ -172,11 +139,19 @@
 		if (m_fadeTimer >= 0f)
 		{
 			m_fadeTimer += deltaTime;
-			Mathf.Clamp01(m_fadeTimer / m_fadetime);
+			float num2 = 1f - Mathf.Clamp01(m_fadeTimer / m_fadetime);
+			m_alpha *= num2;
 			if (m_fadeTimer >= m_fadetime)
 			{
 				Object.Destroy(gameObject);
 			}
 		}
+		if (m_time <= 1f || m_fadeTimer > 0f)
+		{
+			Color color = m_propertyBlock.GetColor(m_colorProp);
+			color.a = m_alpha;
+			m_propertyBlock.SetColor(m_colorProp, color);
+			m_mr.SetPropertyBlock(m_propertyBlock);
+		}
 	}
 }
```

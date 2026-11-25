# `ConditionalObject.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Awake() [Method Body Modified]`
- `Update() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/ConditionalObject.cs
+++ b/ConditionalObject.cs
@@ -60,6 +60,8 @@
 
 	public Vector3 m_startSpringVelocity = new Vector3(1.5f, -1f, 1.5f);
 
+	private Animator m_enableObjectAnimator;
+
 	private void Awake()
 	{
 		m_startScale = m_enableObject.transform.localScale;
@@ -72,12 +74,13 @@
 			EndValue = m_startScale,
 			InitialVelocity = m_startSpringVelocity
 		};
+		m_enableObjectAnimator = m_enableObject.GetComponentInChildren<Animator>();
 		if (ShouldBeVisible() && !string.IsNullOrEmpty(m_globalKeyCondition))
 		{
 			m_enableObject.SetActive(value: true);
-			if (!string.IsNullOrEmpty(m_animatorBool))
+			if (!string.IsNullOrEmpty(m_animatorBool) && (bool)m_enableObjectAnimator)
 			{
-				m_enableObject.GetComponentInChildren<Animator>()?.SetBool(m_animatorBool, value: true);
+				m_enableObjectAnimator.SetBool(m_animatorBool, value: true);
 			}
 			m_springActive = false;
 			m_dropTimer = float.PositiveInfinity;
@@ -108,10 +111,9 @@
 				m_showEffects.Create(transform.position, transform.rotation, transform);
 				if (!string.IsNullOrEmpty(m_animatorBool))
 				{
-					Animator componentInChildren = m_enableObject.GetComponentInChildren<Animator>();
-					if ((object)componentInChildren != null)
+					if ((bool)m_enableObjectAnimator)
 					{
-						componentInChildren.SetBool(m_animatorBool, value: true);
+						m_enableObjectAnimator.SetBool(m_animatorBool, value: true);
 					}
 					else
 					{
```

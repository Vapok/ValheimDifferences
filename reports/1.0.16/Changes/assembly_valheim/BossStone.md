# `BossStone.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/BossStone.cs
+++ b/BossStone.cs
@@ -83,12 +83,12 @@
 
 	private void DelayedAttachEffects_Step1()
 	{
-		m_activateStep1.Create(m_itemStand.transform.position, base.transform.rotation);
+		m_activateStep1.Create(m_itemStand.transform.position, transform.rotation);
 	}
 
 	private void DelayedAttachEffects_Step2()
 	{
-		m_activateStep2.Create(base.transform.position, base.transform.rotation);
+		m_activateStep2.Create(transform.position, transform.rotation);
 	}
 
 	private void DelayedAttachEffects_Step3()
@@ -97,10 +97,10 @@
 		{
 			m_activeEffect.SetActive(value: true);
 		}
-		m_activateStep3.Create(base.transform.position, base.transform.rotation);
+		m_activateStep3.Create(transform.position, transform.rotation);
 		StopCoroutine("FadeEmission");
 		StartCoroutine("FadeEmission");
-		Player.MessageAllInRange(base.transform.position, 20f, MessageHud.MessageType.Center, m_completedMessage);
+		Player.MessageAllInRange(transform.position, 20f, MessageHud.MessageType.Center, m_completedMessage);
 	}
 
 	private IEnumerator FadeEmission()
```

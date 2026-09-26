# `RandomSpeak.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/RandomSpeak.cs
+++ b/RandomSpeak.cs
@@ -41,17 +41,17 @@
 
 	private void Speak()
 	{
-		if (Random.value > m_chance || m_texts.Length == 0 || Player.m_localPlayer == null || Vector3.Distance(base.transform.position, Player.m_localPlayer.transform.position) > m_triggerDistance || (m_onlyOnItemStand && !base.gameObject.GetComponentInParent<ItemStand>()))
+		if (Random.value > m_chance || m_texts.Length == 0 || Player.m_localPlayer == null || Vector3.Distance(transform.position, Player.m_localPlayer.transform.position) > m_triggerDistance || (m_onlyOnItemStand && !gameObject.GetComponentInParent<ItemStand>()))
 		{
 			return;
 		}
 		float dayFraction = EnvMan.instance.GetDayFraction();
 		if ((m_invertTod || (!(dayFraction < m_minTOD) && !(dayFraction > m_maxTOD))) && (!m_invertTod || !(dayFraction > m_minTOD) || !(dayFraction < m_maxTOD)))
 		{
-			m_speakEffects.Create(base.transform.position, base.transform.rotation);
+			m_speakEffects.Create(transform.position, transform.rotation);
 			int num = (m_indexFromDay ? (EnvMan.instance.GetDay() % m_texts.Length) : Random.Range(0, m_texts.Length));
 			string text = m_texts[num];
-			Chat.instance.SetNpcText(base.gameObject, m_offset, m_cullDistance, m_ttl, m_topic, text, m_useLargeDialog);
+			Chat.instance.SetNpcText(gameObject, m_offset, m_cullDistance, m_ttl, m_topic, text, m_useLargeDialog);
 			if (m_onlyOnce)
 			{
 				CancelInvoke("Speak");
```

# `MessageHud.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MessageHud.cs
+++ b/MessageHud.cs
@@ -267,7 +267,7 @@
 		if (m_biomeFoundQueue.Count > 0 && m_biomeMsgInstance == null && m_msgQeue.Count == 0 && m_msgQueueTimer > 2f)
 		{
 			BiomeMessage biomeMessage = m_biomeFoundQueue.Dequeue();
-			m_biomeMsgInstance = Object.Instantiate(m_biomeFoundPrefab, base.transform);
+			m_biomeMsgInstance = Object.Instantiate(m_biomeFoundPrefab, transform);
 			TMP_Text component = Utils.FindChild(m_biomeMsgInstance.transform, "Title").GetComponent<TMP_Text>();
 			string text = Localization.instance.Localize(biomeMessage.m_text);
 			component.text = text;
@@ -333,7 +333,7 @@
 			int freeUnlockMsgSlot = GetFreeUnlockMsgSlot();
 			if (freeUnlockMsgSlot != -1)
 			{
-				Transform parent = base.transform;
+				Transform parent = transform;
 				GameObject gameObject2 = Object.Instantiate(m_unlockMsgPrefab, parent);
 				m_unlockMessages[freeUnlockMsgSlot] = gameObject2;
 				RectTransform obj = gameObject2.transform as RectTransform;
```

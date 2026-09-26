# `Trader.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+10/-10` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Trader.cs
+++ b/Trader.cs
@@ -144,10 +144,10 @@
 
 	private void Update()
 	{
-		Player closestPlayer = Player.GetClosestPlayer(base.transform.position, Mathf.Max(m_byeRange + 3f, m_standRange));
+		Player closestPlayer = Player.GetClosestPlayer(transform.position, Mathf.Max(m_byeRange + 3f, m_standRange));
 		if ((bool)closestPlayer)
 		{
-			float num = Vector3.Distance(closestPlayer.transform.position, base.transform.position);
+			float num = Vector3.Distance(closestPlayer.transform.position, transform.position);
 			if (num < m_standRange)
 			{
 				m_animator.SetBool("Stand", value: true);
@@ -158,13 +158,13 @@
 				m_didGreet = true;
 				List<string> texts = CheckConditionals(m_randomGreets, isGreet: true);
 				Say(texts, "Greet");
-				m_randomGreetFX.Create(base.transform.position, Quaternion.identity);
+				m_randomGreetFX.Create(transform.position, Quaternion.identity);
 			}
 			if (m_didGreet && !m_didGoodbye && num > m_byeRange)
 			{
 				m_didGoodbye = true;
 				Say(m_randomGoodbye, "Greet");
-				m_randomGoodbyeFX.Create(base.transform.position, Quaternion.identity);
+				m_randomGoodbyeFX.Create(transform.position, Quaternion.identity);
 			}
 		}
 		else
@@ -176,11 +176,11 @@
 
 	private void RandomTalk()
 	{
-		if (m_animator.GetBool("Stand") && !StoreGui.IsVisible() && Player.IsPlayerInRange(base.transform.position, m_greetRange))
+		if (m_animator.GetBool("Stand") && !StoreGui.IsVisible() && Player.IsPlayerInRange(transform.position, m_greetRange))
 		{
 			List<string> texts = CheckConditionals(m_randomTalk, isGreet: false);
 			Say(texts, "Talk");
-			m_randomTalkFX.Create(base.transform.position, Quaternion.identity);
+			m_randomTalkFX.Create(transform.position, Quaternion.identity);
 		}
 	}
 
@@ -270,7 +270,7 @@
 		}
 		StoreGui.instance.Show(this);
 		Say(m_randomStartTrade, "Talk");
-		m_randomStartTradeFX.Create(base.transform.position, Quaternion.identity);
+		m_randomStartTradeFX.Create(transform.position, Quaternion.identity);
 		return false;
 	}
 
@@ -292,7 +292,7 @@
 
 	private void Say(string text, string trigger)
 	{
-		Chat.instance.SetNpcText(base.gameObject, Vector3.up * m_dialogHeight, 20f, m_hideDialogDelay, "", text, large: false);
+		Chat.instance.SetNpcText(gameObject, Vector3.up * m_dialogHeight, 20f, m_hideDialogDelay, "", text, large: false);
 		if (trigger.Length > 0)
 		{
 			m_animator.SetTrigger(trigger);
@@ -337,13 +337,13 @@
 	public void OnBought(TradeItem item)
 	{
 		Say(m_randomBuy, "Buy");
-		m_randomBuyFX.Create(base.transform.position, Quaternion.identity);
+		m_randomBuyFX.Create(transform.position, Quaternion.identity);
 	}
 
 	public void OnSold()
 	{
 		Say(m_randomSell, "Sell");
-		m_randomSellFX.Create(base.transform.position, Quaternion.identity);
+		m_randomSellFX.Create(transform.position, Quaternion.identity);
 	}
 
 	public List<TradeItem> GetAvailableItems()
```

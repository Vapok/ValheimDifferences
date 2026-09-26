# `Valheim.UI/SessionPlayerList.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/SessionPlayerList.cs
+++ b/Valheim.UI/SessionPlayerList.cs
@@ -59,10 +59,10 @@
 	{
 		if (m_loadBlockedList)
 		{
-			Canvas canvas = base.gameObject.AddComponent<Canvas>();
-			base.gameObject.AddComponent<CanvasScaler>();
-			base.gameObject.AddComponent<GuiScaler>();
-			base.gameObject.AddComponent<GraphicRaycaster>();
+			Canvas canvas = gameObject.AddComponent<Canvas>();
+			gameObject.AddComponent<CanvasScaler>();
+			gameObject.AddComponent<GuiScaler>();
+			gameObject.AddComponent<GraphicRaycaster>();
 			canvas.overrideSorting = true;
 			canvas.sortingOrder = 10;
 			SetBlockedEntries();
@@ -116,7 +116,7 @@
 	private void SetBlockedEntries()
 	{
 		_players = BlockList.Instance.BlockedPlayers.ToList();
-		base.transform.localScale = new Vector3(1f, 1f, 1f);
+		transform.localScale = new Vector3(1f, 1f, 1f);
 		_headerText.text = Localization.instance.Localize("$settings_blocked_player_list");
 		foreach (ZNet.PlayerInfo player in _players)
 		{
@@ -252,7 +252,7 @@
 
 	public void Close()
 	{
-		base.gameObject.SetActive(value: false);
+		gameObject.SetActive(value: false);
 	}
 
 	private void OnDisable()
@@ -263,7 +263,7 @@
 		}
 		MuteList.Instance.Persist();
 		BlockList.Instance.Persist();
-		Object.Destroy(base.gameObject);
+		Object.Destroy(gameObject);
 	}
 
 	private void Update()
```

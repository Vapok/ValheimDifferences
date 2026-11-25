# `TextsDialog.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `AddStats() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/TextsDialog.cs
+++ b/TextsDialog.cs
@@ -256,6 +256,7 @@
 	{
 		StringBuilder stringBuilder = new StringBuilder();
 		PlayerProfile playerProfile = Game.instance.GetPlayerProfile();
+		stringBuilder.AppendLine("Created: " + Game.instance.GetPlayerProfile().m_dateCreated.ToString("yyyy-MM-dd HH:mm:ss"));
 		if (playerProfile.m_usedCheats)
 		{
 			stringBuilder.AppendLine("Cheater!\n");
```

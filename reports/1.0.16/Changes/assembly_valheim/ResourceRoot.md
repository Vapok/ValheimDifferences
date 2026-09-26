# `ResourceRoot.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+9/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ResourceRoot.cs
+++ b/ResourceRoot.cs
@@ -44,7 +44,15 @@
 	public string GetHoverText()
 	{
 		float level = GetLevel();
-		string text = ((level > m_highThreshold) ? m_statusHigh : ((!(level > m_emptyTreshold)) ? m_statusEmpty : m_statusLow));
+		string text;
+		if (level > m_highThreshold)
+		{
+			text = m_statusHigh;
+		}
+		else
+		{
+			text = ((!(level > m_emptyTreshold)) ? m_statusEmpty : m_statusLow);
+		}
 		return Localization.instance.Localize(text);
 	}
 
```

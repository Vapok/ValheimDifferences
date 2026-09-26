# `Valheim.UI/GroupElement.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/GroupElement.cs
+++ b/Valheim.UI/GroupElement.cs
@@ -11,13 +11,13 @@
 	{
 		if (config == null)
 		{
-			base.Name = "";
-			base.Interact = null;
+			Name = "";
+			Interact = null;
 		}
 		else
 		{
-			base.Name = config.LocalizedName;
-			base.Interact = delegate
+			Name = config.LocalizedName;
+			Interact = () =>
 			{
 				radial.QueuedOpen(config, backConfig);
 				return true;
@@ -33,7 +33,7 @@
 		{
 			Hud.instance.StopCoroutine(m_colorChangeCoroutine);
 		}
-		m_colorChangeCoroutine = Hud.instance.StartCoroutine(ChangeColor(base.BackgroundMaterial.GetColor("_SelectedColor"), 0.1f));
+		m_colorChangeCoroutine = Hud.instance.StartCoroutine(ChangeColor(BackgroundMaterial.GetColor("_SelectedColor"), 0.1f));
 	}
 
 	public virtual void ChangeToDeselectColor()
```

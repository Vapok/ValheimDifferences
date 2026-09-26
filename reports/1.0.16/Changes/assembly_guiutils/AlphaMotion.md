# `AlphaMotion.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_guiutils.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/AlphaMotion.cs
+++ b/AlphaMotion.cs
@@ -13,6 +13,6 @@
 	private void Update()
 	{
 		float time = Time.time;
-		base.transform.localRotation = Quaternion.Euler(0f, 0f, Mathf.Sin(time * m_rotSpeed) * m_rotAngle);
+		transform.localRotation = Quaternion.Euler(0f, 0f, Mathf.Sin(time * m_rotSpeed) * m_rotAngle);
 	}
 }
```

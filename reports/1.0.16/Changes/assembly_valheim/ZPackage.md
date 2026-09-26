# `ZPackage.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZPackage.cs
+++ b/ZPackage.cs
@@ -315,7 +315,7 @@
 
 	public Vector3 ReadSmallRotation()
 	{
-		Vector3 vector = default(Vector3);
+		Vector3 vector = default;
 		uint num = m_reader.ReadUInt16();
 		if ((num & 0x8000) != 0)
 		{
```

# `SaveWithBackups.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `ClearSaveFiles() [Method Body Modified]`
- `EnsureSortedAndPrimaryFileDetermined() [Method Body Modified]`
- `RemoveSaveFile() [Method Body Modified]`
- `public void ClearSaveFiles()`

---

## 📝 Code Diff

```diff
--- a/SaveWithBackups.cs
+++ b/SaveWithBackups.cs
@@ -93,6 +93,13 @@
 		OnModified();
 	}
 
+	public void ClearSaveFiles()
+	{
+		m_saveFiles.Clear();
+		m_saveFilesByNameAndSource.Clear();
+		OnModified();
+	}
+
 	private void EnsureSortedAndPrimaryFileDetermined()
 	{
 		if (!m_isDirty)
```

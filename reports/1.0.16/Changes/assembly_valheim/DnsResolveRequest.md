# `DnsResolveRequest.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/DnsResolveRequest.cs
+++ b/DnsResolveRequest.cs
@@ -34,11 +34,11 @@
 	{
 		m_domainName = domainName;
 		m_worker = new BackgroundWorker();
-		m_worker.DoWork += delegate
+		m_worker.DoWork += (object sender, DoWorkEventArgs e) =>
 		{
 			m_succeeded = DnsResolver.URLToIP(m_domainName, out m_resolvedAddress);
 		};
-		m_worker.RunWorkerCompleted += delegate
+		m_worker.RunWorkerCompleted += (object sender, RunWorkerCompletedEventArgs e) =>
 		{
 			m_completed = true;
 			m_callback?.Invoke(this);
```

# `BrotliCompressor.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+9/-77` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `CompressBytes() [Method Body Modified]`
- `CompressFile() [Method Body Modified]`
- `CompressFile() [Method Removed]`
- `CompressStream() [Method Body Modified]`
- `CompressStream() [Method Removed]`
- `DecompressBytes() [Method Body Modified]`
- `DecompressFile() [Method Body Modified]`
- `DecompressFile() [Method Removed]`
- `DecompressStream() [Method Body Modified]`
- `DecompressStream() [Method Removed]`
- `GetCompressionLevel() [Method Body Modified]`
- `GetCompressionLevel() [Method Removed]`
- `private static CompressionLevel GetCompressionLevel()`
- `public static async Task CompressFileAsync(string originalFileName, string compressedFileName, CancellationToken cancel = default(CancellationToken))`
- `public static async Task CompressStreamAsync(Stream originalStream, Stream compressedStream, CancellationToken cancel = default(CancellationToken))`
- `public static async Task DecompressFileAsync(string compressedFileName, string outputFileName, CancellationToken cancel = default(CancellationToken))`
- `public static async Task DecompressStreamAsync(Stream compressedStream, Stream outputStream, CancellationToken cancel = default(CancellationToken))`
- `public static async Task<byte[]> CompressBytesAsync(byte[] bytes, CancellationToken cancel = default(CancellationToken))`
- `public static async Task<byte[]> DecompressBytesAsync(byte[] bytes, CancellationToken cancel = default(CancellationToken))`
- `public static void CompressFile(string originalFileName, string compressedFileName)`
- `public static void CompressStream(Stream originalStream, Stream compressedStream)`
- `public static void DecompressFile(string compressedFileName, string outputFileName)`
- `public static void DecompressStream(Stream compressedStream, Stream outputStream)`

---

## 📝 Code Diff

```diff
--- a/BrotliCompressor.cs
+++ b/BrotliCompressor.cs
@@ -1,94 +1,26 @@
-using System;
 using System.IO;
 using System.IO.Compression;
-using System.Threading;
-using System.Threading.Tasks;
 
 public static class BrotliCompressor
 {
-	private static CompressionLevel GetCompressionLevel()
-	{
-		if (Enum.IsDefined(typeof(CompressionLevel), 3))
-		{
-			return (CompressionLevel)3;
-		}
-		return CompressionLevel.Optimal;
-	}
-
 	public static byte[] CompressBytes(byte[] bytes)
 	{
-		return CompressBytesAsync(bytes).GetAwaiter().GetResult();
-	}
-
-	public static async Task<byte[]> CompressBytesAsync(byte[] bytes, CancellationToken cancel = default(CancellationToken))
-	{
-		using MemoryStream outputStream = new MemoryStream();
-		using (BrotliStream compressionStream = new BrotliStream(outputStream, GetCompressionLevel()))
+		using MemoryStream memoryStream = new MemoryStream();
+		using (BrotliStream brotliStream = new BrotliStream(memoryStream, CompressionLevel.Fastest))
 		{
-			await compressionStream.WriteAsync(bytes, 0, bytes.Length, cancel);
+			brotliStream.Write(bytes, 0, bytes.Length);
 		}
-		return outputStream.ToArray();
-	}
-
-	public static void CompressFile(string originalFileName, string compressedFileName)
-	{
-		CompressFileAsync(originalFileName, compressedFileName).GetAwaiter().GetResult();
-	}
-
-	public static async Task CompressFileAsync(string originalFileName, string compressedFileName, CancellationToken cancel = default(CancellationToken))
-	{
-		using FileStream originalStream = File.Open(originalFileName, FileMode.Open);
-		using FileStream compressedStream = File.Create(compressedFileName);
-		await CompressStreamAsync(originalStream, compressedStream, cancel);
-	}
-
-	public static void CompressStream(Stream originalStream, Stream compressedStream)
-	{
-		CompressStreamAsync(originalStream, compressedStream).GetAwaiter().GetResult();
-	}
-
-	public static async Task CompressStreamAsync(Stream originalStream, Stream compressedStream, CancellationToken cancel = default(CancellationToken))
-	{
-		using BrotliStream compressor = new BrotliStream(compressedStream, GetCompressionLevel());
-		await originalStream.CopyToAsync(compressor, cancel);
+		return memoryStream.ToArray();
 	}
 
 	public static byte[] DecompressBytes(byte[] bytes)
 	{
-		return DecompressBytesAsync(bytes).GetAwaiter().GetResult();
-	}
-
-	public static async Task<byte[]> DecompressBytesAsync(byte[] bytes, CancellationToken cancel = default(CancellationToken))
-	{
-		using MemoryStream inputStream = new MemoryStream(bytes);
-		using MemoryStream outputStream = new MemoryStream();
-		using (BrotliStream compressionStream = new BrotliStream(inputStream, CompressionMode.Decompress))
+		using MemoryStream stream = new MemoryStream(bytes);
+		using MemoryStream memoryStream = new MemoryStream();
+		using (BrotliStream brotliStream = new BrotliStream(stream, CompressionMode.Decompress))
 		{
-			await compressionStream.CopyToAsync(outputStream, cancel);
+			brotliStream.CopyTo(memoryStream);
 		}
-		return outputStream.ToArray();
-	}
-
-	public static void DecompressFile(string compressedFileName, string outputFileName)
-	{
-		DecompressFileAsync(compressedFileName, outputFileName).GetAwaiter().GetResult();
-	}
-
-	public static async Task DecompressFileAsync(string compressedFileName, string outputFileName, CancellationToken cancel = default(CancellationToken))
-	{
-		using FileStream compressedFileStream = File.Open(compressedFileName, FileMode.Open);
-		using FileStream outputFileStream = File.Create(outputFileName);
-		await DecompressStreamAsync(compressedFileStream, outputFileStream, cancel);
-	}
-
-	public static void DecompressStream(Stream compressedStream, Stream outputStream)
-	{
-		DecompressStreamAsync(compressedStream, outputStream).GetAwaiter().GetResult();
-	}
-
-	public static async Task DecompressStreamAsync(Stream compressedStream, Stream outputStream, CancellationToken cancel = default(CancellationToken))
-	{
-		using BrotliStream decompressor = new BrotliStream(compressedStream, CompressionMode.Decompress);
-		await decompressor.CopyToAsync(outputStream, cancel);
+		return memoryStream.ToArray();
 	}
 }
```

# `ZPackage.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+72/-76` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Clear() [Method Body Modified]`
- `Decompress() [Method Body Modified]`
- `Flush() [Method Body Modified]`
- `GetArray() [Method Body Modified]`
- `GetCompressed() [Method Body Modified]`
- `GetPos() [Method Body Modified]`
- `ReadZDOID() [Method Body Modified]`
- `SetPos() [Method Body Modified]`
- `Size() [Method Body Modified]`
- `Write() [Method Body Modified]`
- `WriteCompressed() [Method Body Modified]`
- `WriteNumItems() [Method Body Modified]`
- `WriteSmallRotation() [Method Body Modified]`
- `public byte[] GetCompressed()`
- `public int GetPos()`
- `public int Size()`
- `public void Decompress()`
- `public void Flush()`
- `public void SetPos(int pos)`
- `public void Write(byte[] array)`
- `public void WriteCompressed(ZPackage pkg)`

---

## 📝 Code Diff

```diff
--- a/ZPackage.cs
+++ b/ZPackage.cs
@@ -64,37 +64,36 @@
 
 	public void Write(ZPackage pkg)
 	{
-		byte[] array = pkg.GetArray();
+		pkg.Flush();
+		Write((int)pkg.m_stream.Length);
+		m_writer.Write(pkg.m_stream.GetBuffer(), 0, (int)pkg.m_stream.Length);
+	}
+
+	public void WriteCompressed(ZPackage pkg)
+	{
+		byte[] array = Utils.Compress(pkg.GetArray());
+		Write(array);
+	}
+
+	public byte[] GetCompressed()
+	{
+		return Utils.Compress(GetArray());
+	}
+
+	public void Decompress()
+	{
+		byte[] array = Utils.Decompress(GetArray());
+		m_stream.Position = 0L;
+		m_stream.Write(array, 0, array.Length);
+		m_stream.Position = 0L;
+	}
+
+	public void Write(byte[] array)
+	{
 		m_writer.Write(array.Length);
 		m_writer.Write(array);
 	}
 
-	public void WriteCompressed(ZPackage pkg)
-	{
-		byte[] array = Utils.Compress(pkg.GetArray());
-		m_writer.Write(array.Length);
-		m_writer.Write(array);
-	}
-
-	public byte[] GetCompressed()
-	{
-		return Utils.Compress(GetArray());
-	}
-
-	public void Decompress()
-	{
-		byte[] array = Utils.Decompress(GetArray());
-		m_stream.Position = 0L;
-		m_stream.Write(array, 0, array.Length);
-		m_stream.Position = 0L;
-	}
-
-	public void Write(byte[] array)
-	{
-		m_writer.Write(array.Length);
-		m_writer.Write(array);
-	}
-
 	public void Write(byte data)
 	{
 		m_writer.Write(data);
@@ -147,12 +146,12 @@
 
 	public void Write(float data)
 	{
-		m_writer.Write(data);
+		m_writer.Write(BitConverter.SingleToInt32Bits(data));
 	}
 
 	public void Write(double data)
 	{
-		m_writer.Write(data);
+		m_writer.Write(BitConverter.DoubleToInt64Bits(data));
 	}
 
 	public void Write(string data)
@@ -162,24 +161,23 @@
 
 	public void Write(ZDOID id)
 	{
-		m_writer.Write(id.UserID);
-		m_writer.Write(id.ID);
+		Write(id.UserID);
+		Write(id.ID);
 	}
 
 	public void Write(Vector3 v3)
 	{
-		m_writer.Write(v3.x);
-		m_writer.Write(v3.y);
-		m_writer.Write(v3.z);
+		Write(v3.x);
+		Write(v3.y);
+		Write(v3.z);
 	}
 
 	public void WriteSmallRotation(Vector3 v3)
 	{
-		v3 *= 2f;
-		uint num = (uint)v3.x;
-		uint num2 = (uint)v3.y;
-		uint num3 = (uint)v3.z;
-		if ((num <= 1 || num >= 719) && (num3 <= 1 || num3 >= 719))
+		uint num = Utils.QuantizeHalfDegrees(v3.x);
+		uint num2 = Utils.QuantizeHalfDegrees(v3.y);
+		uint num3 = Utils.QuantizeHalfDegrees(v3.z);
+		if (num == 0 && num3 == 0)
 		{
 			num2 |= 0x8000;
 			m_writer.Write((short)num2);
@@ -188,39 +186,39 @@
 		uint num4 = num;
 		num4 |= num2 << 10;
 		num4 |= num3 << 20;
-		m_writer.Write((ushort)(num4 >> 16));
-		m_writer.Write((ushort)num4);
+		Write((ushort)(num4 >> 16));
+		Write((ushort)num4);
 	}
 
 	public void Write(Vector2i v2)
 	{
-		m_writer.Write(v2.x);
-		m_writer.Write(v2.y);
+		Write(v2.x);
+		Write(v2.y);
 	}
 
 	public void Write(Vector2s v2)
 	{
-		m_writer.Write(v2.x);
-		m_writer.Write(v2.y);
+		Write(v2.x);
+		Write(v2.y);
 	}
 
 	public void Write(Quaternion q)
 	{
-		m_writer.Write(q.x);
-		m_writer.Write(q.y);
-		m_writer.Write(q.z);
-		m_writer.Write(q.w);
+		Write(q.x);
+		Write(q.y);
+		Write(q.z);
+		Write(q.w);
 	}
 
 	public void WriteNumItems(int numItems)
 	{
 		if (numItems < 128)
 		{
-			m_writer.Write((byte)numItems);
+			Write((byte)numItems);
 			return;
 		}
-		m_writer.Write((byte)((numItems >> 8) | 0x80));
-		m_writer.Write((byte)numItems);
+		Write((byte)((numItems >> 8) | 0x80));
+		Write((byte)numItems);
 	}
 
 	public ZDOID ReadZDOID()
@@ -399,32 +397,30 @@
 
 	public byte[] GetArray()
 	{
+		Flush();
+		return m_stream.ToArray();
+	}
+
+	public void SetPos(int pos)
+	{
+		m_stream.Position = pos;
+	}
+
+	public int GetPos()
+	{
+		return (int)m_stream.Position;
+	}
+
+	public int Size()
+	{
+		Flush();
+		return (int)m_stream.Length;
+	}
+
+	public void Flush()
+	{
 		m_writer.Flush();
 		m_stream.Flush();
-		return m_stream.ToArray();
-	}
-
-	public void SetPos(int pos)
-	{
-		m_stream.Position = pos;
-	}
-
-	public int GetPos()
-	{
-		return (int)m_stream.Position;
-	}
-
-	public int Size()
-	{
-		m_writer.Flush();
-		m_stream.Flush();
-		return (int)m_stream.Length;
-	}
-
-	public void Flush()
-	{
-		m_writer.Flush();
-		m_stream.Flush();
 	}
 
 	public void Clear()
```

# `ZDO.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+42/-42` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZDO.cs
+++ b/ZDO.cs
@@ -891,7 +891,7 @@
 		{
 			SetFlag(ref dataFlags, ExtraDataFlags.ByteArrays);
 		}
-		bool num = m_rotation != Quaternion.identity.eulerAngles;
+		bool flag = m_rotation != Quaternion.identity.eulerAngles;
 		if (Persistent)
 		{
 			SetFlag(ref dataFlags, ExtraDataFlags.Persistent);
@@ -901,13 +901,13 @@
 			SetFlag(ref dataFlags, ExtraDataFlags.Distant);
 		}
 		SetFlag(ref dataFlags, (ExtraDataFlags)((uint)Type << 10));
-		if (num)
+		if (flag)
 		{
 			SetFlag(ref dataFlags, ExtraDataFlags.Rotation);
 		}
 		pkg.Write((ushort)dataFlags);
 		pkg.Write(m_prefab);
-		if (num)
+		if (flag)
 		{
 			pkg.Write(m_rotation);
 		}
@@ -918,31 +918,31 @@
 				pkg.Write((byte)connectionData.m_type);
 				pkg.Write(connectionData.m_target);
 			}
-			ZDODataHelper.WriteData(pkg, floats, delegate(float value)
+			ZDODataHelper.WriteData(pkg, floats, (float value) =>
 			{
 				pkg.Write(value);
 			});
-			ZDODataHelper.WriteData(pkg, vec3s, delegate(Vector3 value)
+			ZDODataHelper.WriteData(pkg, vec3s, (Vector3 value) =>
 			{
 				pkg.Write(value);
 			});
-			ZDODataHelper.WriteData(pkg, quats, delegate(Quaternion value)
+			ZDODataHelper.WriteData(pkg, quats, (Quaternion value) =>
 			{
 				pkg.Write(value);
 			});
-			ZDODataHelper.WriteData(pkg, ints, delegate(int value)
+			ZDODataHelper.WriteData(pkg, ints, (int value) =>
 			{
 				pkg.Write(value);
 			});
-			ZDODataHelper.WriteData(pkg, longs, delegate(long value)
+			ZDODataHelper.WriteData(pkg, longs, (long value) =>
 			{
 				pkg.Write(value);
 			});
-			ZDODataHelper.WriteData(pkg, strings, delegate(string value)
+			ZDODataHelper.WriteData(pkg, strings, (string value) =>
 			{
 				pkg.Write(value);
 			});
-			ZDODataHelper.WriteData(pkg, byteArray, delegate(byte[] value)
+			ZDODataHelper.WriteData(pkg, byteArray, (byte[] value) =>
 			{
 				pkg.Write(value);
 			});
@@ -962,7 +962,7 @@
 		}
 		if (IsFlagSet(extraDataFlags, ExtraDataFlags.AnyLow8Bits))
 		{
-			bool num = IsFlagSet(extraDataFlags, ExtraDataFlags.Connections);
+			bool flag = IsFlagSet(extraDataFlags, ExtraDataFlags.Connections);
 			bool read = IsFlagSet(extraDataFlags, ExtraDataFlags.Floats);
 			bool read2 = IsFlagSet(extraDataFlags, ExtraDataFlags.Vec3);
 			bool read3 = IsFlagSet(extraDataFlags, ExtraDataFlags.Quaternions);
@@ -970,7 +970,7 @@
 			bool read5 = IsFlagSet(extraDataFlags, ExtraDataFlags.Longs);
 			bool read6 = IsFlagSet(extraDataFlags, ExtraDataFlags.Strings);
 			bool read7 = IsFlagSet(extraDataFlags, ExtraDataFlags.ByteArrays);
-			if (num)
+			if (flag)
 			{
 				ZDOExtraData.ConnectionType connectionType = (ZDOExtraData.ConnectionType)pkg.ReadByte();
 				ZDOID target = pkg.ReadZDOID();
@@ -1022,8 +1022,8 @@
 		{
 			SetFlag(ref dataFlags, ExtraDataFlags.ByteArrays);
 		}
-		bool num = !m_rotation.CloseToZero();
-		var (flag, v) = m_position.SmallPosition();
+		bool flag = !m_rotation.CloseToZero();
+		var (flag2, v) = m_position.SmallPosition();
 		if (Persistent)
 		{
 			SetFlag(ref dataFlags, ExtraDataFlags.Persistent);
@@ -1033,25 +1033,25 @@
 			SetFlag(ref dataFlags, ExtraDataFlags.Distant);
 		}
 		SetFlag(ref dataFlags, (ExtraDataFlags)((uint)Type << 10));
-		if (num)
+		if (flag)
 		{
 			SetFlag(ref dataFlags, ExtraDataFlags.Rotation);
 		}
+		if (flag2)
+		{
+			SetFlag(ref dataFlags, ExtraDataFlags.SmallPosition);
+		}
+		pkg.Write((ushort)dataFlags);
+		if (flag2)
+		{
+			pkg.Write(v);
+		}
+		else
+		{
+			pkg.Write(m_position);
+		}
+		pkg.Write(m_prefab);
 		if (flag)
-		{
-			SetFlag(ref dataFlags, ExtraDataFlags.SmallPosition);
-		}
-		pkg.Write((ushort)dataFlags);
-		if (flag)
-		{
-			pkg.Write(v);
-		}
-		else
-		{
-			pkg.Write(m_position);
-		}
-		pkg.Write(m_prefab);
-		if (num)
 		{
 			pkg.WriteSmallRotation(m_rotation);
 		}
@@ -1062,31 +1062,31 @@
 				pkg.Write((byte)connectionData.m_type);
 				pkg.Write(connectionData.m_hash);
 			}
-			ZDODataHelper.WriteToDisk(pkg, floats, delegate(float value)
+			ZDODataHelper.WriteToDisk(pkg, floats, (float value) =>
 			{
 				pkg.Write(value);
 			});
-			ZDODataHelper.WriteToDisk(pkg, vec3s, delegate(Vector3 value)
+			ZDODataHelper.WriteToDisk(pkg, vec3s, (Vector3 value) =>
 			{
 				pkg.Write(value);
 			});
-			ZDODataHelper.WriteToDisk(pkg, quats, delegate(Quaternion value)
+			ZDODataHelper.WriteToDisk(pkg, quats, (Quaternion value) =>
 			{
 				pkg.Write(value);
 			});
-			ZDODataHelper.WriteToDisk(pkg, ints, delegate(int value)
+			ZDODataHelper.WriteToDisk(pkg, ints, (int value) =>
 			{
 				pkg.Write(value);
 			});
-			ZDODataHelper.WriteToDisk(pkg, longs, delegate(long value)
+			ZDODataHelper.WriteToDisk(pkg, longs, (long value) =>
 			{
 				pkg.Write(value);
 			});
-			ZDODataHelper.WriteToDisk(pkg, strings, delegate(string value)
+			ZDODataHelper.WriteToDisk(pkg, strings, (string value) =>
 			{
 				pkg.Write(value);
 			});
-			ZDODataHelper.WriteToDisk(pkg, byteArray, delegate(byte[] value)
+			ZDODataHelper.WriteToDisk(pkg, byteArray, (byte[] value) =>
 			{
 				pkg.Write(value);
 			});
@@ -1305,13 +1305,13 @@
 		Persistent = IsFlagSet(extraDataFlags, ExtraDataFlags.Persistent);
 		Distant = IsFlagSet(extraDataFlags, ExtraDataFlags.Distant);
 		Type = (ObjectType)(((int)extraDataFlags >> 10) & 3);
-		bool num = IsFlagSet(extraDataFlags, ExtraDataFlags.SmallPosition);
-		bool flag2 = IsFlagSet(extraDataFlags, ExtraDataFlags.Rotation);
+		bool flag2 = IsFlagSet(extraDataFlags, ExtraDataFlags.SmallPosition);
+		bool flag3 = IsFlagSet(extraDataFlags, ExtraDataFlags.Rotation);
 		if (!flag)
 		{
 			pkg.ReadVector2s();
 		}
-		if (num)
+		if (flag2)
 		{
 			Vector2s vector2s = pkg.ReadVector2s();
 			m_position = new Vector3(vector2s.x, 0f, vector2s.y);
@@ -1321,13 +1321,13 @@
 			m_position = pkg.ReadVector3();
 		}
 		m_prefab = pkg.ReadInt();
-		if (flag2)
+		if (flag3)
 		{
 			m_rotation = (flag ? pkg.ReadSmallRotation() : pkg.ReadVector3());
 		}
 		if (IsFlagSet(extraDataFlags, ExtraDataFlags.AnyLow8Bits))
 		{
-			bool num2 = IsFlagSet(extraDataFlags, ExtraDataFlags.Connections);
+			bool flag4 = IsFlagSet(extraDataFlags, ExtraDataFlags.Connections);
 			bool read = IsFlagSet(extraDataFlags, ExtraDataFlags.Floats);
 			bool read2 = IsFlagSet(extraDataFlags, ExtraDataFlags.Vec3);
 			bool read3 = IsFlagSet(extraDataFlags, ExtraDataFlags.Quaternions);
@@ -1335,7 +1335,7 @@
 			bool read5 = IsFlagSet(extraDataFlags, ExtraDataFlags.Longs);
 			bool read6 = IsFlagSet(extraDataFlags, ExtraDataFlags.Strings);
 			bool read7 = IsFlagSet(extraDataFlags, ExtraDataFlags.ByteArrays);
-			if (num2)
+			if (flag4)
 			{
 				ZDOExtraData.ConnectionType connectionType = (ZDOExtraData.ConnectionType)pkg.ReadByte();
 				int hash = pkg.ReadInt();
```

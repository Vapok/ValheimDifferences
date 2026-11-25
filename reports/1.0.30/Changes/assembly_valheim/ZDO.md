# `ZDO.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+69/-46` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Clone() [Method Body Modified]`
- `Deserialize() [Method Body Modified]`
- `InternalSetPosition() [Method Body Modified]`
- `InvalidateSector() [Method Body Modified]`
- `Reset() [Method Body Modified]`
- `Serialize() [Method Body Modified]`
- `SetSector() [Method Body Modified]`
- `Update() [Method Body Modified]`
- `Update() [Method Removed]`
- `Write() [Method Body Modified]`
- `private static void Write(ZPackage pkg, Quaternion value)`
- `private static void Write(ZPackage pkg, Vector3 value)`
- `private static void Write(ZPackage pkg, byte[] value)`
- `private static void Write(ZPackage pkg, float value)`
- `private static void Write(ZPackage pkg, int value)`
- `private static void Write(ZPackage pkg, long value)`
- `private static void Write(ZPackage pkg, string value)`
- `private void SetSector(ZoneSystem.SectorIndex sectorIndex)`
- `private void SetSector(ZoneSystem.SectorIndex sectorIndex, ZoneSystem.SectorIndex oldSector)`
- `public void Update(int hash, Vector3 value)`

---

## 📝 Code Diff

```diff
--- a/ZDO.cs
+++ b/ZDO.cs
@@ -48,13 +48,29 @@
 		Terrain
 	}
 
+	private static readonly Vector3 c_quaternionIdentity = Quaternion.identity.eulerAngles;
+
+	private static readonly Action<ZPackage, float> WriteFloat = Write;
+
+	private static readonly Action<ZPackage, Vector3> WriteVec3 = Write;
+
+	private static readonly Action<ZPackage, Quaternion> WriteQuaternion = Write;
+
+	private static readonly Action<ZPackage, int> WriteInt = Write;
+
+	private static readonly Action<ZPackage, long> WriteLong = Write;
+
+	private static readonly Action<ZPackage, string> WriteString = Write;
+
+	private static readonly Action<ZPackage, byte[]> WriteByteArray = Write;
+
 	private const int c_PrefabInvalid = -1;
 
 	private const int c_PrefabNull = 0;
 
 	public ZDOID m_uid = ZDOID.None;
 
-	private Vector3 m_rotation = Quaternion.identity.eulerAngles;
+	private Vector3 m_rotation = c_quaternionIdentity;
 
 	private Vector3 m_position = Vector3.zero;
 
@@ -292,7 +308,7 @@
 		m_tempSortValue = 0f;
 		Valid = false;
 		m_position = Vector3.zero;
-		m_rotation = Quaternion.identity.eulerAngles;
+		m_rotation = c_quaternionIdentity;
 	}
 
 	public ZDO Clone()
@@ -365,14 +381,6 @@
 		}
 	}
 
-	public void Update(int hash, Vector3 value)
-	{
-		if (ZDOExtraData.Update(m_uid, hash, value))
-		{
-			IncreaseDataRevision();
-		}
-	}
-
 	public void Set(string name, Quaternion value)
 	{
 		Set(name.GetStableHashCode(), value);
@@ -481,8 +489,9 @@
 	{
 		if (!(m_position == pos))
 		{
-			SetSector(ZoneSystem.GetSectorIndex(pos));
+			ZoneSystem.SectorIndex sectorIndex = GetSectorIndex();
 			m_position = pos;
+			SetSector(GetSectorIndex(), sectorIndex);
 			if (IsOwner())
 			{
 				IncreaseDataRevision();
@@ -492,16 +501,16 @@
 
 	public void InvalidateSector()
 	{
-		SetSector(ZoneSystem.SectorZero);
-	}
-
-	private void SetSector(ZoneSystem.SectorIndex sectorIndex)
+		SetSector(ZoneSystem.SectorZero, GetSectorIndex());
+	}
+
+	private void SetSector(ZoneSystem.SectorIndex sectorIndex, ZoneSystem.SectorIndex oldSector)
 	{
 		if (Game.instance.PortalPrefabHash.Contains(GetPrefab()))
 		{
 			return;
 		}
-		ZoneSystem.SectorIndex sectorIndex2 = (OutsideZones ? ZoneSystem.SectorZero : GetSectorIndex());
+		ZoneSystem.SectorIndex sectorIndex2 = (OutsideZones ? ZoneSystem.SectorZero : oldSector);
 		if (!(sectorIndex2 == sectorIndex))
 		{
 			ZDOMan.instance.RemoveFromSector(this, sectorIndex2);
@@ -891,7 +900,7 @@
 		{
 			SetFlag(ref dataFlags, ExtraDataFlags.ByteArrays);
 		}
-		bool flag = m_rotation != Quaternion.identity.eulerAngles;
+		bool flag = m_rotation != c_quaternionIdentity;
 		if (Persistent)
 		{
 			SetFlag(ref dataFlags, ExtraDataFlags.Persistent);
@@ -918,35 +927,49 @@
 				pkg.Write((byte)connectionData.m_type);
 				pkg.Write(connectionData.m_target);
 			}
-			ZDODataHelper.WriteData(pkg, floats, (float value) =>
-			{
-				pkg.Write(value);
-			});
-			ZDODataHelper.WriteData(pkg, vec3s, (Vector3 value) =>
-			{
-				pkg.Write(value);
-			});
-			ZDODataHelper.WriteData(pkg, quats, (Quaternion value) =>
-			{
-				pkg.Write(value);
-			});
-			ZDODataHelper.WriteData(pkg, ints, (int value) =>
-			{
-				pkg.Write(value);
-			});
-			ZDODataHelper.WriteData(pkg, longs, (long value) =>
-			{
-				pkg.Write(value);
-			});
-			ZDODataHelper.WriteData(pkg, strings, (string value) =>
-			{
-				pkg.Write(value);
-			});
-			ZDODataHelper.WriteData(pkg, byteArray, (byte[] value) =>
-			{
-				pkg.Write(value);
-			});
-		}
+			ZDODataHelper.WriteData(pkg, floats, WriteFloat);
+			ZDODataHelper.WriteData(pkg, vec3s, WriteVec3);
+			ZDODataHelper.WriteData(pkg, quats, WriteQuaternion);
+			ZDODataHelper.WriteData(pkg, ints, WriteInt);
+			ZDODataHelper.WriteData(pkg, longs, WriteLong);
+			ZDODataHelper.WriteData(pkg, strings, WriteString);
+			ZDODataHelper.WriteData(pkg, byteArray, WriteByteArray);
+		}
+	}
+
+	private static void Write(ZPackage pkg, float value)
+	{
+		pkg.Write(value);
+	}
+
+	private static void Write(ZPackage pkg, Vector3 value)
+	{
+		pkg.Write(value);
+	}
+
+	private static void Write(ZPackage pkg, Quaternion value)
+	{
+		pkg.Write(value);
+	}
+
+	private static void Write(ZPackage pkg, int value)
+	{
+		pkg.Write(value);
+	}
+
+	private static void Write(ZPackage pkg, long value)
+	{
+		pkg.Write(value);
+	}
+
+	private static void Write(ZPackage pkg, string value)
+	{
+		pkg.Write(value);
+	}
+
+	private static void Write(ZPackage pkg, byte[] value)
+	{
+		pkg.Write(value);
 	}
 
 	public void Deserialize(ZPackage pkg)
```

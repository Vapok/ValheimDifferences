# `DistantFogEmitter.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/DistantFogEmitter.cs
+++ b/DistantFogEmitter.cs
@@ -72,7 +72,7 @@
 
 	private void PlaceOne()
 	{
-		if (GetRandomPoint(base.transform.position, out var p))
+		if (GetRandomPoint(transform.position, out var p))
 		{
 			ParticleSystem.EmitParams emitParams = new ParticleSystem.EmitParams
 			{
```

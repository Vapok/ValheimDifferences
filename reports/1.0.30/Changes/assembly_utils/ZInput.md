# `ZInput.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+10/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `ApplyDeadzoneFloat() [Method Body Modified]`
- `ApplyDeadzoneToMagnitude() [Method Body Modified]`
- `ApplyDeadzoneVector() [Method Body Modified]`
- `GetScrollModifier() [Method Body Modified]`
- `m_stickDeadZone [Field Removed, was float]`
- `private void ApplyDeadzoneToMagnitude(ref float magnitude)`
- `private void ApplyDeadzoneToMagnitude(ref float magnitude, float deadzone)`

---

## 📝 Code Diff

```diff
--- a/ZInput.cs
+++ b/ZInput.cs
@@ -307,7 +307,11 @@
 
 	private const bool c_EmoteOnlyMode = false;
 
-	private const float m_stickDeadZone = 0.2f;
+	private const float c_deadZone1D = 0.2f;
+
+	private static readonly float s_deadZone2D = Mathf.Sqrt(0.080000006f);
+
+	private const float c_TriggerDeadZone = 0.2f;
 
 	private const float m_axisPressDeadZone = 0.4f;
 
@@ -2615,20 +2619,20 @@
 	{
 		float num = Mathf.Sign(value);
 		value = Mathf.Abs(value);
-		ApplyDeadzoneToMagnitude(ref value);
+		ApplyDeadzoneToMagnitude(ref value, 0.2f);
 		return value * num;
 	}
 
 	private Vector2 ApplyDeadzoneVector(Vector2 value)
 	{
 		float magnitude = value.magnitude;
-		ApplyDeadzoneToMagnitude(ref magnitude);
+		ApplyDeadzoneToMagnitude(ref magnitude, s_deadZone2D);
 		return value.normalized * magnitude;
 	}
 
-	private void ApplyDeadzoneToMagnitude(ref float magnitude)
-	{
-		magnitude = Mathf.Clamp01((magnitude - 0.2f) / 0.8f);
+	private void ApplyDeadzoneToMagnitude(ref float magnitude, float deadzone)
+	{
+		magnitude = Mathf.Clamp01((magnitude - deadzone) / (1f - deadzone));
 	}
 
 	private static float GetScrollModifier()
```

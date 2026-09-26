# `Valheim.UI/RadialMenuAnimationManager.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+14/-14` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/RadialMenuAnimationManager.cs
+++ b/Valheim.UI/RadialMenuAnimationManager.cs
@@ -86,15 +86,15 @@
 
 		private void SharedInit(string id, T targetValue, float duration, Action onEnd, Action onTick = null)
 		{
-			base.ID = id;
-			base.Active = false;
+			ID = id;
+			Active = false;
 			_targetValue = targetValue;
 			_duration = duration;
 			_elapsedTime = 0f;
 			OnEnd = onEnd;
 			OnTick = onTick;
 			_hasInitialized = true;
-			base.HasEndAction = onEnd != null;
+			HasEndAction = onEnd != null;
 		}
 
 		protected void InitInternal(string id, T targetValue, Func<T> get, Action<T> set, float duration = 1f, Action onEnd = null, Action onTick = null)
@@ -112,13 +112,13 @@
 			}
 			else
 			{
-				base.Active = true;
+				Active = true;
 			}
 		}
 
 		public override void Tick(float deltaTime)
 		{
-			if (!base.Active)
+			if (!Active)
 			{
 				return;
 			}
@@ -136,7 +136,7 @@
 			}
 			catch
 			{
-				base.Active = false;
+				Active = false;
 			}
 		}
 
@@ -152,7 +152,7 @@
 			catch
 			{
 			}
-			base.Active = false;
+			Active = false;
 		}
 	}
 
@@ -282,7 +282,7 @@
 
 		protected override float UpdateValue()
 		{
-			return Mathf.SmoothDamp(GetValue(), _targetValue, ref _velocity, base.SmoothTime);
+			return Mathf.SmoothDamp(GetValue(), _targetValue, ref _velocity, SmoothTime);
 		}
 	}
 
@@ -296,7 +296,7 @@
 
 		protected override Vector2 UpdateValue()
 		{
-			return Vector2.SmoothDamp(GetValue(), _targetValue, ref _velocity, base.SmoothTime);
+			return Vector2.SmoothDamp(GetValue(), _targetValue, ref _velocity, SmoothTime);
 		}
 	}
 
@@ -310,7 +310,7 @@
 
 		protected override Vector3 UpdateValue()
 		{
-			return Vector3.SmoothDamp(GetValue(), _targetValue, ref _velocity, base.SmoothTime);
+			return Vector3.SmoothDamp(GetValue(), _targetValue, ref _velocity, SmoothTime);
 		}
 	}
 
@@ -384,7 +384,7 @@
 
 	public void CancelTweens(string id)
 	{
-		CancelOrPauseTweens(id, delegate(Tween tween)
+		CancelOrPauseTweens(id, (Tween tween) =>
 		{
 			tween.Cancel();
 		});
@@ -396,7 +396,7 @@
 
 	public void EndTweens(string id)
 	{
-		CancelOrPauseTweens(id, delegate(Tween tween)
+		CancelOrPauseTweens(id, (Tween tween) =>
 		{
 			tween.End();
 		});
@@ -408,7 +408,7 @@
 
 	public void PauseTweens(string id)
 	{
-		CancelOrPauseTweens(id, delegate(Tween tween)
+		CancelOrPauseTweens(id, (Tween tween) =>
 		{
 			tween.Pause();
 		});
@@ -416,7 +416,7 @@
 
 	public void UnPauseTweens(string id)
 	{
-		CancelOrPauseTweens(id, delegate(Tween tween)
+		CancelOrPauseTweens(id, (Tween tween) =>
 		{
 			tween.UnPause();
 		});
```

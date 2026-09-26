# `CensorShittyWords.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+18/-18` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CensorShittyWords.cs
+++ b/CensorShittyWords.cs
@@ -212,8 +212,8 @@
 		{
 			GenerateNormalizedLists();
 		}
-		bool num = FilterInternal(input, out output);
-		if (num)
+		bool flag = FilterInternal(input, out output);
+		if (flag)
 		{
 			cachedCensored.Add(input, output);
 		}
@@ -222,7 +222,7 @@
 			cachedNotCensored.Add(input);
 		}
 		cacheMiss = true;
-		return num;
+		return flag;
 		static bool FilterInternal(string text, out string reference)
 		{
 			string thisString = Normalize(text);
@@ -298,24 +298,24 @@
 			{
 				for (int n = 0; n < item4.Value.Count; n++)
 				{
-					for (int num2 = 0; num2 < item4.Key.Length; num2++)
-					{
-						array4[item4.Value[n] + num2] = true;
+					for (int num = 0; num < item4.Key.Length; num++)
+					{
+						array4[item4.Value[n] + num] = true;
 					}
 				}
 			}
 			char[] array5 = new char[text.Length];
 			bool result = false;
-			for (int num3 = 0; num3 < text.Length; num3++)
-			{
-				if (array4[num3] && text[num3] != ' ')
-				{
-					array5[num3] = '*';
+			for (int num2 = 0; num2 < text.Length; num2++)
+			{
+				if (array4[num2] && text[num2] != ' ')
+				{
+					array5[num2] = '*';
 					result = true;
 				}
 				else
 				{
-					array5[num3] = text[num3];
+					array5[num2] = text[num2];
 				}
 			}
 			reference = new string(array5);
@@ -472,7 +472,7 @@
 
 	public static string FilterUGC(string text, UGCType ugcType, long playerId)
 	{
-		return FilterUGC(text, ugcType, default(PlatformUserID), playerId);
+		return FilterUGC(text, ugcType, default, playerId);
 	}
 
 	public static string FilterUGC(string text, UGCType ugcType = UGCType.Other, PlatformUserID userId = default(PlatformUserID), long playerId = 0L, GetUserProfileCompletedHandler completedHandler = null)
@@ -567,9 +567,9 @@
 		}
 		if (!userId.IsValid)
 		{
-			PrivilegeResult num = PlatformManager.DistributionPlatform.PrivilegeProvider.CheckPrivilege(GetPrivilegeFromUGCType(ugcType));
+			PrivilegeResult privilegeResult = PlatformManager.DistributionPlatform.PrivilegeProvider.CheckPrivilege(GetPrivilegeFromUGCType(ugcType));
 			allowAttemptResolve = true;
-			if (num == PrivilegeResult.Granted)
+			if (privilegeResult == PrivilegeResult.Granted)
 			{
 				return UGCFilteringMethod.Censored;
 			}
@@ -591,9 +591,9 @@
 		}
 		if (PlatformManager.DistributionPlatform.RelationsProvider == null)
 		{
-			PrivilegeResult num2 = PlatformManager.DistributionPlatform.PrivilegeProvider.CheckPrivilege(Privilege.ViewUserGeneratedContent);
+			PrivilegeResult privilegeResult2 = PlatformManager.DistributionPlatform.PrivilegeProvider.CheckPrivilege(Privilege.ViewUserGeneratedContent);
 			allowAttemptResolve = true;
-			if (num2 != PrivilegeResult.Granted)
+			if (privilegeResult2 != PrivilegeResult.Granted)
 			{
 				return UGCFilteringMethod.BlockedByPrivilege;
 			}
@@ -635,7 +635,7 @@
 		else if (UnifiedPopup.IsAvailable())
 		{
 			ugcNotificationShown = true;
-			UnifiedPopup.Push(new WarningPopup("$menu_ugcwarningheader", "$menu_ugcwarningtext", delegate
+			UnifiedPopup.Push(new WarningPopup("$menu_ugcwarningheader", "$menu_ugcwarningtext", () =>
 			{
 				UnifiedPopup.Pop();
 			}));
```

# `Minimap.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Minimap.cs
+++ b/Minimap.cs
@@ -544,10 +544,10 @@
 		m_mapSmallShader.SetTexture("_FogTex", m_fogTexture);
 		m_nameInput.gameObject.SetActive(value: false);
 		UIInputHandler component = m_mapImageLarge.GetComponent<UIInputHandler>();
-		component.m_onRightClick = (Action<UIInputHandler>)Delegate.Combine(component.m_onRightClick, (Action<UIInputHandler>)delegate
+		component.m_onRightClick = (Action<UIInputHandler>)Delegate.Combine(component.m_onRightClick, (Action<UIInputHandler>)((UIInputHandler _) =>
 		{
 			RemovePinUnderPointer();
-		});
+		}));
 		component.m_onMiddleClick = (Action<UIInputHandler>)Delegate.Combine(component.m_onMiddleClick, new Action<UIInputHandler>(OnMapMiddleClick));
 		component.m_onLeftDown = (Action<UIInputHandler>)Delegate.Combine(component.m_onLeftDown, new Action<UIInputHandler>(OnMapLeftDown));
 		component.m_onLeftUp = (Action<UIInputHandler>)Delegate.Combine(component.m_onLeftUp, new Action<UIInputHandler>(OnMapLeftUp));
```

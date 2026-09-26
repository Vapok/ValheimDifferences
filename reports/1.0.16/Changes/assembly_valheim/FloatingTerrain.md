# `FloatingTerrain.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/FloatingTerrain.cs
+++ b/FloatingTerrain.cs
@@ -53,7 +53,7 @@
 			m_targetOffset = 0f;
 			return;
 		}
-		m_targetOffset = m_lastHeightmap.GetHeightOffset(base.transform.position) + m_padding;
+		m_targetOffset = m_lastHeightmap.GetHeightOffset(transform.position) + m_padding;
 		if (!m_dummy)
 		{
 			GameObject gameObject = new GameObject();
@@ -81,8 +81,8 @@
 				m_dummyCollider.center = Vector3.Scale(m_collider.center, m_collider.transform.localScale);
 				m_dummyCollider.center -= m_collider.transform.localPosition;
 			}
-			gameObject.transform.parent = base.transform.parent;
-			gameObject.transform.position = base.transform.position;
+			gameObject.transform.parent = transform.parent;
+			gameObject.transform.position = transform.position;
 			m_collider.isTrigger = true;
 			UnityEngine.Object.Destroy(m_body);
 		}
@@ -101,8 +101,8 @@
 				m_waveTime += Time.fixedDeltaTime;
 				num += Mathf.Cos(m_waveTime * m_waveFreq) * m_waveAmp;
 			}
-			base.transform.position = m_dummy.transform.position + new Vector3(0f, num, 0f);
-			base.transform.rotation = m_dummy.transform.rotation;
+			transform.position = m_dummy.transform.position + new Vector3(0f, num, 0f);
+			transform.rotation = m_dummy.transform.rotation;
 		}
 	}
 
@@ -140,7 +140,7 @@
 		}
 		if (m_dummy != null)
 		{
-			Gizmos.DrawLine(base.transform.position, base.transform.position + new Vector3(0f, m_currentOffset, 0f));
+			Gizmos.DrawLine(transform.position, transform.position + new Vector3(0f, m_currentOffset, 0f));
 		}
 	}
 
```

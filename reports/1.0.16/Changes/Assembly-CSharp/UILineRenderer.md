# `UILineRenderer.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `Assembly-CSharp.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UILineRenderer.cs
+++ b/UILineRenderer.cs
@@ -35,22 +35,22 @@
 		UIVertex simpleVert = UIVertex.simpleVert;
 		simpleVert.color = color;
 		simpleVert.position = quaternion * new Vector3((0f - thickness) * 0.5f, 0f);
-		simpleVert.position += base.transform.InverseTransformPoint(line.Start.position);
+		simpleVert.position += transform.InverseTransformPoint(line.Start.position);
 		vh.AddVert(simpleVert);
 		UIVertex simpleVert2 = UIVertex.simpleVert;
 		simpleVert2.color = color;
 		simpleVert2.position = quaternion * new Vector3(thickness * 0.5f, 0f);
-		simpleVert2.position += base.transform.InverseTransformPoint(line.Start.position);
+		simpleVert2.position += transform.InverseTransformPoint(line.Start.position);
 		vh.AddVert(simpleVert2);
 		UIVertex simpleVert3 = UIVertex.simpleVert;
 		simpleVert3.color = color;
 		simpleVert3.position = quaternion * new Vector3((0f - thickness) * 0.5f, 0f);
-		simpleVert3.position += base.transform.InverseTransformPoint(line.End.position);
+		simpleVert3.position += transform.InverseTransformPoint(line.End.position);
 		vh.AddVert(simpleVert3);
 		UIVertex simpleVert4 = UIVertex.simpleVert;
 		simpleVert4.color = color;
 		simpleVert4.position = quaternion * new Vector3(thickness * 0.5f, 0f);
-		simpleVert4.position += base.transform.InverseTransformPoint(line.End.position);
+		simpleVert4.position += transform.InverseTransformPoint(line.End.position);
 		vh.AddVert(simpleVert4);
 		int num = index * 4;
 		vh.AddTriangle(num, num + 1, num + 3);
```

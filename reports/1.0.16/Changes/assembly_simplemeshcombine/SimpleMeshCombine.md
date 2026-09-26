# `SimpleMeshCombine.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_simplemeshcombine.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SimpleMeshCombine.cs
+++ b/SimpleMeshCombine.cs
@@ -44,7 +44,7 @@
 	{
 		MeshFilter[] array = null;
 		int num = 0;
-		array = base.transform.GetComponentsInChildren<MeshFilter>();
+		array = transform.GetComponentsInChildren<MeshFilter>();
 		for (int i = 0; i < array.Length; i++)
 		{
 			if (array[i].GetComponent<MeshRenderer>() != null && array[i].GetComponent<MeshRenderer>().enabled)
@@ -68,7 +68,7 @@
 	public void CombineMeshes()
 	{
 		GameObject gameObject = new GameObject();
-		gameObject.name = "_Combined Mesh [" + base.name + "]";
+		gameObject.name = "_Combined Mesh [" + name + "]";
 		gameObject.gameObject.AddComponent<MeshFilter>();
 		gameObject.gameObject.AddComponent<MeshRenderer>();
 		MeshFilter[] array = null;
@@ -117,7 +117,7 @@
 			CombineInstance[] combine = (arrayList2[k] as ArrayList).ToArray(typeof(CombineInstance)) as CombineInstance[];
 			array2[k] = new Mesh();
 			array2[k].CombineMeshes(combine, mergeSubMeshes: true, useMatrices: true);
-			array3[k] = default(CombineInstance);
+			array3[k] = default;
 			array3[k].mesh = array2[k];
 			array3[k].subMeshIndex = 0;
 		}
@@ -141,7 +141,7 @@
 		meshRenderer.materials = materials;
 		combined = gameObject.gameObject;
 		EnableRenderers(e: false);
-		gameObject.transform.parent = base.transform;
+		gameObject.transform.parent = transform;
 		gameObject.GetComponent<MeshFilter>().sharedMesh.RecalculateBounds();
 		vCount = gameObject.GetComponent<MeshFilter>().sharedMesh.vertexCount;
 		if (vCount > 65536)
```

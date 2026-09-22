# Valheim Differences

An automated archive of Valheim game version comparisons, assembly decompilation diffs, Unity asset/prefab evolution, and Harmony Transpiler safety audits.

Maintained by **[Vapok](https://github.com/Vapok)**.

---

## 📚 Version Comparison Archive

| Version | Assemblies Modified | Game Classes Changed | Unity Assets Changed | Transpiler Safety |
| :---: | :---: | :---: | :---: | :---: |
| [**`1.0.15`**](reports/1.0.15/Valheim_Diff.md) | `1` | `6` modified | [`6` assets](reports/1.0.15/Changes/assets/Valheim_Assets_Diff.md) | `11` Safe |
| [**`1.0.14`**](reports/1.0.14/Valheim_Diff.md) | `2` | `32` modified | - | `16` Safe / `⚠️ 1` Caution |

---

## 🛠️ How Diffs Are Generated

Diffs and audits in this repository are produced automatically using the [`valheim_diff.py`](https://github.com/Vapok) workspace utility:
1. **Decompilation**: Full decompilation of all game assemblies (`assembly_valheim.dll`, `assembly_guiutils.dll`, `assembly_utils.dll`, `Assembly-CSharp.dll`, etc.) via `ilspycmd`.
2. **Modular C# Diffs**: Clean per-class diff Markdown files structured under `reports/<Version>/Changes/<Assembly>/<Class>.md`.
3. **Transpiler IL Safety Audits**: Method-level and bytecode-level verification of all Harmony Transpilers to ensure vanilla hook points remain intact across patches.
4. **Workspace Mod Impact Scoring**: Cross-referencing changed game methods against mod patches to flag breaking API shifts before testing.
5. **Unity Asset & Prefab Diffs**: Automated headless extraction of ~5,000 prefabs, components, recipes, and status effects from dedicated server instances, paired with AI-driven difference commentary in `reports/<Version>/Changes/assets/`.

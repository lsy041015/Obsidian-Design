# CAD 시각화·문서화 매뉴얼 압축 규칙

Apply this reference only to relevant CAD/STL/URDF or project-specific robotics documentation. Numeric tolerances, artifact budgets, metadata, and section layouts below are project conventions, not general Markdown requirements. Follow the user's requested scope and current project conventions; verify applicability before using an old default. Read the source manual only when its exact conventions are needed and the file is available. If unavailable, disclose that limit when material; do not claim it was checked or block unrelated documentation.

Source of truth:

`<vault-root>/path/to/CAD-visualization-documentation-manual.md`

The placeholder denotes a manual in the active vault or project. Resolve it before use; never assume a host-specific absolute path. Read the source when exact local conventions matter. This file routes the high-risk rules only.

## Pipeline

`원본 STL → numpy parse → component/plane/boundary measurement → crop → reduction → int16+gzip+base64 → inline Three.js viewer → screenshots → Obsidian`

Keep original geometry untouched. Measurements always use original geometry. Reduced mesh is for viewing.

## STL and measurement

- Binary STL: verify `size == 84 + 50 * triangle_count`; do not `.view()` ASCII as binary.
- Recompute normals from vertices; do not trust stored normals.
- Weld STL vertices before topology operations; typical tolerance `0.05 mm` only when justified.
- For boundary loops, combine `r_std/r_mean` with material-area versus outer-bbox-area cross-check.
- If a loop is ambiguous, plot the actual plane triangles as a polygon.
- Record bbox, triangle count, source hash, frame, units, and measurement tolerance.

## URDF

- Write mount URDF by hand only for measured values, frame conventions, and `calibration:` comments.
- Reuse the existing dual generator; do not copy generators for each rig.
- Validate one root, unique parents, link/joint counts, mount frame, joint1 axis, bolt points, limits, and left/right symmetry.
- Use `1 µm` validation tolerance; do not use unrealistic `1e-9` tolerance for rounded rpy.
- After generator changes, compare regenerated output byte-for-byte.
- FK-bake link meshes to preview STL and reuse viewer pipeline.

## Viewer and artifact

- HTML artifact budget: `16 MB`.
- Prefer indexed int16 geometry + gzip + base64; record quantization origin/scale.
- Pad typed-array payload so index offset is 4-byte aligned; store `indexOffset` in metadata.
- For local files, decompress with `new Response(bin).body`, not a Blob stream that may fail on `file://`.
- Use inline unminified `three.module.js` when class names must remain available in the same module.
- Use `DoubleSide`, recomputed normals, corrected Z-up/Y-up rotation, centered origin, and floor from the model bbox.
- Generate deterministic 4 views plus 2 detail cuts. Capture model revision and camera purpose.

## Dimension drawings

- Use matplotlib `Agg`; keep 3D in Three.js and 2D dimensions in matplotlib.
- Draw dimensions over measured face triangles, not hand-sketched geometry.
- Use equal aspect, axis-direction labels, semantic colors, `bbox_inches="tight"`, `dpi=150`, white background.

## Obsidian

- Use frontmatter with graph metadata, tags, date, repo/branch, source, status, project, and parent note.
- Use standard Markdown image embeds under `assets/`, not wiki image embeds.
- Caption each image with one italic line describing view and key observation.
- Preferred sections: `0 Summary`, `1 Target`, `2 Measurement`, `3 Design`, `4 Results`, `5 Outputs`, `6 Validation`, `7 Unknowns`, `8 Next steps`.
- Use `warning` for unsafe/untrusted/uncertain values, `note` for corrections/tolerances, `tip` for reusable shortcuts, and `info` for missing measurements.
- Never silently delete an earlier wrong measurement; record what was wrong and the cross-check that corrected it.
- Record exact commands and artifact paths. Do not claim a result without its output.

## Required checklist

- [ ] Original source format, hash, triangle count, bbox
- [ ] Coordinate frame and units
- [ ] Component, plane, boundary-loop, and area cross-check
- [ ] Mount URDF calibration and generator regression
- [ ] URDF frame/bolt/axis/symmetry assertions
- [ ] FK preview and deterministic screenshots
- [ ] Dimension drawing from measured geometry
- [ ] Obsidian frontmatter, assets, captions, callouts
- [ ] Reproduction commands and unresolved items

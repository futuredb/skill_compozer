# Materials, reference description, and code handoff

Read this alongside the reconstruction contract before analyzing a reference. The material workflow applies to every reconstruction. Save the handoff and actual code by default in the current workspace.

## Evidence before parameters

A screenshot determines appearance, not a unique source construction. Separate observed facts, inferred implementation, and unavailable information. Do not assign numerical confidence without a measurement model. Use high / medium / low confidence with a short evidence statement. Similar foreground and background hues alone establish neither transparency nor opacity.

Inspect the whole screen and matched crops at native size and enlarged scale. Calibrate screenshot pixels to source-frame pixels before estimating effect widths. Enlarging a crop does not recover missing detail. If editable original layers are available, inspect their actual paints/effects first and distinguish those values from estimates derived from pixels.

For each visually important surface, record an ordered material recipe:

- underlying background and relevant content behind the surface;
- base fills, gradient types, stops with alpha, centers, handles, axes and coordinate units;
- tint, fill alpha, blend mode, and separate node opacity;
- background blur versus layer blur, target layer and estimated radius;
- border alignment, width, color/alpha, edge highlights and inner shadows;
- outer shadows or glow with offset, radius, spread, color/alpha;
- mask, clipping bounds, corner geometry, and front-to-back relationships.

Include only supported contributions. A glass label is not a recipe. Test glass against an opaque gradient alternative: does recognizable content continue behind it, lose contrast or sharpness inside it, and change with the underlying background? Preserve sharp foreground labels. A bright rim can be a stroke, highlight, or inner effect; inspect its direction and falloff rather than adding all three.

For gradients, locate color maxima and transition geometry across the whole surface before tuning stops. Distinct blooms may require several radial layers. For shadows, compare the contour and falloff on multiple edges, separate contact shadow from broad ambient shadow only when both are visible. A screenshot cannot reliably prove refraction, noise, or hidden backgrounds; mark these unknown instead of inventing them.

## Blur, glass and gradient borders

Reconstruct visible effects rather than adding them by style association. For blur, identify which pixels are softened, the blur boundary and clipping, and whether the effect acts on the layer or content behind it. Calibrate against the reconstructed background at the reference viewport; a nominal radius alone is not evidence of a match. Keep text and icons outside a blurred surface layer when they are sharp in the source.

For glass, tune background continuity, tint/alpha, backdrop blur, edge highlights and shadows independently. Preserve background detail visible through the surface and the reference's contrast loss. A translucent flat fill or opaque gradient alone does not pass when the source shows blurred content behind glass. Do not invent refraction or noise without visible evidence. Verify backdrop effects with the real stacking and clipping in the target browser; document a fallback and its visual difference if unsupported.

Reconstruct linear, radial, elliptical, conic or layered gradient fields according to their visible transitions. Match direction, center, extent, stop positions, color and alpha; preserve off-center or asymmetric blooms. Do not replace a multi-layer field with a generic two-stop diagonal gradient.

Treat a gradient border as its own paint: record thickness, contour, gradient direction, stops/alpha and any edge-dependent highlight. Use layered backgrounds for suitable opaque surfaces, or a separate masked border layer / SVG stroke for transparent and complex surfaces. Keep the interior truly transparent when the reference requires it; do not simulate a hollow border with a solid center that hides the backdrop. Align inner and outer contours, including smoothed corners and custom paths. Verify border continuity, clipping and compositing at corners and along rotated edges in the browser. Distinguish a gradient stroke from a glow or blurred highlight by edge sharpness and falloff.

## Candidate and render loop

For an ambiguous, prominent material, compare two plausible recipes on the same reconstructed background. Start with background and geometry, then fills, translucency and blur, then borders/highlights and shadows. Change one parameter family per comparison. Prefer the simplest recipe that explains the visible evidence; retain the rejected alternative and reason in the handoff when uncertainty matters.

Inspect equal-size source/output crops and the whole screen. Check color-field topology, edge sharpness, background visibility, shadow falloff, clipping and foreground contrast separately. Use overlays or difference images when available, but exclude intentional system-UI omissions and substituted media from fidelity claims. Never interpret a single whole-screen similarity score as proof of correct effects.

Treat a visually dominant material as an early acceptance criterion, alongside layout and typography. Do not defer it to final polish. After three correction passes without meaningful improvement, record the remaining mismatch and likely limitation rather than looping indefinitely or declaring a match.

## Shared reference package

Save each reference under `reference-packs/<stable-reference-id>/`, preserving previous versions and unrelated files. Use `reference.md` for a concise human-readable handoff and `reference.json` for the same model in structured form. Include an original image/export when accessible and authorized; otherwise keep the source link and mark the image unavailable. Never fabricate an export path.

Use these top-level JSON keys (schema version `1.0`):

| Key | Content |
| --- | --- |
| schemaVersion | `1.0` |
| original | Source URL/file/node IDs, accessible image path, viewport, image-to-frame transform and crop |
| structure | Stable element IDs, parent IDs, type, bounds in source-frame px, z-order, layout and clipping |
| designTokens | Colors, typography, spacing, radii, material recipes and their IDs; scope limited to this reference |
| components | Instances, element IDs, token/material references, visible variants |
| composition | Alignment, spacing relationships, hierarchy, overlap and anchoring rules |
| behavior | Observed states/interactions with evidence; unknown for motion or gestures unavailable in a static image |
| semanticTags | Interface type, style, mood and searchable material tags, labeled as interpretation |
| rebuild | Required code paths, exports, styles, assets and preview route; source reference IDs, asset substitutions with source asset path or URL, image hash and output-element mapping (or bundled asset path and fallback reason), and renderer-specific approximations |
| quality | Verification status per target, compared crops, discrepancies, confidence/evidence and unresolved alternatives |

For inferred properties use `{ "value": ..., "status": "inferred", "confidence": "medium", "evidence": "..." }`; use `observed` for directly established facts and `unknown` with a null value for unavailable information. Store editable-source values as observed with their source node. An inferred estimate remains inferred even after its rendered appearance has been verified.

Record units, coordinate origins and paint-stack ordering explicitly. Preserve stable element/material IDs across the reference model and code. The Markdown summary should explain distinctive composition and materials, reconstruction decisions, missing evidence and what the next agent should verify; it must link to the JSON and accessible original. Validate JSON syntax and that all parent/token/material references resolve before reporting the package complete.

## Required code package and creative-prototyping handoff

Source lives in the current project, following existing conventions, never in the installed skill directory. In creative-prototyping save reference evidence under `outputs/<project_id>/reference-packs/<reference-id>/`; standalone work uses `reference-packs/<reference-id>/`. Keep source files in the app's source tree and point to them from the package.

For every completed screen export a reusable component (for example Screen01) with data and callbacks separate from visual layout. Include scoped CSS or existing styling-system files, permitted assets and the faithful viewport fixture. Write `code-handoff.json` with:

- schemaVersion and referenceId;
- source image path/URL and optional source node;
- entryFile, exportName, styles, assets, dependency names/versions and package manager;
- props contract and minimal import/usage example;
- reference viewport, preview route and run command;
- reference model path, original-to-element mapping, baseline/adapted status;
- verification.build, verification.visual, evidence paths, known limitations and review verdict.

Use paths relative to the current project root and record that root. All paths must resolve; do not invent a URL for a server that was not started. Verify imports and exports with the project build when available. JSON descriptions alone do not satisfy delivery.

Map materials to semantic DOM and CSS, retaining separate layers for independent opacity, blur and stacking. Compare browser output directly with the original, not an intermediate reconstruction. Label source observations separately from proposed responsiveness or motion. creative-prototype-composer imports the delivered components instead of reconstructing them again; it adapts them through props, scoped tokens and motion wrappers to the approved scenario. Do not publish or deploy as part of this handoff.

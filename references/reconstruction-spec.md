# Code reconstruction contract

## Output and viewport

Build semantic DOM, React components, editable CSS and SVG icons. Never use the whole reference screenshot as the rendered screen, a traced background, a full-screen raster or a canvas substitute for UI. Raster photographs remain allowed inside media containers.

For a clean screenshot use the actual UI viewport. For a photographed or tilted device, infer a front-facing UI viewport from visible boundaries and record uncertainty; bitmap dimensions are not automatically viewport dimensions. Exclude hands, bezels, reflections and presentation backdrops. Preserve intentional rotation within the UI. Multiple screens in one image are independent outputs unless clearly continuous.

Capture a faithful reference-sized baseline, with original clipping and corner geometry where measurable. Implement responsive behavior as an explicit adaptation for creative-prototyping, not as a fact recovered from a screenshot. Do not force unrelated screens into one design system.

## Composition and layout

Establish hierarchy, proportion, density, alignment and dominant materials first. Use flex/grid, actual padding and gap for logical blocks; absolute positioning only for overlap, independent anchors and intentional rotations. For the faithful fixed-viewport calibration, measured absolute positioning is allowed when it reproduces the visible geometry more accurately. Keep text editable and repeated elements as components. Derive responsive flex/grid constraints afterward; do not let generic responsive defaults distort the baseline. Keep meaningful card/button/input/navigation components and scoped styles. Reuse repeated structures within a reference; share across references only when the approved product direction supports it.

Preserve visible content, wrapping, crop and layering. Do not invent hidden parts or interactions as observed evidence. Keep user-supplied text where legible; mark uncertain transcription rather than fabricating a quote. Functional controls use semantic elements, accessible labels and real state/handlers when scenario behavior is authorized; do not claim a working flow for decorative controls.

## Typography

Identify heading, body, numeric and decorative roles independently. Inspect project/local/licensed font sources and available official font distributions. Compare a primary candidate with three plausible alternatives for visually distinctive or uncertain font roles, at comparable cap height and optical weight. Verify browser loading and Cyrillic/Latin support using `Съешь ещё этих французских булок` and `The quick brown fox jumps`. Mark unavailable comparisons, do not invent font identification.

Match typeface character before tuning size, weight, line-height, tracking, block width and line count. Do not use excessive letter spacing or transforms to hide a wrong family. Distinguish serif construction; never default every serif to DM Serif. Use real editable text, not outlines or rasterized text.

## Materials and geometry

Use layered CSS radial/linear/conic gradients and editable SVG paints where appropriate. Match color-field topology, off-center blooms and elliptical proportions before fine color tuning. Preserve paint ordering. Test opaque and translucent candidates over the actual background; similar hues alone do not establish transparency.

Use backdrop-filter for blur of content behind a surface, filter for the surface itself, and independently tunable shadows/highlights. Keep labels sharp and opaque when only the surface is translucent. Do not bake gradients, shadows or blur into images. Record approximations where CSS cannot exactly reproduce the inferred material.

Preserve per-corner radii and distinguish continuous corners from circular radii. Use supported CSS or editable vector clipping when necessary, with explicit fallback and browser verification; do not assume browser support for corner smoothing. Keep fractional geometry when necessary for fidelity rather than forcing a modular grid that distorts evidence.

## Contours, smooth corners and rotation

Measure each corner independently in source-frame units; distinguish circular arcs, elliptical radii, continuous/smoothed corners and fully custom contours. Do not replace a smooth corner with an oversized circular radius. For smoothing, match the transition from straight edge into curve and the distribution of curvature, not just the corner's bounding box. Use verified browser-supported CSS when it matches; otherwise use an editable SVG path or clip with the appropriate contour. Keep fill, border, highlights and clipping aligned to that same geometry. Record uncertain smoothing parameters as estimates, not recovered source values.

Measure intentional element rotation from visible edges or landmarks and preserve its sign, angle, transform origin and stacking. Separate local rotation from perspective distortion of the source photograph. Check the rotated silhouette and overlap, not only the untransformed layout box; do not round measured angles to convenient presets.

For distinctive curved shapes, inspect an enlarged source crop and identify extrema, inflection points, tangent directions, concavities and asymmetry. Reconstruct with editable SVG Bézier paths and appropriate holes/fill rules where needed. Use enough control points to preserve the contour without introducing wobbles; avoid substituting circles, pills, rounded rectangles or coarse polygons for complex curves. Compare aligned silhouette overlays and negative spaces at native size and enlarged scale. Preserve the path's aspect ratio and verify any scaling or clipping in the actual browser.

## Icons and assets

Use Lucide as the default icon library (`lucide-react` in React projects, the appropriate Lucide integration for the existing stack otherwise). Inspect installed exports or the official catalog before choosing an icon; verify names and APIs against the version actually used. Search by meaning and visual synonyms, then compare plausible candidates as rendered SVGs beside the source crop. Match silhouette, proportions, orientation, optical size, negative space, stroke weight, caps, joins and outline versus filled treatment. A matching label alone is not sufficient.

Tune rendered size and stroke width together: compare the visible line thickness at the final screen scale rather than accepting library defaults. Preserve any icon container as a separate layer. Do not apply blanket fill to a line icon to imitate a filled glyph when that closes gaps or changes its construction. If no Lucide candidate matches a defining filled, mixed-fill or unusual silhouette, use an accurate permitted source vector or an editable custom SVG and record why Lucide was unsuitable. Do not force an inaccurate library icon merely for consistency. Record the selected export, size, stroke/fill treatment and any custom-vector exception in the reference model. No emoji, Unicode or icon-font substitutes. Prefer available project and user-provided media. Never treat complete UI screenshots as media assets to fill the reconstructed UI. Record substitutions and asset provenance, keep images local when authorized, and preserve licensing constraints.

For unavailable media, a clearly labeled geometry placeholder is allowed only in an unfinished development fixture. It cannot pass fidelity review when the media defines the reference. Do not replace different image/icon roles with a single repeated Wi-Fi glyph, generic circles or arbitrary gradients. Resolve the actual asset or a disclosed style-matched replacement before presenting the adaptation as complete.

## System UI

For the faithful calibration only, omit operating-system status icons while preserving the original top safe-area and app-content positions in the baseline. If the reference shows a system keyboard, represent its region with one shared-gradient placeholder, preserving application controls above it. In the functional responsive prototype use real input behavior and allow the device keyboard; keep the placeholder only in the reference fixture, not as a permanently blocked region in the live app.

For the separate staged mobile preview, use the bundled system bars and automatic platform selection defined in [preview-shell.md](preview-shell.md). Do not apply the calibration omission rule to that shell.

## Verification

Build top-down, render after major blocks, correct visible mismatches promptly, and finish one reference before the next. Compare complete screenshots and aligned crops at the calibrated viewport. Inspect typography, geometry, materials, clipping and z-order separately; a build pass does not establish visual fidelity. Use the shared maximum of three correction cycles per reference from art-director.md. Preserve unresolved/unknown status rather than claiming pixel accuracy from low-resolution or occluded material.

## Measured scene model before code

Use the same explicit layer reasoning that supports accurate design-tool reconstruction. In the existing reference model, record a compact scene tree: layer ID, parent, semantic role, bounding box in normalized UI coordinates, z-order, clipping, corner geometry, fill, text/style or asset ID. Establish a source UI coordinate frame first; for perspective photos record estimated bounds and uncertainty. Keep observations distinct from implementation decisions. Inspect the original pixels while writing this model; do not reconstruct from catalog captions.

Translate the scene model into editable DOM/CSS/SVG at a fixed calibration viewport. Browser default margins, line-height, flex shrink, auto grid sizing and inherited styles must not silently change measured bounds. Check actual rendered element bounds and loaded font metrics against the model. Use accurate local SVG paths for distinctive vector geometry; do not approximate every silhouette with rounded rectangles and circles. If the user supplies measured geometry, styles or source assets, use them as evidence rather than guessing them again.

## Separate calibration and product adaptation

Maintain two explicit states/artifacts, with separate data: reference-calibration (source content and source-specific imagery) and scenario-adaptation (the user's required content and behavior). Label calibration outside the rendered UI. Never add payment headers or progress indicators to an unchanged Library/Navigation/WaterPod reference and present that hybrid as a payment direction.

Before handing off a product direction, inspect every visible string, image role and action against the scenario contract. Remove source-only sample text and unrelated source functionality from the adapted state; retain the calibrated visual system. Conversely, do not insert payment-specific Wi-Fi icons into the faithful source fixture. A source reconstruction is not evidence that product adaptation is complete. Compare both with the original, and report their verdicts separately.

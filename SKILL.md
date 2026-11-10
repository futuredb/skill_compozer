---
name: compozer
description: Reconstruct UI reference images and local screenshots directly as reusable React components and editable CSS. Use for faithful image-to-code reconstruction, interactive screen demos and reference components consumed by creative-prototyping.
---

# Reconstruct references directly in code

Produce actual reusable source and a local browser preview. Do not substitute specifications for code.

## Inputs and scope

Accept local images, selected reference IDs from the creative-prototyping catalog, accessible image URLs. Read original images at sufficient resolution, not only contact sheets. For a directory, establish the relevant screen/region queue from the requested scope; do not reconstruct the entire library unless requested. Ignore filenames when determining image content.

## Required references

Read [references/reconstruction-spec.md](references/reconstruction-spec.md), [references/materials-and-handoff.md](references/materials-and-handoff.md), and [references/art-director.md](references/art-director.md). They define the code reconstruction, evidence model and review loop.

Read [references/typography-space-imagery.md](references/typography-space-imagery.md) for typography, whitespace and imagery calibration, including small thumbnails. Apply its separate acceptance checks before calling an adaptation faithful.

## Fidelity priorities

Reproduce the reference's actual contours and materials: per-corner radii, smoothed corners, rotation angles, complex curves, blur, glass, layered gradients and gradient borders where visible. Use Lucide as the default icon library, selecting by visual construction as well as meaning. Do not simplify distinctive geometry into standard rounded boxes or accept a semantically correct icon with the wrong silhouette, stroke weight or fill treatment. Follow the measured geometry, icon-selection and material checks in the reconstruction contract; verify these details in aligned browser crops before declaring fidelity.

## Recognized components and animated demo

Identify interactive components and their scroll containers in each reference. Use `21st:21st-cli-use` to search for suitable animation components, inspect and retrieve matching source, then integrate and adapt the motion into the reconstructed UI. Preserve reference geometry and record provenance; use a documented local fallback only when no suitable accessible match exists. Read [references/interaction-demo.md](references/interaction-demo.md) to build real local behavior and a short animated demonstration: scrolling, presses, field entry, gallery movement and other supported actions. Apply this after faithful static calibration. The staged preview plays one cancellable sequence; manual interaction takes over immediately. Keep calibration and library comparison images still, and mark inferred behavior and added motion as designed adaptation.

## Persistent reference library

Before analyzing or reconstructing any input, check the shared library at `~/.codex/compozer-library/index.json`. Follow [references/library.md](references/library.md) for lookup, reuse and recording. Reuse an existing reconstruction when the source matches; inspect its original/result and limitations before deciding which work remains. Do not reconstruct the same reference from scratch by default.

After reconstruction, save the source/result pair, reusable code snapshot, reference package and verification status in the library, and update its searchable index and visual gallery. This library is persistent user data outside the installed skill and separate from project deliverables. Read the library’s AGENTS.md before updating it. Never write gallery HTML from an importer: run `python3 ~/.codex/compozer-library/scripts/render_gallery.py` and `python3 ~/.codex/compozer-library/scripts/validate_gallery.py` after each catalog change. Preserve the dark three-column image-only slider gallery and both icon-only actions; do not report the save complete if validation fails.

## Workflow

1. Check the library for this reference before starting a new breakdown; reuse a matching entry according to references/library.md. Inspect the current project, its instructions, framework, assets, fonts and dependencies. Use its React/TypeScript and styling conventions. For a new standalone preview, use a minimal React setup; do not replace an existing application or add a second framework. A non-React project keeps its own stack unless migration is authorized; report the handoff format.
2. Inspect each selected original independently. Record source viewport/crop, mockup perspective and uncertainty. Separate the application UI from phone hardware, hands and presentation backdrops.
3. Build a measured layer/scene model before code as specified in reconstruction-spec.md; use explicit bounds, text roles, asset IDs and stacking rather than approximate layout from memory. Build the reference model and material evidence, including component roles, state/action mappings, scroll axes and evidence status. Establish typography, composition and dominant surfaces before fine detail. Do not normalize unrelated references into a shared visual style.
4. Implement one reference at a time as exported source components, scoped styles, local permitted assets and data/interaction props. Start with the screen structure and major materials; render and inspect each major block before advancing.
5. First produce and visually compare a faithful calibration of the selected source screen/region before replacing its content. Record 3–5 defining traits and measurable geometry in the reference package. Keep a faithful baseline at the reference viewport. When invoked by creative-prototyping, additionally adapt it to the approved direction, responsive layout and real scenario. Preserve baseline evidence and label adaptations explicitly. Compare original → calibration → adapted browser render; a generic layout with similar colors does not pass. This stage does not restart the three-direction approval flow.
6. Search 21st for matching component animations and integrate suitable retrieved source as specified in references/interaction-demo.md. Implement the recognized components’ local interactions and the cancellable demo sequence from references/interaction-demo.md. Consume verified component-manifest and local React Bits matches when provided. The integrated creative prototype uses suitable animation libraries by default; preserve composition and an inspectable still state. Static images do not prove original timing or gestures. Mark added motion as designed adaptation, verify access/API before using libraries, and provide reduced-motion behavior.
7. Run available build/type checks and render the local preview. Compare actual browser screenshots against original images at the reference viewport, plus responsive views for the integrated prototype. Perform the mandatory magnified-detail self-check in references/art-director.md: inspect matched source/render crops, correct complex contours and small details, then capture fresh evidence. Apply the bounded art-director loop; independent review does not replace the composer’s self-check. If browser access is unavailable, deliver source with visual verification marked unverified.
8. Before saving the final result, run the final neatness, symmetry and shape audit in references/art-director.md on fresh renders of every screen and its staged preview. Correct supported defects and recheck the affected areas; preserve intentional source asymmetry. Check that calibration and adapted scenario are separate artifacts, that every adapted string/action belongs to the requested scenario, and that no defining asset remains a generic placeholder. Record separate visual verdicts. Save the reference package and code handoff. Wire the completed components into the authorized prototype route/scene when that is part of the task; otherwise provide a precise import and usage example. Do not deploy merely to show a preview.

## Mobile reconstruction preview

Wrap completed mobile reconstructions in the control-free design shell from `mobile-prototype-stage-v2`. Read [references/preview-shell.md](references/preview-shell.md) before implementing the preview. Infer iOS or Android from reference details without asking for a platform choice. Keep the faithful calibration independent from the staged preview. Desktop/web references keep their appropriate viewport rather than being forced into a phone.

## Preview library shortcut

After reconstruction, add an icon-only Lucide Library button at the top-right of the preview shell linking to the Compozer library. Follow the preview navigation and gallery rules in references/library.md. Keep it outside the reconstructed component and exclude preview chrome from calibration captures.

## Completion

Report implemented screens/components, recognized interactions, demo route and verification, source paths, preview route or run command, reference package and handoff paths, build/browser verification, reviewer mode/verdict and material limitations. Include the library entry path and whether it was reused, revised or newly added. Code is the required deliverable.

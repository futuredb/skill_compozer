# Typography, space and imagery fidelity

Read when reconstructing or adapting an image reference. This extends the calibration workflow; record the evidence in the existing reference package rather than creating another approval stage.

## Compare the UI, not the presentation photograph

Identify the visible application plane, excluding hands, phone bezel, surrounding photograph and external preview controls. For angled phones, estimate front-facing proportions from that plane; record uncertainty. Do not compare raw bounding boxes from the perspective photo against a flat screen or count the surrounding photograph as application whitespace. Never claim exact font identity or pixel accuracy from an insufficient-resolution photograph.

## Typography is a layout system

For each text role record family character, glyph width and x-height, optical weight, case, tracking, size relative to screen width, line-height, line count, block width, alignment and emphasis within the line. Inspect heading, numerals, labels and captions separately. A source can mix light and bold words within a small heading; replacing that with a large uniformly bold title changes its style.

Identify fonts from available source/assets when possible. If unknown, compare available candidates visually using the actual target-language string and representative numerals. Verify Cyrillic coverage and loaded browser fonts after document.fonts.ready; a Latin-only face silently falling back is a fidelity failure. Label the chosen font as an approximation when identity is unconfirmed. Do not default to the project's usual sans without comparison.

Fit text using the source's block width, scale, optical weight and line rhythm together. Preserve meaning and required information; shorten optional copy only where authorized. Do not enlarge the title to fill empty space or arbitrarily force source line breaks onto longer translated content. If content cannot fit without losing the source hierarchy, record the conflict and change the anchor or grouping rather than silently making the screen heavier. Keep text legible; reproduce the hierarchy rather than unreadably small photographed pixels.

## Whitespace and optical density

Record normalized bounds for the header, card group and footer, side margins, header-to-grid gap, column/row gaps, internal padding and deliberately empty zones. Distinguish space outside cards from empty space inside them. Estimate text/image/solid-dark occupied area and the relative prominence of heading versus tiles. Use these as comparison targets, with explicit uncertainty rather than invented exact measurements.

Preserve staggered columns, unequal tile heights and the balance of quiet and active regions. Matching the number of tiles is insufficient. Do not fill empty areas with extra captions, badges, decorative lines or oversized symbols. Judge optical density at equal UI width, then inspect text and asset crops at native scale. Functional controls added for the target scenario must be acknowledged in the adaptation and must not silently consume all of the reference's breathing room.

## Inventory images at every scale

Before coding list every visible visual asset by role: main photograph, cut-out object, illustration, thumbnail/avatar, inset image, icon, texture. For each record location, relative size, crop, medium, lighting/material, palette, edge treatment and overlap. Small circular images inside chips are assets, not interchangeable colored dots. Keep icons distinct from thumbnails.

Match the source's media language when replacing subjects for the task. A landscape photo and cropped botanical image do not justify a glossy 3D product symbol; a photographic thumbnail does not justify a generic SVG icon. Preserve image-to-card ratio, cropping and visual hierarchy. Use permitted existing assets or create/source appropriate replacements through available tools within the task scope. If a defining asset is unavailable, mark the gap and do not call a placeholder faithful. Do not insert the entire reference as the screen background. Do not add irrelevant imagery solely to meet an asset count.

## Palette and surface contrast

Record colors by semantic surface: application background, cards, primary/secondary text, controls and accents. Compare hue, saturation, lightness and the contrast between adjacent surfaces independently. Do not substitute a warm cream canvas for a neutral light-gray canvas, or tint neutral surfaces to harmonize with an illustration. Distinguish the application background from the surrounding photograph. Sample multiple clean interior areas where tools allow, avoiding shadows, edges, reflections and compression artifacts; label values estimated from a photographed screen rather than asserting exact design tokens. Check the palette in the rendered browser at the same still state. Preserve subtle gray-background/white-card separation; matching accent colors alone does not pass.

For the supplied 6bbdb233673f1702ab21374d96a3924e.jpg reference, the user explicitly identifies the application background as gray. Preserve a neutral light-gray screen background and white/light cards; the cream cast in the payment adaptation is a mismatch, not an intentional palette choice. The exact gray value remains to be calibrated against the image.

## Review evidence and stopping rule

At the same normalized UI width compare original → calibration → adaptation. Include focused crops of (1) typography, (2) the whitespace/grid, (3) main images and small inset images. In the existing review record observed source trait, implemented value/asset, visible mismatch and correction. Review typography, whitespace, imagery and palette independently: a matching grid cannot compensate for wrong fonts or imagery. Missing defining small assets, unjustified weight/scale increases, lost empty zones, or substitution of photographic imagery with generic 3D/gradients require revision. Follow the existing maximum of three correction cycles; unresolved differences remain explicit, not a claimed pass.

## Diagnostic example: 6bbdb233673f1702ab21374d96a3924e.jpg

This example is not a template for other references. The provided photo shows a relatively small two-line uppercase date heading with mixed emphasis, a tiny welcome line, a separate pale-blue search control, staggered tall/short tiles, photographic landscape imagery, cropped botanical imagery on coral, small circular images in overlapping black chips, and a restrained lower strip. Exact font identity is not established by the photograph.

The supplied payment adaptation preserves a staggered grid but introduces a large heavy sentence-case heading, a glossy extruded Wi-Fi illustration, abstract lines in the coral tile, and text-only chips. These are substantive style changes. A faithful revision should restore the source's heading scale/weight rhythm, quiet spacing, media treatment and small-image roles using task-relevant assets, while retaining required payment information and actions. Do not copy the hand, device perspective or photo backdrop into application layout; do not remove a necessary payment action to mimic a home screen.

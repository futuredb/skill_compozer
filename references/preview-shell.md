# Control-free mobile preview

Use the installed `mobile-prototype-stage-v2` skill as the shell reference. Read its SKILL.md and relevant design-shell parts of assets/starter/index.html before implementation; reuse its bundled system-bar assets. This Compozer mode explicitly overrides its operator-control requirements: omit all scenario/state buttons, platform/theme switches, scene dimension/radius inputs, zoom controls, settings panels and presentation entry buttons. Keep configuration in code, not in visible controls. Do not ask whether to add presentation. This request selects the design shell, not hands, hardware mockups, 3D or a presentation editor.

## Automatic platform and appearance

Inspect system status/navigation details, gesture handle or button navigation, safe areas, app navigation patterns and visible device cues. Choose the strongest supported iOS or Android interpretation; do not use filename or color alone as evidence. Record platform, appearance, cues and uncertainty in the handoff. If genuinely ambiguous, use iOS as the documented fallback without blocking on a question. Match light/dark system artwork to the actual top/bottom product surfaces. This choice affects shell/system artwork, not a redesign of the product into platform defaults. Android uses gesture navigation unless the reference clearly shows button navigation; never render both.

## Surface and responsive behavior

Use reusable MobileSurface, SystemStatusBar and SystemNavigationBar components or existing equivalents. On desktop, center the live mobile interface on a frameless neutral stage, with no outer card, bezel, mockup hardware, added notch or settings sidebar. Use the stage skill's design-shell background and soft shadow; keep its platform-specific surface radius defaults (iOS 60px, Android 50px) unless visible source geometry justifies another radius. Configure dimensions from the inferred logical reference viewport; use 393×852 only when unknown, not to distort a measured reference. Fit uniformly on small desktops without independent X/Y stretching.

Use the stage skill's bundled transparent system-bar artwork and bar layout contract in the staged preview. Preserve product content and avoid duplicate bars, islands or home indicators: reuse an existing correct system region or separate it from the exported product component before composing the shell. Do not layer system artwork over reference text or controls. On mobile below 768px, show the live product edge-to-edge at full width and 100dvh, with safe areas and exactly one set of system bars; remove desktop radius, shadow, transforms and stage decoration. Preserve real product controls and interactions: “no controls” means no demo/operator controls, not removal of application buttons.

The previously requested icon-only Library shortcut remains the sole desktop shell action, at the page's upper-right outside the mobile surface. Hide it on mobile and in calibration captures; retain it in the desktop staged preview. Follow library.md for a working local destination.

## Calibration and saved evidence

Keep a dedicated reference-sized calibration route/fixture without added shell chrome; retain its existing system-UI omission policy and measured content positions. The staged preview is a separate presentation of the same reusable live product, not evidence of exact source geometry. Do not change a faithful calibration to accommodate newly added system bars. Keep reference-specific content unchanged; a shell alone is not a product-scenario adaptation.

Record calibration and staged-preview routes, chosen platform and relevant dimensions in the handoff. Store a staged-preview screenshot separately when captured. The library before/after pair continues to use original versus faithful calibration, not the whole desktop stage. Do not overwrite saved reconstruction evidence merely to add a shell.

Verify desktop and mobile: correct inferred platform, one set of system bars, no demo controls in the DOM/tab order, no duplicated system artwork, no obscured app content, working product interactions, desktop Library shortcut and edge-to-edge mobile layout. Check the calibration separately for unchanged measured geometry. Only claim browser verification when both states were actually inspected.

## Multi-screen references

When a reference contains multiple screens, preserve all of them in the default staged preview as a horizontal strip of live mobile surfaces in reference order. On desktop show them side by side, fitting height uniformly; when width is insufficient, scroll horizontally rather than shrinking screens into thumbnails. On mobile show one full-width surface at a time with native horizontal swipe and scroll snap. Do not add operator controls or screen-switching buttons. Keep exactly one desktop Library shortcut outside the strip.

Keep every screen mounted and preserve its local state; share scenario data where the original flow requires it. Existing product navigation scrolls to the corresponding screen rather than replacing or unmounting the others. Native scroll must coexist with vertical product scrolling, range inputs and editable fields. Respect reduced motion. The library preview link opens the entire strip; ?screen=<stable-id> positions the strip on the requested screen without hiding siblings. Verify every screen is reachable on desktop and mobile, state persists across navigation, only one Library icon exists, and source calibration remains unchanged. Record screen IDs/order and deep links in the handoff.

## Animated interaction demonstration

Apply [interaction-demo.md](interaction-demo.md) to the staged live product after calibration. Keep the shell free of operator controls; the Library shortcut remains its sole desktop action. The animation runner owns only a short local demonstration and yields to user interaction. Keep all multi-screen surfaces mounted, avoid competing scroll controllers, and preserve exact calibration with demo disabled.

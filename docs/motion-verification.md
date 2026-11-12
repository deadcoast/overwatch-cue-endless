# Queue motion refinement — 2026-11-12

Updated `searching-overlay.html` using the supplied `sonar_effect.mp4` reference, sampled at 0.3-second intervals.

- Replaced the gradient hairline and orbiting dot with two solid SVG clutch shoes with squared radial ends and stepped shoulders.
- Added a paired amber wave on a 3-second cycle, clipped to the pink surface, with matching frame reflections and a short outward frame echo.
- Removed the unrelated automatic horizontal highlights and emblem sparkle; retained button hover highlights.
- Contained and softened the static gold halo. Preserved layout, typography, embedded assets, timer, and settings.
- Reduced motion stops the spinner and hides the pulse and frame echo.

Verified in headless Chromium at 1480 x 580 and 880 x 270: rendered six animation phases, inspected full and tab layouts, cancel reset to 0:00, layout switching, and reduced motion (zero active animations). No page JavaScript errors. Screenshots are saved alongside this note. Native OBS rendering and subjective user acceptance remain unverified.

## Spinner correction after user review

The first revision still read as a segmented outline and was rejected. Replaced its long, narrow arcs with short filled plates: 80-degree coverage per piece, 100-degree gaps, approximately twice the previous thickness, faceted outer edges, raised shoulders and chamfered ends. The inner seat follows the gold rim. Pulse and layout were preserved. Inspected three rendered rotation phases in Chromium at 880 x 270; no JavaScript errors. See `clutch-0.png`, `clutch-425.png`, and `clutch-850.png`. This faceted revision was also rejected; it is superseded by the correction below.

## Connected ring correction after the 02:00 screenshot

Opened and visually inspected the user's `Screenshot 2026-11-12 020015.png`, the saved reference, and six frames extracted directly from the original `sonar_effect.mp4`. The rejected shape had detached white polygons, jagged outer edges, and an oversized gold rim. The reference shows a fine continuous white ring joining two wider circular sections.

- Replaced the faceted polygons with smooth circular arcs and short stepped ends, connected by a full white band.
- Matched the badge's size relative to the tab and the dark-disc-to-outer-white radius ratio (23.8 / 30.3 = 0.785; approximately 42 / 54 = 0.778 in the video). Narrowed and lightened the gold rim.
- Kept the existing rotation period, pulse, embedded icon, layout, timer, and settings behavior.

[Inspected original-video / revised-render comparison](../.design/shape-reference-comparison.png). The original video is enlarged from its native resolution; the comparison supports the silhouette and proportions, not a claim of pixel-identical artwork.

Personally viewed Chromium screenshots of the revised shape at 0, 45, 90, and 135 degrees, the full overlay at 1480 x 580, the tab at 880 x 270, and the normal browser preview with settings. A separate visual review also checked the comparison and rotated closeups. The white band remains continuous and the long outside edges are circular in the inspected views.

Runtime checks: no page JavaScript errors; layout switching and cancel-to-0:00 passed; rotation transforms returned to their starting value after 1700 ms. With reduced motion enabled on an idle page, there were zero active animations, the spinner's animation was `none`, and all sonar/echo elements had zero opacity. A separate check immediately after hovering Cancel still saw the existing button sheen; it was not spinner motion.

Local intermediate captures and measurements are in `.design/shape-*`. Original video SHA-256: `ef2f2421670d1cb223460bd6e29e7a7d0c1647509f30e3b72fa04c4f9229d971`. Native OBS was not exercised in this correction.

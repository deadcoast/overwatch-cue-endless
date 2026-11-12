# Queue motion refinement — 2026-11-12

Updated `searching-overlay.html` using the supplied `sonar_effect.mp4` reference, sampled at 0.3-second intervals.

- Replaced the gradient hairline and orbiting dot with two solid SVG clutch shoes with squared radial ends and stepped shoulders.
- Added a paired amber wave on a 3-second cycle, clipped to the pink surface, with matching frame reflections and a short outward frame echo.
- Removed the unrelated automatic horizontal highlights and emblem sparkle; retained button hover highlights.
- Contained and softened the static gold halo. Preserved layout, typography, embedded assets, timer, and settings.
- Reduced motion stops the spinner and hides the pulse and frame echo.

Verified in headless Chromium at 1480 x 580 and 880 x 270: rendered six animation phases, inspected full and tab layouts, cancel reset to 0:00, layout switching, and reduced motion (zero active animations). No page JavaScript errors. Screenshots are saved alongside this note. Native OBS rendering and subjective user acceptance remain unverified.

## Spinner correction after user review

The first revision still read as a segmented outline and was rejected. Replaced its long, narrow arcs with short filled plates: 80-degree coverage per piece, 100-degree gaps, approximately twice the previous thickness, faceted outer edges, raised shoulders and chamfered ends. The inner seat follows the gold rim. Pulse and layout were preserved. Inspected three rendered rotation phases in Chromium at 880 x 270; no JavaScript errors. See `clutch-0.png`, `clutch-425.png`, and `clutch-850.png`. User acceptance remains pending.

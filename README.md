# Overwatch Cue Endless

A standalone, animated Overwatch-style searching widget for OBS. Show an endless queue screen with an elapsed timer, rotating badge, and sonar pulse. Choose the full panel or a compact searching tab.

The widget is manually controlled. It does not read your Overwatch queue or send commands to the game.

## Screenshot

![Running widget with the full panel, elapsed timer, and settings drawer][widget-screenshot]

Captured from the running browser preview with settings open. The blue backdrop belongs to the preview; the OBS overlay has a transparent background.

**Screenshot URL placeholder:** replace the `widget-screenshot` URL at the bottom of this README after pushing. The captured image is saved at [docs/images/widget-running.png](docs/images/widget-running.png).

## Installation

1. Download this repository using **Code → Download ZIP**, then extract it.
2. Keep [searching-overlay.html](searching-overlay.html) in a permanent folder, such as `C:\Overlays\Overwatch\`. This is the only file needed to run the widget; its fonts and icon are embedded.
3. Double-click the HTML file to preview it in your browser. The widget starts immediately, with its settings visible.

There is no build step, package installation, local server, or internet connection required to run the downloaded widget. Use OBS Studio with a Browser source for streaming, or a modern browser for standalone preview.

### Add it to OBS

1. In your scene, select **Sources → + → Browser** and name the source.
2. Enable **Local file**, then browse to `searching-overlay.html`.
3. Set **Width** to **1480** and **Height** to **580** for the default full panel.
4. Leave **Refresh browser when scene becomes active** off to avoid restarting the visual animation whenever you return to the scene. Leave the default transparent Custom CSS in place.
5. Confirm the source, then position and scale it in your scene.
6. Right-click the source and choose **Interact**. Click inside the interaction window, then press **S**, or double-click the circular badge, to open settings.
7. Choose the elapsed time, speed, and layout. Hide settings again before showing the source on stream; the settings drawer is part of the rendered overlay.

| Widget layout | OBS width | OBS height | Visible content |
| --- | ---: | ---: | --- |
| Full panel | 1480 | 580 | Searching tab, queue label, Cancel, and Change Role |
| Button only | 880 | 270 | Searching tab, badge, and timer |

After changing the widget's layout, update the source's Width and Height in OBS properties to match. Changing layout inside the widget does not resize the OBS source automatically.

For the host application's source properties, see the [official OBS Browser Source guide](https://obsproject.com/kb/Browser-Source).

## Using the widget

For a fresh queue, open **Interact**, set speed to **1×**, and choose **Jump to → 0:00**. To continue an existing wait, enter its elapsed time and press **Set**. Hide settings with **S** or a double-click on the badge, then close the interaction window. The timer keeps counting.

When the queue ends, hide the source or switch scenes in OBS. Hiding the source does not pause the timer. Reset it when you want to start the next wait.

### Controls

| Control | What it does |
| --- | --- |
| **S** or double-click badge | Opens or hides settings. In OBS, use the source's **Interact** window first. |
| **Elapsed → Set** or **Enter** | Sets the timer to the entered value and continues counting from there. |
| **Jump to** | Starts counting from `0:00`, `12:00`, `25:00`, `40:00`, or `1:20:00`. |
| **1× / 10× / 60×** | Changes timer speed. At 60×, one real second adds one timer minute. Badge and pulse animation speeds stay the same. |
| **Full panel / Button only** | Changes the visible layout. Use the matching OBS dimensions above. |
| **CANCEL** | Resets the widget timer to `0:00` and immediately resumes counting. It does not cancel an actual game queue. |
| **CHANGE ROLE** | Decorative; it has no action. |

In **Button only** mode, Cancel is hidden. Reset through settings using **Jump to → 0:00** or the elapsed input.

If **S** does not close settings, move focus out of the elapsed input first, or double-click the badge.

### Entering elapsed time

| Input | Meaning |
| --- | --- |
| `38` | 38 minutes |
| `0:38` | 38 seconds |
| `38:20` | 38 minutes, 20 seconds |
| `1:05:30` | 1 hour, 5 minutes, 30 seconds |

Use whole numbers separated by colons. The seconds field must be below 60; in the three-part format, the minutes field must also be below 60.

### Saved settings and timer behavior

Elapsed time, speed, and layout are saved in local browser storage. The timer uses the system clock, so it includes time spent hidden or closed and resumes from that elapsed total after a reload while the saved state remains available. There is no pause control.

Your regular browser and OBS have separate storage. Configure the actual OBS source through **Interact**; settings changed in a browser preview do not configure OBS. Clearing browser-source storage, moving the file, or using a different browser/profile can start a new saved state. Settings visibility is not saved.

When reduced motion is enabled in the browser environment, the badge stops rotating and the sonar pulse is hidden. The elapsed timer continues.

## Optional URL setup

You can supply starting settings in a local file URL. In OBS source properties, turn **Local file** off and put a URL like this in **URL**, replacing the example path with your own:

```text
file:///C:/Overlays/Overwatch/searching-overlay.html?t=38:20&layout=tab&speed=1
```

Use forward slashes and encode spaces in the path as `%20`.

| Parameter | Values | Effect |
| --- | --- | --- |
| `t` | `38`, `38:20`, or `1:05:30` | Sets elapsed time using the same formats as the input. |
| `layout` | `full` or `tab` | Selects Full panel or Button only. |
| `speed` | `1`, `10`, or `60` | Sets the timer multiplier. |

`layout` and `speed` are reapplied whenever that URL loads. `t` is applied only when its value differs from the last successfully applied `t` value, so refreshing the same URL does not repeatedly reset the timer. Use the widget controls when you want to reset it deliberately.

## Troubleshooting

- **The overlay is clipped or has excess space:** match the widget layout to the OBS source dimensions above, then adjust its scene placement.
- **The settings drawer is visible on stream:** open **Interact** and hide it with **S** or by double-clicking the badge.
- **The timer runs too fast:** select **1×**. If using URL mode, also change or remove its `speed` parameter before reloading.
- **The timer is higher after reopening:** time continues while the widget is closed. Reset with Cancel or **Jump to → 0:00**.
- **OBS still shows an older version after replacing the HTML:** refresh the Browser source from its properties.

The screenshot and browser checks were captured in Chromium. Native OBS rendering was not exercised for this documentation update. Earlier visual checks are recorded in [docs/motion-verification.md](docs/motion-verification.md).

<!-- Replace this placeholder with the final hosted screenshot URL after pushing. -->
[widget-screenshot]: https://example.com/REPLACE_WITH_WIDGET_SCREENSHOT_URL.png

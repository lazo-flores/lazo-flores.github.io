# Capture Fullpage Screenshot

Render a fullpage screenshot of the local site using headless Chrome and save it to `~/Documents/website-review/` for visual review.

## Arguments

- `home` — capture only the home page (index.html)
- `consulting` — capture only the consulting page
- `both` (default) — capture both pages
- A specific filename or version label can be appended; otherwise the next version suffix (`v5`, `v6`, …) is chosen automatically per page.

## Instructions

1. **Make sure the dev server is running on port 8001.** If `curl -s -o /dev/null -w "%{http_code}" http://localhost:8001/` doesn't return 200, start it via `python3 -m http.server 8001` in the background, then wait for a 200 before continuing. **Never use port 8000** (Swing Trader).

2. **Pick output filenames.** The convention is `<NN>-<page>-fullpage-v<N>.png` for home and `<NN>-consulting-fullpage-v<N>.png` for consulting, where `NN` is a zero-padded sequence number and `v<N>` is a version label. Look in `~/Documents/website-review/` for the highest existing version per page and increment. If the user passes an explicit filename, use that.

3. **Capture raw screenshots** with headless Chrome. Use a generous viewport height so the page isn't truncated:
   - Home: `--window-size=1400,22000` (current document is ~19.6k tall; leave headroom)
   - Consulting: `--window-size=1400,8000` (current ~6.3k tall; the Calendly iframe area is mostly blank in headless)

   Example:
   ```bash
   '/Applications/Google Chrome.app/Contents/MacOS/Google Chrome' \
       --headless --disable-gpu --hide-scrollbars \
       --window-size=1400,22000 --virtual-time-budget=4000 \
       --screenshot=/tmp/screenshot-home-raw.png \
       http://localhost:8001/
   ```

   Run home and consulting captures in parallel (background bash tools) when capturing both.

4. **Smart-trim the trailing whitespace.** Naive trim breaks because the AI Twin widget is `position: fixed` and renders at the bottom-right of the viewport, so the last non-white row in the raw image is the widget — not the page content. Crop using the leftmost ~1100 columns (excluding the widget zone on the right) when scanning for the last content row:

   ```python
   from PIL import Image
   import numpy as np, os

   def smart_trim(raw_path, out_path, widget_col_exclude=300, pad=60):
       img = Image.open(raw_path)
       arr = np.array(img.convert('L'))
       # Ignore rightmost columns where the fixed AI Twin widget sits
       content = arr[:, :img.width - widget_col_exclude]
       nonwhite = np.where(content.min(axis=1) < 245)[0]
       last = int(nonwhite.max())
       img.crop((0, 0, img.width, min(last + pad, img.height))).save(out_path, optimize=True)
   ```

5. **Save trimmed screenshots** to `~/Documents/website-review/<filename>` and report each path + final dimensions to the user.

6. **Calendly iframe note:** on the consulting page, the embedded Calendly widget renders as a loading skeleton (three dots) in headless captures because the third-party iframe doesn't complete before the screenshot fires. The container styling (rounded corners, soft shadow) is still verifiable. Mention this when reporting if the user is reviewing the consulting CTA area.

7. **After saving**, you may want to spot-check via crops (e.g. crop a specific section to verify a fix). Save crops to `/tmp/` so they don't clutter `~/Documents/website-review/` (which is the canonical review folder).

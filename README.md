# SEG-Y Co-render Tools

**Open the tools:** https://hbedle-subsurface.github.io/seismic-corender/

Two browser tools for **co-rendering three seismic attribute volumes as one colour image**, so you can
see how the attributes relate at every point instead of flipping between three separate displays.
They were built for teaching at the University of Oklahoma, with the AASPI consortium.

- **Nothing to install.** Each tool is a single HTML file. Open the link above, or download a file and
  double-click it to use it offline in Chrome or Edge.
- **Your data stay on your computer.** SEG-Y files are read in your browser and never uploaded.

## Why co-render?

Each attribute highlights something different: amplitude or envelope for bright spots, coherence for
edges and faults, curvature for structure, spectral components for thickness and tuning. Blending
three of them into one colour image shows where they agree and where they don't. A channel that is
bright in the 30 Hz component, dim at 50 Hz and bounded by low coherence stands out as one colour,
where three separate maps would leave you to line it up in your head.

## Which tool?

| | **Simple** | **Advanced** |
|---|---|---|
| Blending | Direct RGB, ternary (LAB), HSV | Same, plus a colour map per volume, and base + overlay |
| Ranges | Clip % per volume | Histogram per volume: drag the lines, or type values |
| Views | Inline, crossline, time slice | Same, plus a **3D view** of all three together |
| Extras | Colour-blind-safe presets, colour key, save as PNG | Transparency, your own `.alut` colour maps, north arrow, scale bar, vertical stretch, zoom and hover readout, crop, enlarged view |

New to co-rendering? Start with **Simple**.

## Quick start

1. **Load** three or more SEG-Y volumes on the same grid (same inlines, crosslines and samples).
2. **Check the byte locations.** Click **View file headers**. If the text header names the inline and
   crossline bytes (Petrel exports often use 5 and 21), use those. The defaults are 189 and 193.
3. **Pick** which volume drives A, B and C, and choose a **blend mode**.
4. **Adjust each volume's range.** In the advanced tool, drag the yellow lines on its histogram.
5. **Save the view as PNG** when you have what you want.

## Moving around

**2D views:** use the slider. In the advanced tool you can also type an inline, crossline or time (ms) in
the box next to it and press Enter.

**Zoom, hover and crop in 2D** (advanced tool): scroll to zoom toward the mouse, drag to move around
when zoomed in, and double-click to reset the zoom. Hover to see the inline, crossline, time and each
volume's value under the mouse. To crop, click **✂ Crop** and drag a box, or type the limits in the
**Crop** row. The crop carries over to the other views, including 3D, where you can also type inline,
crossline and time limits. **Show all** goes back.

**Enlarge** (advanced tool) opens the picture on its own, filling the browser window, with just the
controls it needs. Rotate and zoom in 3D as usual there. **✕ Close** or Esc goes back.

**3D view** (advanced tool, **3D** button):

| To | Do this |
|---|---|
| Rotate | Drag |
| Move side to side / up and down | **Shift-drag** or **Ctrl-drag** (or right-drag) |
| Zoom | Scroll. It zooms toward where the mouse is pointing |
| Move / zoom with keys | Click the view first, then use the arrow keys and **+ / −** |
| Start over | Double-click, **Reset view**, or press **0** |
| Move a panel | Its slider, or type a line number or time |

Tick **Inline**, **Crossline** and **Time slice** in any combination. **Vertical stretch** and
**Panel opacity** are above the view.

## Good to know

- **Each volume is rescaled before blending.** A volume's low → high range is stretched over its full
  colour, so attributes with very different values (say −10,000 to 10,000 and 0 to 1) count equally.
  The range you set *is* the scaling, and **Weight** makes one volume count more.
- **Separate or shared range** (advanced tool). For volumes of the same kind, such as spectral components, choose
  **one shared range for all**, so a component with less energy stays dimmer instead of being
  stretched to look as strong as the others.
- **Range from the slice or the whole volume.** By default each slice gets its own 1–99 % range, which clips the
  extreme 1 % at each end so a few outliers don't wash out the colours. In the advanced tool you can switch
  the default to the true minimum to maximum, a range you set by hand is kept from slice to slice, and
  **Reset to default** or **Reset all ranges** puts things back.
- **Transparency.** In the advanced tool, any volume can have a see-through range, shown as dashed
  blue lines on its histogram. You can see through those parts to the panels behind in 3D.
- **North arrow and scale bar** (advanced tool) come from the X/Y coordinates in the trace headers. These are map-grid
  coordinates, so the arrow shows **grid north** of that coordinate system, not true north.
- **Vertical stretch** makes sections and the 3D box taller or flatter. It's a display stretch,
  not a true vertical exaggeration, because the files don't say how fast sound travelled.

## Citing

Please cite the tools if you use them in teaching, talks or papers. Click **Cite this repository** on
the right of this page for APA and BibTeX. A credit line and a link back are all we ask.

## Authors and licence

Dr. April Moreno-Ward and Dr. Heather Bedle, University of Oklahoma, with the
[AASPI](https://www.ou.edu/mcee/labs/aaspi) consortium.

Licensed [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/): free to use, adapt and
share, including in teaching, provided the source is credited and any adaptation is released under the
same licence.

## Open-source credits

The tools load no outside code, but they include colour maps and palettes made by others:

- **Colour maps** (advanced tool) from [Matplotlib](https://matplotlib.org/) (Hunter, 2007), including the
  ColorBrewer maps and turbo. *This product includes color specifications and designs developed by
  Cynthia Brewer (http://colorbrewer.org/).* turbo: copyright 2019 Google LLC, Apache License 2.0.
  viridis, plasma, inferno and magma by Nathaniel Smith and Stéfan van der Walt; cividis by Nuñez et al.
  (2018); cubehelix by Green (2011); coolwarm by Moreland (2009); twilight by Bastian Bechtold.
- **Colour-blind-safe presets** after Wong (2011, *Nature Methods*) and Paul Tol's muted palette.

Full list, references and licences: [open-source credits](https://hbedle-subsurface.github.io/seismic-corender/open_source.html).

## Versions

- **Simple V5.1:** `SEGY_Corender_simple_V5.1.html`
- **Advanced V6.4.3:** `SEGY_co-render_advanced_V6.4.3.html`. It adds the 3D view, transparency (a range
  around zero or both extremes), north arrow, scale bar, vertical stretch, the shared-range option, easier
  3D navigation, a colour key you can hide, reset buttons for the ranges, 2D zoom and hover readout, cropping (in 2D and 3D) and an enlarged view.

Older files stay in the repository, so earlier links keep working.

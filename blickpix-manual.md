# BlickPix Manual

## Overview

BlickPix is a minimalist macOS image viewer built around speed, keyboard navigation, and low UI clutter. Open an image and the surrounding folder becomes a browsable set — no import, no library, no setup.

---

## Supported Formats

| Format | Extensions |
|--------|-----------|
| JPEG | `.jpg`, `.jpeg` |
| PNG | `.png` |
| HEIC / HEIF | `.heic`, `.heif` |
| TIFF | `.tif`, `.tiff` |
| AVIF | `.avif` |
| JPEG XL | `.jxl` |
| WebP | `.webp` |
| GIF | `.gif` — animated GIFs play automatically |

---

## Opening Images

| Method | How |
|--------|-----|
| File picker | `Cmd+O` |
| Drag and drop | Drag a file onto the BlickPix window |
| Finder | Right-click any supported file → Open With → BlickPix |

When a file is opened, BlickPix scans its containing folder and builds a browsable image list starting from that file.

### Folder Access

BlickPix runs in a sandbox. If it cannot read the folder of a file you opened (for example an image dropped from a restricted location), it will prompt you to grant folder access. Clicking **Grant Access** in that dialog enables full folder browsing. If you decline, the single image loads without navigation.

To skip the per-folder prompt for folders you use often, add them once in **Settings → Permissions** (see below). Folders added there are accessible silently on every launch.

---

## Thumbnail Strip

A floating thumbnail strip sits below the main window and shows all images in the current folder.

- Thumbnails load outward from the current image so nearby images appear first
- The current image is highlighted with an amber-orange border and tint
- Click any thumbnail to jump directly to that image
- Press **T** or click the strip-toggle icon in the bottom-right toolbar to show or hide the strip
- Strip visibility is remembered across launches
- The strip scrolls automatically to keep the current image centered

### Multi-Selection in the Strip

Hold a modifier while clicking to select more than one image:

| Action | Result |
|--------|--------|
| Click | Jump to image (single select) |
| `Cmd`+click | Toggle image in/out of selection |
| `Shift`+click | Extend selection to a range from the last clicked image |
| `Cmd+A` | Select all images in the folder |

When two or more thumbnails are selected, the canvas switches to **Compare Mode** (see below).

---

## Compare Mode

Selecting multiple thumbnails replaces the single-image canvas with a side-by-side or grid layout.

| Selection count | Layout |
|-----------------|--------|
| 2 | Side by side |
| 3–4 | 2 × 2 grid |
| 5 or more | Scrollable adaptive grid |

**Navigating within compare mode:**

- `Left` / `Right` — move the focus ring to the previous/next tile. The focused tile is marked with a white inner ring inside the orange selection border.
- `Up` / `Down` / `Escape` — collapse the selection to the focused tile and return to single-image view.
- Click any tile — collapse to that image and return to single-image view.

**Context menu in compare mode:**
- **Clear Selection** — collapses to the focused tile
- **Select All** — adds all folder images to the selection
- **Sort By** — reorders the folder list (see Sorting)

Zoom, info bar, toolbar icons, and crop/resize are not available while compare mode is active.

---

## Keyboard Shortcuts

### Single-Image Mode

| Key | Action |
|-----|--------|
| `Left Arrow` | Previous image |
| `Right Arrow` | Next image |
| `Shift+Left Arrow` | Rotate counter-clockwise |
| `Shift+Right Arrow` | Rotate clockwise |
| `Up Arrow` | Zoom in |
| `Down Arrow` | Zoom out |
| `Shift+Up Arrow` | Expand window to fill screen |
| `Shift+Down Arrow` | Reset zoom to fit |
| `Space` | Toggle Fit / Actual Size |
| `T` | Toggle thumbnail strip |
| `Cmd+A` | Select all images (enters compare mode) |
| `Return` | Start rename for current image |
| `Escape` | Quit BlickPix |

### Rename Mode

| Key | Action |
|-----|--------|
| `Return` | Confirm rename |
| `Escape` | Cancel rename |

### Compare Mode

| Key | Action |
|-----|--------|
| `Left Arrow` | Move focus to previous tile |
| `Right Arrow` | Move focus to next tile |
| `Up Arrow` / `Down Arrow` / `Escape` | Collapse to focused tile, return to single view |
| `T` | Toggle thumbnail strip |
| `Cmd+A` | Select all images |

---

## Mouse and Trackpad

| Action | Result |
|--------|--------|
| Hover canvas | Reveal title bar, export button, info bar, toolbar icons |
| Double-click title | Start rename |
| Right-click canvas | Open context menu |
| Scroll wheel (vertical) | Zoom in / out |
| Pinch on trackpad | Zoom in / out |
| Two-finger horizontal swipe | Previous / next image (only when not zoomed in) |
| Click thumbnail | Jump to that image |
| `Cmd`+click thumbnail | Toggle selection |
| `Shift`+click thumbnail | Extend selection range |

---

## Image Info Bar

Hovering the canvas reveals a subtle bar along the bottom of the image showing:

- Current zoom percentage
- Image dimensions (width × height in pixels)
- File size on disk

The bar sits on a dark gradient so it remains legible over any image. It is hidden during crop, during compare mode, and when the window is too narrow to show it without overlapping the bottom-right toolbar — the toolbar icons take priority and the info bar reappears once the window is wide enough.

---

## Title and Window Chrome

When hovering, the filename appears centered at the top of the canvas. BlickPix automatically samples the top portion of the image and switches the window title bar between light and dark appearance so the title is always readable regardless of what's behind it.

---

## Feedback Toasts

After a successful export or rename, a small message briefly appears above the filename pill confirming the operation (for example "Saved as photo.png" or "Renamed to photo.jpg"). It fades automatically after two seconds.

---

## Recursive Subfolder Scan

The **folder** icon in the bottom-right toolbar toggles recursive scanning.

- When off (default): only images in the same folder as the opened file are included
- When on (icon turns blue): all images in that folder and every subfolder are included as a single flat list
- Toggling rescans immediately and repositions to the current image

---

## Bottom-Right Toolbar

Four icon buttons appear in the bottom-right corner when hovering. They are hidden during crop and during compare mode.

| Icon | Action |
|------|--------|
| Crop square | Open in-canvas crop overlay |
| Resize arrows | Open resize dialog |
| Strip rectangle | Show / hide the thumbnail strip (same as `T`); accent-coloured when the strip is visible |
| Folder | Toggle recursive subfolder scan |

Crop and Resize are disabled when no image is loaded. Strip and Folder always work.

---

## Animated GIFs

Animated GIFs play automatically when opened. Frame timing is read from the file metadata. Navigating away stops playback immediately.

---

## Image Rotation

`Shift+Left` and `Shift+Right` rotate the current image 90° at a time. Rotation is session-only — it does not write to disk. Use Export to save the rotated result.

---

## Resize

Open via the toolbar resize icon or right-click → **Resize…**

- Enter a target width or height; the other dimension updates automatically (aspect ratio locked)
- Click **Resize** to apply, **Cancel** to dismiss
- The resize is session-only — use Export to save it to disk
- The window resizes automatically after the operation

---

## Crop

Open via the toolbar crop icon or right-click → **Crop…**

- A crop overlay appears directly on the canvas with a draggable selection rectangle
- **Drag a corner handle** to resize the crop region
- **Drag the interior** to reposition it
- A rule-of-thirds grid is shown inside the selection for composition reference
- The result size in pixels is shown live as you drag
- Press **Return** or click **Crop** to apply; press **Escape** or click **Cancel** to dismiss
- The crop is session-only — use Export to save it to disk
- Window resizing is disabled while the crop overlay is active

---

## Export

Open the export panel via the circle icon (top-right, on hover) or right-click → **Export As** / **Quick Export…**

**Export As** — choose a format from the submenu; the export panel opens immediately with that format pre-selected.

**Quick Export…** — re-opens the export panel with the last used format pre-selected.

### Export Formats

| Format | Notes |
|--------|-------|
| JPEG | Quality slider available |
| PNG | Lossless; quality slider hidden |
| HEIC | Quality slider available |
| AVIF | Quality slider available |
| JPEG XL | Quality slider available |

When the exported file is saved into the same folder currently being browsed, the thumbnail strip automatically updates to include it.

---

## Rename

Start rename via `Return`, double-clicking the title, or right-click → **Rename…**

- The title bar becomes an editable text field pre-filled with the base filename (no extension)
- The file extension is always preserved automatically
- Press `Return` to confirm, `Escape` to cancel
- Rename is blocked if: the target name already exists, the name is unchanged, or the name contains invalid characters (`/`, `:`, `\`)

---

## Sorting

Right-click → **Sort By** to change the order images are listed in:

| Order | Description |
|-------|-------------|
| Name | Alphabetical |
| Date Modified | Most recently modified first |
| Date Created | Most recently created first |

Sort order is saved and restored between sessions. It affects left/right navigation order, the thumbnail strip order, and the index position shown in the filename overlay.

---

## Zoom and Window Sizing

In **Fit** mode, the window resizes to match the image at the current zoom level. No black bars — the window is always exactly the image's aspect ratio.

In **Actual Size** mode, one image pixel equals one screen pixel (so a 1000 px wide image appears as 500 points on a Retina display). A scrollable view lets you pan around.

- `Up` / `Down` — zoom in or out in 10% steps
- `Shift+Up` — expand the window to 95% of the available screen
- `Shift+Down` — reset to default fit zoom
- `Space` — toggle between Fit and Actual Size
- Scroll wheel and pinch-to-zoom work in both modes
- Two-finger horizontal swipe navigates to the previous/next image when not zoomed in

---

## Context Menu (Single-Image Mode)

| Item | Action |
|------|--------|
| Rename… | Start rename for current image |
| Resize… | Open resize dialog |
| Crop… | Open in-canvas crop overlay |
| Export As | Submenu with all export formats |
| Quick Export… | Export with last used format |
| Sort By → Name | Sort folder by filename |
| Sort By → Date Modified | Sort by modification date |
| Sort By → Date Created | Sort by creation date |
| Reveal in Finder | Show current file in Finder |

---

## Settings

Open with **BlickPix → Settings…** or **`Cmd+,`**. Three tabs:

### General

| Setting | Effect |
|---------|--------|
| Background | Background colour for the canvas and window. Click the colour well to pick any colour; **Reset** restores black. Applied live. |
| Default Export Format | Format pre-selected when the export panel opens. Picking a different format inside the panel updates this setting. |

### Permissions

A list of folders BlickPix can access without prompting on launch. Useful for any folder you regularly browse from Finder.

- **Add Folder…** opens a directory picker. Pick a folder once; BlickPix remembers it across launches.
- The minus button next to a folder revokes access.
- Subfolders inside an added folder are also accessible — you do not need to add each one.

This uses macOS security-scoped bookmarks. Sandbox rules require the initial pick to go through the system file dialog; you cannot type a path.

### License

(Website / direct-download version only.)

Before activation, this tab is the same as the launch screen — enter your Payhip license key and click **Activate**. Each key activates on up to two Macs.

After activation, this tab shows your registered email, a masked license key, and the activation date, plus a **Deregister** button. Deregistering frees up an activation slot so you can move BlickPix to another Mac, but you remain licensed on the current Mac for the rest of the session.

The Mac App Store version does not have this tab — purchases are tied to your Apple ID and verified by the system.

---

## Activation

(Website / direct-download version only.)

The first time BlickPix launches, an activation screen asks for your Payhip license key. Enter the key and click **Activate**. Once activated, BlickPix opens directly into the canvas on every subsequent launch. Closing the activation window quits the app — there is no trial mode.

License keys are bound to the Mac they were activated on. If you move BlickPix to another Mac, deregister first via **Settings → License → Deregister** to free up an activation slot.

---

## Quick Reference

| Action | Shortcut |
|--------|----------|
| Open file | `Cmd+O` |
| Open Settings | `Cmd+,` |
| Previous / Next | `Left` / `Right` |
| Rotate left / right | `Shift+Left` / `Shift+Right` |
| Zoom in / out | `Up` / `Down` |
| Fill screen / reset zoom | `Shift+Up` / `Shift+Down` |
| Fit / Actual Size | `Space` |
| Toggle thumbnail strip | `T` |
| Select all | `Cmd+A` |
| Start rename | `Return` or double-click title |
| Confirm rename | `Return` |
| Cancel rename | `Escape` |
| Collapse compare mode | `Up` / `Down` / `Escape` |
| Quit | `Escape` |

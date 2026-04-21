# CMS Auction Builder

Merged tool combining the OBS Auction Scene Renamer and the Banner Generator into
one workflow driven by a single **Working On CSV** upload.

## Files

- `index.html` — the application (open in a browser, or serve from your repo)
- `template.json` — OBS scene collection template (unchanged from the original renamer)
- `assets/states/` — state images (unchanged from the original banner generator)

## Setup

Host this as a static site in the same repo you used for the banner generator.
The tool reads `template.json` from the same directory as `index.html` and reads
state images from your GitHub repo's `assets/states/` folder (configured in the
State Library admin tab — same settings as before, PIN still `0623`).

## Flow

1. **Upload Working On CSV** — shows lot/option/breed stats.
2. **Pick styles** — choose Style 1 (Diagonal) or Style 2 (Clean) for transition
   banners and for option banners independently.
3. **Review & download**:
   - **Step 1 on the page**: Click "Download All Banners (ZIP)". Unzip the
     archive into `/Users/brysonmurray/Library/CloudStorage/Dropbox/Auction OBS/Lot Banners/`
     — keep the filenames exactly as they come out.
   - **Step 2 on the page**: Click "Download OBS Scene Collection" (only enabled
     after the banners have been downloaded at least once). In OBS: Scene
     Collection → Import.

## Banner file naming

- Standard lot: `Lot_402_Transition.png`
- Option lot transition: `Lot_401-A_Transition.png`, `Lot_401-B_Transition.png`, ...
- Shared option banner: `Lot_401-Option.png` (one file per option group,
  referenced by all non-last Video scenes in that group)

## Banner placement inside OBS

- Transition banners: full width, y = 880 (bottom edge flush with 1080p canvas)
- Option banners: full width, y = 0 (top edge flush)

## Hardcoded path

Banner image sources in the OBS JSON point to:
`/Users/brysonmurray/Library/CloudStorage/Dropbox/Auction OBS/Lot Banners/{filename}`

Change the `DROPBOX_BANNER_PATH` constant at the top of the `<script>` block in
`index.html` if you ever need to move this.

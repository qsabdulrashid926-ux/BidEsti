# BidEst QTO — NRM2 quantity take-off

A browser-based quantity take-off and Bill of Quantities tool measured to **RICS NRM2**.
Everything runs in the browser: no server, no database, no build step.

## What it does

**Page 1 — Inputs** holds every main input:

- Levels: existing ground level (EGL), typical bottom of footing (BOF), top of grade slab, blinding thickness and projection, working space
- Typical dimensions, used wherever a schedule cell is left blank
- Manual schedules: footings, necks, tie and grade beams, grade slab, columns, shear walls, beams, floor and roof slabs, stairs, blockwork types and walls, doors and windows, room finishes, and civil and external works
- Specifications, which appear in the BOQ descriptions, and reinforcement densities

**Take-off pages, one per NRM2 work section**, show every quantity as Times × Length × Width × Depth:

| Section | Covers |
|---|---|
| 05 Excavating and filling | Footing pits and beam trenches from EGL to (BOF − blinding), make-up fill, sub-base, backfill, disposal, anti-termite |
| 11 Concrete | Blinding (area), footings, necks, tie beams, grade beams, grade slab, columns, shear walls, beams (net below slab), slabs, roof slab, stairs |
| 11 Formwork | All contact areas |
| 11 Reinforcement | Estimated from kg/m³ densities, plus fabric mesh |
| 14 Masonry | Net area by block type, with openings over 0.5 m² deducted |
| 19 Waterproofing | Under footings; around footings (sides and top); necks and beams below EGL; under beams; polyethylene under grade slab; roof membrane; roof insulation |
| 23 / 24 | Windows and doors |
| 28 / 29 / 30 | Plaster, render, floor finishes, skirting, wall tiling, paint, ceilings |
| 34–36 | Drainage, site works, fencing (manual items) |

The **Bill of quantities** page has rate entry, section totals and a summary. You can export to Excel (.xlsx) or CSV, or print it.

Projects save automatically in the browser (localStorage). Use **Save project (.json)** to back up a project or move it to another computer.

## Publish on GitHub Pages

1. Create a new repository on GitHub, for example `bidest-qto`.
2. Upload `index.html`, `README.md` and `LICENSE` with **Add file → Upload files**, then **Commit**.
3. Go to **Settings → Pages**. Under *Build and deployment* choose **Deploy from a branch**, branch `main`, folder `/ (root)`, then **Save**.
4. After a minute the app is live at `https://<your-username>.github.io/bidest-qto/`.

To run it locally, double-click `index.html`. It works offline, except Excel export and the web fonts, which load from CDNs.

## Measurement rules applied

- Excavation is taken from EGL to BOF minus the blinding thickness. Plan size is the footing plus the blinding projection and the working space on each side.
- Backfill = excavation − blinding − footing concrete − necks below EGL. Beam trenches are backfilled separately.
- Disposal = (excavated − backfilled) × bulking factor.
- Necks run from the top of the named footing up to the underside of the grade slab, unless a top level is given.
- Beams are measured net below the slab. Columns are measured to the height entered (typically the clear height to the slab soffit).
- Openings ≤ 0.5 m² are not deducted (NRM2). The threshold can be changed on Page 1.

## Limitations

- Reinforcement from densities is an **estimate**. Replace it with bar-bending schedule totals before tender.
- Overlap between beam trenches and footing pits is not deducted.
- A single EGL applies across the whole site.
- Quantities depend entirely on the dimensions entered, so check them against the drawings.

## Licence

MIT — see `LICENSE`.

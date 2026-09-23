# Embryo Injection Bench

A browser game for practising **Drosophila embryo microinjection** before you touch real embryos. It walks a newcomer through a full session, from a sealed needle to imaging at nuclear cycle 11, with the same order of steps, time pressure and failure modes as the bench. The clock simply runs faster.

It is a single self-contained file (`index.html`). There is nothing to install and no server. Open it in a browser and play.

> Current version: **v6.2** (shown in the game's header).

## Quick start

1. Download `index.html` (or open the GitHub Pages link).
2. Open it in Chrome, Edge, Firefox or Safari on a computer.
3. Pick your settings on the start screen and press **Enter** (or click *Put flies on the plate — start*).

Phones are only partly supported for now: the game runs, but the layout and controls were designed for a keyboard and a larger screen.

## A session in six steps

| Step | What you do | What can go wrong |
| --- | --- | --- |
| 1. Break the needle | Drive the sealed tip into the coverslip edge. Speed at contact sets how much glass snaps off. | A hard crash leaves a wide opening that leaks and pushes embryos off the glue. |
| 2. Test the flow | Hold Pressure in the oil and watch the droplet. | No droplet means a glass shard is blocking the tip. A gush means the opening is too wide. |
| 3. Line up | Check the glue, then drag embryos from the double-sided tape onto the glue strip. | Embryos dry from the moment they leave the plate. Old embryos (translucent edge) and bad glue spoil the row. |
| 4. Desiccate | Top up drying until the embryos look slightly baggy. | Full embryos push liquid back out. Shrivelled ones die. |
| 5. Inject | Line each embryo up, go in, give a small dose, and come out before moving the stage. | Overfilling, going through the embryo, tearing it, clogging, or running out of time. |
| 6. Develop and image | Choose the incubator temperature and time so embryos reach cycle 11. | Imaging too early or too late, or the mRNA not yet translated. |

The results screen shows a simulated fluorescence image of every embryo, coach's notes on what to fix, and a word of encouragement from **Dr. R** (with a fruit fly buzzing about — tap it).

## Controls

| Key | On screen | Action |
| --- | --- | --- |
| ◀ ▶ or A D | arrow pad | Needle out / in (hold to speed up) |
| ▲ ▼ or W S | arrow pad | Move the stage |
| Space | PRESSURE | Hold to push liquid out |
| E | SUCK | Hold to draw liquid back |
| Enter | highlighted button | Next step (press twice to end injection early) |
| R · N | buttons | Re-crash the needle · mount a new needle |
| B | button | Back to the tape to line up more embryos |
| G · V · Z | buttons | Add heptane to the glue · new glue vial · ×3 magnifier (line-up) |
| P · H | header | Pause · trainer aids on/off |
| mouse / touch | drag | Move embryos from the tape to the glue |

## Settings

- **Embryo layout:** horizontal (long axis to the needle, pole injection) or vertical (side injection).
- **Embryos on the tape:** 8, 15, 20, 30 or 40.
- **Difficulty:** Trainee, Standard, Hard or Expert. Harder levels make the clock faster and the injection window shorter, with more blockages and faster drying.
- **Injecting:** mRNA (needs time to be translated), fluorescent beads (jam narrow tips) or labelled protein (thick, flows slowly).
- **Room temperature:** 25 °C or 22 °C.
- **Scenarios:**
  - *Blocked mid-session*
  - *Late to the bench*
  - *Under-dried batch*
  - *Last needle*
  - *Microscope booked*
- **Sham plate first:** fewer old, retained eggs on the tape.
- **Trainer aids:** show the numbers (opening size, dose, dryness, cycle, glue) or judge everything by eye.

## Changing the science

All the tunable numbers are near the top of the script. Open the file in any text editor and search for **`§1 CONFIG`**. A table of contents at the start of the script lists all 15 sections (`§1`–`§15`), so you can jump to any part by searching for its marker.

| To change | Search for |
| --- | --- |
| When each nuclear cycle starts | `const CYC` |
| Difficulty levels | `const DIFFS` |
| Materials (flow, clogging, mRNA delay) | `const MATS` |
| Temperature speed-ups | `TEMP_RATE` |
| Scenarios | `const SCENS` and `applyScenario` |
| Glue vial odds | `function vialConc` |
| How much glass snaps off per hit | `function breakTip` |
| Leakage rule | `function withdraw` |
| Death threshold | `function dmgOf` |
| What counts as a usable embryo | `function evaluate` |
| Dr. R's quotes | `DRR_QUOTES` |

Change one number at a time, save, reload the page and play a session. If you share a changed copy, bump the version tag in the header.

## What the model simplifies

The numbers are teaching approximations, not measurements:

- **Cycle timing:** cycle 11 starts about 88 min after laying at 25 °C.
- **Temperature:** 22 °C runs at 0.8× and 18 °C at 0.5× the 25 °C speed.
- **Dose:** 150–500 pL counts as a good dose.
- **Materials:** mRNA takes about 40 min to show a signal, and beads need at least a 1.4 µm opening.
- **Glue:** the concentrations and how often vials go bad are guesses.

The needle moves along one axis only: there is no focus, angle or compensation pressure. The fluorescence image is a stylised picture. The game has been tested in Chrome, and personal bests are saved only in the browser you play in.

## Files

- `index.html` — the game (everything, including artwork, is inside this one file)
- `checkpoints/` — earlier saved versions

## Credits

Designed by Isaac Wong (Raff lab, University of Oxford), based on the lab's microinjection routine and embryo staging notes. Dr. R portrait and fruit-fly artwork supplied by Isaac Wong. Built with help from Claude.

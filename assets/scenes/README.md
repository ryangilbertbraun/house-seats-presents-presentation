# Scene art — drop your illustrations here

The opening gallery (`gallery.html`) animates illustrated scenes. It works right
now with procedural flat-Deco placeholders; drop real images here and name them
in the `SCENES` manifest (top of the `<script>` in `gallery.html`) to upgrade
each scene in place.

## What to generate (ChatGPT / DALL·E 3 or Adobe Firefly)

Use this **shared style line** on every image so the set is cohesive:

> Flat Art Deco illustration, 1920s jazz-age, bold simple geometric shapes,
> deep plum/burgundy background with warm gold and soft violet accents, elegant
> silhouetted figures, editorial poster style, symmetrical, clean vector-like
> linework, NO text, cinematic but minimal.

### Full scenes — 1600×900 (16:9), landscape

| filename       | prompt (append the shared style line)                                                                                                                                                                                |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `facade.jpg`   | A grand Art Deco theater / supper-club façade, straight-on, symmetrical, a central marquee and several tall arched lit windows in a grid — each window a small glowing nightlife vignette. Ornate stepped rooflines. |
| `showroom.jpg` | A packed Art Deco supper-club showroom, a lit stage, an audience seated at candlelit tables, warm spotlights.                                                                                                        |
| `dining.jpg`   | An opulent Art Deco dining room, candlelit tables, a maître d', warm gold light.                                                                                                                                     |
| `tour.jpg`     | A row of Art Deco theater façades receding into a city skyline of glowing marquees at dusk, symmetrical avenue perspective.                                                                                          |

### Window vignettes — square, TRANSPARENT PNG (optional, richer parallax)

| filename          | prompt                                                                                        |
| ----------------- | --------------------------------------------------------------------------------------------- |
| `win-stage.png`   | just a small stage with a singer at a microphone, framed by a curtain, transparent background |
| `win-table.png`   | just an elegant candlelit dinner table for two, transparent background                        |
| `win-box.png`     | just a vintage box-office ticket window with a glowing sign, transparent background           |
| `win-marquee.png` | just a lit Art Deco marquee sign, blank (no letters), transparent background                  |

Tips: say "no text/letters" so signage stays clean; generate 3–4 of each and keep the best.

---

## Layered animation (making small elements move)

Two ways to add motion, and they stack:

### 1) Procedural accents (already on — no art needed)

The façade scene already animates flickering window glows, a sweeping entrance
spotlight, and drifting light motes drawn in code over `facade.png`. Tune them
in the manifest via `accents: [...]`, `spotX`, and the `windows` ratio boxes.

### 2) Real layered art (most like Archidirectors)

Generate each moving piece as its OWN image, **same 16:9 framing as the base**,
on a **pure solid black background** (for light layers we screen-blend, so black
drops out — no transparency needed). Only solid objects (a crowd) need true
transparency (use Adobe Firefly's transparent toggle or remove.bg).

Drop into `assets/scenes/` and uncomment the `layers` block in the manifest.

| filename             | ChatGPT prompt                                                                                                                                                                                                                                                     | how it's animated                     |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------- |
| `facade-glow.png`    | Flat Art Deco, 16:9. ONLY the warm glowing light from a grid of tall arched theater windows (three rows), soft gold/amber glowing shapes matching a symmetrical façade + central entrance glow. Everything else PURE SOLID BLACK. No building, no people, no text. | `blend:"screen", motion:"flicker"`    |
| `facade-rays.png`    | Flat Art Deco, 16:9. Soft warm gold spotlight beams / god-rays fanning down from top center. PURE SOLID BLACK background, nothing else. No building, no text.                                                                                                      | `blend:"screen", motion:"sweep"`      |
| `facade-marquee.png` | Flat Art Deco, 16:9. ONE lit art deco marquee canopy centered, BLANK (no letters), glowing gold. PURE SOLID BLACK background, nothing else.                                                                                                                        | `blend:"screen", motion:"pulse"`      |
| `facade-crowd.png`   | Flat Art Deco, 16:9. A row of elegant 1920s guests (gowns, tuxedos, top hats) as small silhouettes arriving at a theater entrance, centered. PURE SOLID BLACK background. (Then remove background: remove.bg or Firefly transparent.)                              | `blend:"source-over", motion:"drift"` |

**Motions available:** `flicker`, `pulse`, `sweep`, `drift`, `float` (with optional `amp` and `speed`).

---

## Scenes 2–5 — image prompts (drop into assets/scenes/, set `art:` in the manifest)

Use the shared style line above on each. 16:9 landscape.

**Composition rule (important):** the scene's copy sits on one side, so the image
must keep the OTHER side dark/empty for legibility. Match the scene's `layout`:

- `layout: "right"` → copy on the RIGHT → put the subject LEFT, keep the **right third** dark
- `layout: "left"` → copy on the LEFT → put the subject RIGHT, keep the **left third** dark
- `layout: "lower-band"` → copy across the BOTTOM → keep the **lower third** dark
- `layout: "center"` / `"hero"` → copy centered → keep the **center** calmer, detail to the edges

| filename          | scene / layout                   | prompt                                                                                                                                                                                                                                                                                                                                                                                                |
| ----------------- | -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `boxoffice.png`   | 3 · The Booking (`right`)        | An Art Deco theater box office at night — a vintage ticket window with a glowing gold "SOLD OUT" sign above it, ornate geometric grillwork, a single elegant 1920s attendant silhouette behind the glass. Warm amber light pooling from the window. Subject in the **left two-thirds**; the **right third is empty deep-plum shadow** for text. No readable text besides a suggested glowing sign.    |
| `newsstand.png`   | 4 · On the Bill (`left`)         | An opulent Art Deco newsstand at night — a glowing display of elegant magazines / a weekly journal fanned out, warm editorial gold light, an elegant 1920s figure browsing. Subject in the **right two-thirds**; the **left third is empty deep-plum shadow** for the copy + section list. No readable cover text.                                                                                    |
| `fouracts.png`    | 5 · The Four Acts (`left`)       | A row of grand Art Deco theater marquees receding down a glowing avenue into a city skyline at dusk — four lit marquees getting bigger toward the front, suggesting a show that grows into a national tour. Warm gold marquee light against deep plum sky. Subject/perspective weighted in the **right two-thirds**; the **left third is empty deep-plum shadow** for text. No readable marquee text. |
| `compounding.png` | 6 · The Box Office (`right`)     | An Art Deco box-office interior at night — an ornate ticket-booth cash drawer with neat stacks of gold coins and cash growing taller left to right (a rising staircase of receipts), warm amber light, geometric deco detailing. Subject in the **left two-thirds**; the **right third is empty deep-plum shadow** for text. Painterly, no readable text.                                             |
| `blueprint.png`   | 7 · The Set Design (`center`)    | An architect's drafting table / blueprint — elegant deco building elevations and floor plans in fine gold linework on deep plum drafting paper, compass and ruler, warm lamp light. Keep the **center calmer/darker** (a pool of shadow) so an overlaid window reads on top; detail toward the edges/corners. Painterly, no readable text.                                                            |
| `thehouse.png`    | 8 · The House / funnel (`right`) | The grand interior of an Art Deco theater auditorium seen from the stage — rows of plush seats filling with an elegant 1920s audience, a warm glowing house, ornate balconies and a domed ceiling. Subject/interior in the **left two-thirds**; the **right third is empty deep-plum shadow** for the funnel. Painterly, no readable text.                                                            |

To wire one in: set `art: "assets/scenes/boxoffice.png"` (etc.) on that scene in
the `SCENES` manifest in gallery.html — the procedural placeholder is replaced
automatically and the subtle flourishes stay on top.

`playbill.png` (scene 2 · The Program, `left`) and `facade.png` (scene 1, `hero`)
are already generated and wired.

## Scenes 9–16 — remaining prompts (same shared style prefix)

Style prefix for every one: _Flat Art Deco illustration, 1920s jazz-age, hand-painted poster style (not 3D, not futuristic), warm gold + soft violet on deep plum-black, cinematic, muted plum (#2a1840) / deep violet / antique gold (#f4c56a), no readable text, 16:9._

| filename          | scene / layout                          | subject-specific prompt (append to prefix)                                                                                                                  | negative space                 |
| ----------------- | --------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------ |
| `preview.png`     | 9 · The Preview (`lower-band`)          | A theater stage during a dress-preview rehearsal — a spotlight on a half-raised curtain, a few figures in the front row, anticipation before opening night. | lower third dark               |
| `schedule.png`    | 10 · Production Schedule (`left`)       | A backstage production call-board / stage-manager's desk — clipboards, cue cards, a clock, a warm lamp, suggesting a timeline.                              | left third dark                |
| `ticket.png`      | 11 · Ticket Economics (`left`)          | An elegant deco theater ticket + season-pass booklet on velvet, gold foil edges, a few gold coins, intimate light.                                          | left third dark                |
| `workorders.png`  | 12 · The Work Orders (`center`)         | A staged ladder of ornate numbered framed act-panels ascending, suggesting gated commitments.                                                               | center calmer, detail to edges |
| `stagemgmt.png`   | 13 · Stage Management & Risk (`center`) | A backstage stage-manager's control desk — levers, cue lights, rigging overhead, the theater wings.                                                         | center calmer, detail to edges |
| `theask.png`      | 14 · The Ask (`center`)                 | A single grand spotlight pool on center stage, velvet curtain behind, an air of decision + invitation.                                                      | center darkest, glow to edges  |
| `curtaincall.png` | 15 · Curtain Call (`center`)            | A triumphant curtain call — performers bowing under applause light, drawn curtain, glowing footlights.                                                      | center calmer, detail to edges |
| `services.png`    | 16 · Services addendum (`center`)       | A deco theater atelier — drafting compass, paintbrush, typewriter, film reel, megaphone arranged elegantly (full-service house).                            | center calmer, detail to edges |

## The House Floor (community scene)

| filename         | scene / layout                 | subject-specific prompt (append the shared style prefix)                                                                                                                                                                                                                                                                                                                | negative space                 |
| ---------------- | ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------ |
| `housefloor.png` | 4 · The House Floor (`center`) | A lively Art Deco grand lobby / mezzanine where elegant 1920s guests mingle and converse in small groups — the social heart of a theater, warm and buzzing, a sense of connection and conversation. Keep the **center calmer/darker** so the four feature cards read on top; concentrate the crowd + deco detail toward the edges/corners. Painterly, no readable text. | center calmer, detail to edges |

# G1105 Glow-Up — Handoff

Pick this up on the Mac (where Claude Code can actually drive Chrome and use the
Firefly session) and finish the job: **generate the 5 renders, drop them in
`images/`, preview, and deploy.** Everything else is already built and on the
branch `claude/apartment-decor-ideas-UZyLl`.

---

## TL;DR for whoever runs this on the Mac

1. **Generate 6 images in Adobe Firefly** (1 hero + 5 zones) using the prompts in
   the table below. Save each with the **exact filename** into `g1105/images/`.
2. **Preview** the site locally (`npx wrangler dev`) — the renders auto-appear in
   their slots; the page already handles missing images gracefully.
3. **Deploy** (`npx wrangler deploy`) so it goes live at
   `https://pointless-websites.com/g1105/`.
4. Commit the images on the same branch.

> **Why this is a handoff, not done already:** the cloud session that built this
> page runs in an isolated container with **no browser control and no access to
> the user's Firefly account** — it physically cannot drive Chrome or spend the
> user's Firefly credits. A local Claude Code on the Mac (with computer-use /
> browser tooling) can. Hence: handoff.

---

## The project in one paragraph

Unit **G1105 at Camden Tempe** (Tempe, AZ) is a one-bedroom in the cool
**Contemporary** finish (gray shaker cabinets, gray wood-look floor, off-white
walls). It currently reads cold, cluttered, and unfinished. Goal: a **warm
desert-modern reset** — walnut, cognac leather, cream linen, terracotta, sage,
brass against the cool gray. Constraints: **portable, no-drill, no-paint,
dog-proof.** Budget **$1.5k–$3.5k**. Full plan, palette, budget, and an
interactive checklist live in `index.html`.

**Real dimensions (from the floor plan, APT 1004 layout):**
- Living **13'6" × 10'4"** → 82" sofa, standard depth, **not** a sectional
- Dining/Office nook **6'3" × 9'3"** → one job only; the round walnut table = desk + dining
- Bedroom **12'5" × 13'0"**
- Ground-floor **patio + storage closet**, plus a real **foyer**

**Already owned (design around these):** round walnut table, dark espresso
platform bed, wood dresser, desert/cactus canvas, pampas grass, a floor lamp.

---

## Step 1 — Generate the renders in Firefly

Open **Chrome → firefly.adobe.com → "Text to image."** For each row: paste the
prompt, set **Content type: Photo**, set the **Aspect**, generate, pick the best
variation, **download**, and save it to `g1105/images/` with the **exact filename**.

The full, copy-ready prompt text for each is in `index.html` (each zone has a
**"Copy prompt"** button) — or pull them from the table below.

| # | Save as | Aspect | What it is |
|---|---------|--------|------------|
| 1 | `images/hero.jpg` | 16:9 Widescreen | Hero — the whole warm living great room (becomes the masthead background) |
| 2 | `images/living.jpg` | 16:9 Widescreen | Living room zone |
| 3 | `images/office.jpg` | 16:9 Widescreen | Office/dining nook with the round walnut table |
| 4 | `images/entry.jpg` | Portrait or Square | Entry / foyer console + mirror |
| 5 | `images/bedroom.jpg` | 16:9 Widescreen | Bedroom around the espresso platform bed |
| 6 | `images/patio.jpg` | 16:9 Widescreen | Ground-floor desert patio |

**Tips for matching reality:** every prompt already specifies *cool grey
wood-look floor + off-white walls* so the renders look like *this* apartment, not
a generic showroom. Keep that phrasing if you regenerate. Favor variations with
**warm golden light and visible plants** — that's the whole point.

### The prompts (verbatim)

**hero.jpg / living.jpg** (same scene; use the strongest variation for the hero)
> Photorealistic interior photograph of a small modern one-bedroom apartment
> living room in warm desert-modern style. Cool grey wood-look plank flooring and
> soft off-white walls. An 82-inch cognac tan leather sofa with slim walnut legs
> against the long wall, a round walnut coffee table, a layered cream and
> muted-terracotta low-pile rug, a large leaning arched mirror, framed desert and
> cactus art, woven jute and boucle textures, terracotta and sage throw pillows,
> brass and matte-black accents, abundant healthy green potted plants including a
> tall bird of paradise and small cacti in terracotta pots and woven baskets.
> Warm golden-hour Arizona sunlight through floor-to-ceiling oatmeal linen
> curtains; layered table and floor lamps glowing warm. Calm, uncluttered,
> inviting, editorial magazine quality, 35mm, natural light, shallow depth of field.

**office.jpg**
> Photorealistic interior photograph of a compact home-office and dining nook in a
> modern apartment, warm desert-modern style. A round walnut wood table used as
> both a two-person dining table and a desk, paired with a single mid-century
> chair and a comfortable woven task chair. Cool grey wood-look floor, off-white
> wall, a large window with oatmeal linen curtains hung high and wide. A small
> cream rug defines the zone, one tall potted plant in a woven basket, a warm
> brass task lamp, a framed minimalist desert print leaning on the wall, a few
> books and a ceramic vase, cables hidden. Bright warm natural daylight, tidy and
> intentional, editorial magazine quality, 35mm, shallow depth of field.

**entry.jpg**
> Photorealistic interior photograph of a small modern apartment entryway, warm
> desert-modern style. A slim walnut console table with closed cabinet shoe
> storage against an off-white wall, a round brass-framed mirror leaning above it,
> a tall vase of pampas grass, a small terracotta tray for keys, one potted
> trailing plant, a woven runner on cool grey wood-look flooring. Warm inviting
> lighting, soft daylight from around the corner, uncluttered and welcoming,
> editorial magazine quality, 35mm, shallow depth of field.

**bedroom.jpg**
> Photorealistic interior photograph of a calm modern bedroom in warm
> desert-modern style. A low dark espresso wood platform bed with a headboard,
> dressed in layered cream and oatmeal bedding with a terracotta throw blanket and
> textured pillows. Cool grey wood-look floor, off-white walls, a soft greige area
> rug under the bed. Floor-to-ceiling oatmeal linen curtains framing the window, a
> large piece of minimalist desert art leaning above the headboard, matching
> warm-toned table lamps on wood nightstands, a potted plant in the corner, brass
> accents. Soft warm morning light, serene and inviting, editorial magazine
> quality, 35mm, shallow depth of field.

**patio.jpg**
> Photorealistic photograph of a small ground-floor apartment patio in Tempe
> Arizona, warm desert-modern style. Two comfortable lounge chairs with cream and
> terracotta cushions, a small round side table, an indoor-outdoor rug in warm
> earth tones, warm string lights overhead, a cluster of potted cacti and agave
> and succulents in terracotta pots, a woven basket planter. Golden-hour desert
> light, warm and inviting, cozy outdoor living, editorial magazine quality, 35mm,
> shallow depth of field.

> **Optional, even better:** Firefly's **"Generative fill" / reference image**
> can take a real photo of the room and restyle it. If you upload the actual
> living-room and bedroom photos and prompt with the same wording, the renders
> will match the true geometry of G1105. Worth trying for `living.jpg` and
> `bedroom.jpg`.

---

## Step 2 — Preview locally

```bash
cd pointless-websites.com
npx wrangler dev        # serves the whole site; open the printed localhost URL
# visit /g1105/ — renders fill their slots as soon as the files exist
```

The page is a single static `index.html`, no build step. Missing images are
handled (each slot shows a labeled placeholder until its file is added).

## Step 3 — Deploy

```bash
cd pointless-websites.com
npx wrangler deploy     # publishes to Cloudflare → https://pointless-websites.com/g1105/
```

(Requires the Cloudflare account that owns the `pointlesswebsites` worker — config
is in `wrangler.jsonc`. If `wrangler` isn't logged in, run `npx wrangler login`.)

## Step 4 — Commit the images

```bash
git add g1105/images/*.jpg
git commit -m "Add Firefly renders for the G1105 glow-up page"
git push -u origin claude/apartment-decor-ideas-UZyLl
```

---

## Still needed from Tyler

- [ ] **Photo of the round walnut table** (the "this —" message got cut off). Confirm:
      is it the **dining/office** table (assumed) or a **coffee table**? Changes Zone 02.
- [ ] **Patio photo** + rough size — to tailor Zone 05 furniture.
- [ ] **Tape-measure confirm** of the living-room sofa wall (~13'6" assumed) before buying the sofa.

## File map

```
g1105/
├── index.html        # the page (plan, palette, budget, interactive checklist, prompts)
├── HANDOFF.md        # this file
└── images/           # drop the 6 Firefly renders here (hero, living, office, entry, bedroom, patio)
```

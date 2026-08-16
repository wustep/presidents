# Presidents — Ruleset Builder

A single-page tool for assembling a house ruleset for **Presidents** (a.k.a. Scum, Asshole, Capitalism, Landlord — and upstream, the Japanese climbing game 大富豪 *Daifugō*).

Start from the base game everyone already knows. Toggle mechanics on. The rule sheet rewrites itself, and tells you what each addition costs in teaching time and what it quietly breaks.

**Live:** <https://presidents-zeta.vercel.app>

---

## Why this instead of a rules wiki

Rules wikis list variants. They don't tell you which ones fight each other. This does three things a static page can't:

1. **Dependency and conflict resolution.** Three-of-spades requires jokers and auto-enables them. Revolution and four-of-a-kind bombs claim the same trigger, so turning one on kicks the other off and says why. Blocked options are visibly dimmed rather than silently broken.
2. **Interaction analysis.** Below the sheet, the tool reads your combination and reports what it does to play — three-plus clearing mechanics means tricks never go around twice; runs plus the exchange means the President's advantage compounds; a steep exchange without *miyako-ochi* means one person holds office all night.
3. **A teaching-cost budget.** Every mechanic carries a 1–3 cost. The gauge converts the total into a rough minutes-to-teach figure and a tier, from *Kitchen table* to *Unhinged*.

## Design notes

- **Palette** is drawn from the game's own materials: table felt (`#14372c`), card stock ivory (`#f7f4ec`), pip red (`#9e1f26`), chip gold (`#bf9a55`). Red means *enabled*; gold means *office / hierarchy*. Nothing else gets a colour.
- **Tokens encode something true.** A mechanic printed on a specific card gets a real card face (2♦, 8♣, 3♠). A mechanic that lives on the table gets a dashed stamp. You can tell at a glance which rules are in the deck and which are social contract.
- **Signature interaction:** the rank ladder in the masthead physically inverts when you enable Revolution. It's the one place the interface does what the mechanic does.
- **The hierarchy rail** under the settings is a live read-out of the two controls that matter most — player count and the exchange — because the exchange is the game's actual engine and turning it off is a bigger decision than any single mechanic.

## Mechanics included

**Cards with powers** — twos wipe the pile · eight-cut (八切り) · jokers · three of spades counter (スペ3) · seven gift (7渡し) · nine reverse (9リバース) · five skip (5飛び)

**What four of a kind does** — bombs clear · bombs can be built · revolution (革命)

**How a trick is played** — suits break ties · suit lock (縛り) · runs (階段) · match-and-skip · three of clubs leads · can't finish dirty

**Titles** — fall from grace (都落ち) · thrones and seating · scoring

**Table** — the Scum serves · President's decree

## Stack

None. One `index.html`, no build step, no dependencies, no framework. State lives in memory and serialises to the URL hash, so **Copy link** shares an exact ruleset.

## Local

```bash
open index.html          # that's it
# or, if you want a server:
python3 -m http.server 8000
```

## Deploy

Hosted on Vercel with the GitHub repo connected, so a push to `main` deploys to production and any other branch gets a preview URL.

To deploy by hand:

```bash
npx vercel            # preview
npm run deploy        # production (npx vercel --prod)
```

Project settings: framework preset **Other**, no build command, output directory `.`.

## License

MIT

# Hexfall: Lanes & Legions

A turn-based hex strategy game for the browser that mixes base building and a two-resource economy (Warcraft 2), terrain-based tactical combat with day/night and zones of control (Wesnoth), districts with adjacency bonuses and a small tech tree (Civ 6), and champions, lanes, minion waves, towers and jungle camps (League of Legends).

The whole game is a single file, `index.html`, with no build step and no dependencies.

## Play locally

Open `index.html` in any modern browser.

## Deploy on Cloudflare Pages

1. Push `index.html` and this README to the root of `github.com/Dirzo/strategy` (on GitHub: **Add file → Upload files**, then commit).
2. In the Cloudflare dashboard, go to **Workers & Pages → Create → Pages → Connect to Git**, and pick the `Dirzo/strategy` repository.
3. Use these build settings:
   - Framework preset: **None**
   - Build command: *(leave empty)*
   - Build output directory: `/`
4. Click **Save and Deploy**. The game will be live at `https://<project-name>.pages.dev`.

Every push to the main branch redeploys automatically.

## How the game works

- **Goal:** destroy the Horde's Keep. Each Keep is shielded until one of its three lane towers falls.
- **Economy:** the Keep earns 8 gold per turn. Workers on gold mines add 8 gold; workers in forests add 4 lumber.
- **Buildings:** Barracks (unlocks soldiers), Lumber mill (+2 lumber per adjacent forest), Market (+2 gold per adjacent building), Guard tower.
- **Research:** six technologies, one at a time, each taking a few turns.
- **Combat:** each strike hits with 100% minus the defender's terrain defense. Defenders strike back with the same weapon type. Units earn experience and get promoted.
- **Day/night:** Kingdom units deal +25% by day and −25% by night; the Horde is the reverse.
- **Lanes:** every three rounds, minion waves march down three roads. Champions earn bonus gold for last hits.
- **Champions:** four abilities each (Q/W/E/R), with the ultimate unlocking at level 3. Buy gear while standing next to your Keep.
- **Saving:** progress is saved in the browser after every turn.

## Controls

Enter ends the turn. Esc cancels. Tab or Space cycles through ready units. C selects your champion, K your Keep, H opens help. Drag to pan; scroll or pinch to zoom.

## Code layout (inside index.html)

- The first `<script>` holds the game core: map generation, units, combat, economy, turn flow and the AI.
- The second `<script>` holds the interface: canvas rendering, input, panels and dialogs.

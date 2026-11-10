# Lithium Sounds

Free sound packs for [Lithium Studio](https://github.com/thecalamityjoe87/ikaros-studio): sampled pianos, drums, bass, guitar and strings, downloaded from inside the app.

You don't need to download anything from here by hand. In Lithium Studio, open **Sounds > Manage Sounds** (or say yes to the starter sounds the first time the app starts), pick the packs you want, and the app downloads and installs them for you. The Linux installer can also fetch the starter sounds while it installs.

## The packs

| Pack | Category | Download | What it is | From | License |
|---|---|---|---|---|---|
| Piano | Keyboards | 31 MB | A Kawai upright piano in a living room, with two velocity layers. | [Upright Piano KW](https://freepats.zenvoid.org/Piano/acoustic-grand-piano.html), FreePats (Gonzalo and Roberto) | CC0-1.0 |
| Grand Piano | Keyboards | 145 MB | A Yamaha C5 grand piano with 16 velocity layers, hammer noise and string resonance. | [Salamander Grand Piano](https://freepats.zenvoid.org/Piano/acoustic-grand-piano.html), Alexander Holm | CC-BY-3.0 |
| Electric Pianos | Keyboards | 18 MB | Three classic electric pianos: a Yamaha CP80, a Hohner Pianet T and a Wurlitzer EP200. | [E-Pianos](https://github.com/sfzinstruments/GregSullivan.E-Pianos), Greg Sullivan | CC-BY-3.0 |
| Drums | Drums | 163 MB | A big, rough acoustic drum kit played with sticks: kick, snare, hi-hat, three toms, ride and crash. | [Big Rusty Drums](https://shop.karoryfer.com/pages/free-big-rusty-drums), Karoryfer Samples | CC0-1.0 |
| Red Zeppelin Kit | Drums | 9 MB | A vintage Ludwig rock kit with Zildjian and Sabian cymbals. Drummer tracks play it. | [AVL Drumkits](https://www.bandshed.net/avldrumkits/), Glen MacArthur (AV Linux) | CC-BY-SA-3.0 |
| Bass | Bass | 30 MB | A Squier Jazz Bass, with four velocity layers and four takes of every note. | [Growlybass](https://github.com/sfzinstruments/karoryfer.growlybass), Karoryfer Samples | CC0-1.0 |
| Guitar | Guitar | 57 MB | An archtop guitar, recorded both through its pickup and with a microphone. | [Shinyguitar](https://github.com/sfzinstruments/karoryfer.shinyguitar), Karoryfer Samples (played and mapped by D. Smolken) | CC0-1.0 |
| Strings | Strings | 95 MB | Violin, viola, cello and double bass sections, a solo violin and pizzicato strings, from a chamber orchestra. | [VSCO 2 Community Edition](https://github.com/sgossner/VSCO-2-CE), Versilian Studios (Sam Gossner) | CC0-1.0 |

**Starter Sounds** is the set a new user is offered: Piano, Drums, Bass, Guitar and Strings (about 377 MB).

## Credits and licenses

The samples are the work of the people above; Lithium Studio only packages them (maps them to its instruments and trims and converts the files). Each pack keeps its own license, and every zip holds the full license text (`LICENSE.txt`) and its credits (`pack.json`).

- **CC0-1.0** packs are in the public domain: use them for anything, no credit needed (though it's always appreciated).
- **CC-BY-3.0** packs (Grand Piano, Electric Pianos) may be used for anything, including commercial music, as long as you credit the authors when you share the samples or work made from them (a line in your release notes or credits does it).
- **CC-BY-SA-3.0** (Red Zeppelin Kit): the same credit, and a shared or modified copy of the samples themselves must keep the same license.

## How the app finds the packs

Each [release](https://github.com/thecalamityjoe87/lithium-sounds/releases) holds every pack's zip and an `index.json` listing them: name, category, description, size, SHA-256 and license of each pack, and the Starter Sounds set. Lithium Studio reads the index of the latest release:

    https://github.com/thecalamityjoe87/lithium-sounds/releases/latest/download/index.json

The zips' addresses in the index are relative to it, so they always come from the same release. The app checks every download against its SHA-256 before installing it.

## Adding or updating a pack

Packs are built by `tools/packs/build_packs.py` in the Lithium Studio repository, which downloads the original libraries, converts them, and writes the zips and `index.json`. To publish:

1. Build the packs (bump a pack's version when it changes).
2. Make a new release here (`v2`, `v3`...) and upload **every** zip plus the new `index.json`: the app only looks at the latest release.

A pack's `id` (such as `ikaros-studio.drums`) must never change: sessions refer to their sounds by it.

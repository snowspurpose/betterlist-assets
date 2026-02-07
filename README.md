# Betterlist Assets [WIP]

Asset repository for [Betterlists](https://betterlists.pages.dev/) - a tier list maker for gacha games.

## What's This?

This repo powers [Betterlists](https://betterlists.pages.dev/) with character portraits and element icons for:
- **Genshin Impact** - 100+ characters, 7 elements
- **Honkai: Star Rail** - 70+ characters, 7 types
- **Wuthering Waves** - 60+ resonators, 6 elements
- **Zenless Zone Zero** - 55+ agents, 6 attributes

**Note:** While this is primarily built for Betterlists, you're welcome to use these assets via CDN for your own projects.

## Repository Structure

```
betterlist-assets/
├── genshin/characters/          # Character portraits
├── genshin/element/             # Element icons
├── genshin/manifest.json        # Character data
├── hsr/...                      # Same structure for HSR
├── wuwa/...                     # Same structure for Wuwa
├── zzz/...                      # Same structure for ZZZ
└── main_template.json           # Game list config
```

## Using the Assets

### Base URL

```
https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/
```

### Examples

**Character portraits:**
```
https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/genshin/characters/zhongli.png
https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/zzz/characters/miyabi.png
```

**Element icons:**
```
https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/genshin/element/pyro.png
https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/zzz/element/ice.png
```

### Quick Integration

```javascript
const BASE = 'https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main';

// Character image
const char = `${BASE}/genshin/characters/hu-tao.png`;

// Element icon
const element = `${BASE}/genshin/element/pyro.png`;
```

## Manifest Files

### Game List

`main_template.json` lists all supported games with their paths:

```javascript
const games = await fetch(
  'https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/main_template.json'
).then(r => r.json());

// Result:
// [
//   { id: "genshin", name: "Genshin Impact", thumbnail: "genshin/coverico.png", ... },
//   { id: "hsr", name: "Honkai Star Rail", ... },
//   ...
// ]
```

### Character Data

Each `{game}/manifest.json` contains character info and tier templates:

```javascript
const { tiers, items } = await fetch(
  'https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/genshin/manifest.json'
).then(r => r.json());

// tiers: [{ id: "t0", name: "T0 (OP)", color: "#ff7f7f" }, ...]
// items: [{ id: "zhongli", file: "characters/zhongli.png", element: "Geo", weapon: "Polearm" }, ...]
```

**Character Properties:**
- **Genshin/Wuwa:** `id`, `file`, `element`, `weapon`
- **ZZZ:** `id`, `file`, `element`, `type` (attack/defense/support/anomaly/stun)

## Naming Convention

All files use kebab-case:
- `hu-tao.png` - Standard characters
- `kamisato-ayaka.png` - Full names
- `traveler-dendro.png` - Element variants
- `rover-havoc-2.png` - Alt versions (numbered)

**Special characters:**
- Traveler/Rover: Element-specific versions (e.g., `traveler-pyro.png`, `rover-aero.png`)
- Mannequins: Placeholder images (`manekin.png`, `manekina-2.png`, etc.)

## Contributing

### Adding New Characters

New character released? Here's how to add them:

#### 1. Prepare the Image

- [x] PNG format with transparent background
- [x] Square aspect ratio preferred
- [x] Clear, centered composition
- [x] Optimized file size (aim for <100KB)

#### 2. Name the File

Use kebab-case: `character-name.png`

Check existing files for reference:
- `lan-yan.png`
- `the-herta.png`
- `kamisato-ayaka.png`

#### 3. Add to the Correct Folder

```
genshin/characters/new-character.png
hsr/characters/new-character.png
wuwa/characters/new-character.png
zzz/characters/new-character.png
```

#### 4. Update the Manifest

Edit `{game}/manifest.json` and add to the `items` array:

**For Genshin/Wuwa:**
```json
{
  "id": "new-character",
  "file": "characters/new-character.png",
  "element": "Pyro",
  "weapon": "Sword"
}
```

**For ZZZ:**
```json
{
  "id": "new-character",
  "file": "characters/new-character.png",
  "element": "fire",
  "type": "attack"
}
```

#### 5. Submit a Pull Request

- **Title:** `Add [Character Name] ([Game])`
- **Description:** Character details and source

### Adding New Games

Want to add a new game? You'll need:
- Character portraits folder
- Element/type icons folder
- Game cover icon (`coverico.png`)
- Manifest file following the existing structure
- Entry in `main_template.json`

Open an issue first to discuss!

### Quality Guidelines

#### Images

**Required:**
- [x] PNG with transparency
- [x] High resolution (but optimized <100KB)
- [x] Centered character
- [x] Clean background removal

**Not Allowed:**
- [ ] Watermarks
- [ ] Low-quality upscales
- [ ] Artifacts or compression issues

#### Manifests

**Required:**
- [x] Valid JSON (use a validator)
- [x] Consistent property names
- [x] Correct element/weapon/type values

**Recommended:**
- [x] Alphabetical order (helps but not required)

### Where to Find Assets

Good sources for character images:
- [hakush.in](https://hakush.in/) - Our current data source
- Official game wikis
- Game press kits and official art
- High-quality fan renders (with permission)

**Important:** Make sure you have the right to use any images you submit.

## Credits

- Character data sourced from [hakush.in](https://hakush.in/)
- Built for [Betterlists](https://betterlists.pages.dev/)
- Community contributors

## Questions?

- **Bug or missing character?** Open an issue
- **Want to contribute?** See above and submit a PR
- **Using this for your project?** That's cool! A link back is appreciated but not required

---

**Disclaimer:** Unofficial fan project. All game assets © their respective owners (HoYoverse, Kuro Games). Not affiliated with or endorsed by any game publisher.

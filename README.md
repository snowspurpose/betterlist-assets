# Betterlist Assets

A comprehensive asset repository for popular gacha games, providing character portraits and element icons for tier list generation and character management applications.

## 📋 Overview

This repository contains high-quality character portraits and element/type icons for four major gacha games:

- **Genshin Impact** - 150+ characters across 7 elements
- **Honkai: Star Rail** - 70+ characters across 7 combat types
- **Wuthering Waves** - 60+ characters across 6 element types
- **Zenless Zone Zero** - 55+ characters across 6 attribute types

## 🎮 Supported Games

### Genshin Impact (`/genshin`)
150+ characters across 7 elements (Anemo, Cryo, Dendro, Electro, Geo, Hydro, Pyro)

### Honkai: Star Rail (`/hsr`)
70+ characters across 7 combat types (Fire, Ice, Imaginary, Lightning, Physical, Quantum, Wind)

### Wuthering Waves (`/wuwa`)
60+ resonators across 6 elements (Aero, Electro, Fusion, Glacio, Havoc, Spectro)

### Zenless Zone Zero (`/zzz`)
55+ agents across 6 attributes (Electric, Ether, Fire, Ice, Physical, Honed Edge)

## 📁 Repository Structure

```
betterlist-assets/
├── genshin/
│   ├── characters/          # 150+ character portraits
│   ├── element/             # 7 element icons
│   ├── coverico.png         # Game cover icon
│   └── manifest.json        # Character and element metadata
├── hsr/
│   ├── characters/          # 70+ character portraits
│   ├── element/             # 7 combat type icons
│   ├── coverico.png         # Game cover icon
│   └── manifest.json        # Character and element metadata
├── wuwa/
│   ├── characters/          # 60+ character portraits
│   ├── element/             # 6 element icons
│   ├── coverico.png         # Game cover icon
│   └── manifest.json        # Character and element metadata
├── zzz/
│   ├── characters/          # 55+ character portraits
│   ├── element/             # 6 attribute icons
│   ├── coverico.png         # Game cover icon
│   └── manifest.json        # Character and element metadata
├── main_template.json       # Main configuration template
└── README.md
```

## 🔧 Asset Naming Convention

All character assets follow a consistent kebab-case naming pattern:

```
character-name.png
```

### Examples:
- `arataki-itto.png` - Multi-word names use hyphens
- `kamisato-ayaka.png` - Full character names
- `hu-tao.png` - Names with spaces
- `traveler-anemo.png` - Variant characters include suffix
- `trailblazer-fire.png` - HSR protagonist variants
- `rover-havoc.png` - Wuthering Waves protagonist variants

### Special Cases:
- **Travelers/Rovers**: Element-specific variants (e.g., `traveler-dendro.png`, `rover-spectro.png`)
- **Alternative versions**: Numbered suffixes (e.g., `traveler-anemo-2.png`)
- **Mannequins**: Placeholder characters (`manekin.png`, `manekina.png` with numbered variants)

## 📦 Usage

### Direct File Access

All assets can be accessed directly via GitHub's raw content URL:

```
https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/{game}/{type}/{filename}
```

#### Examples:

**Character Portraits:**
```
https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/genshin/characters/zhongli.png
https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/hsr/characters/acheron.png
https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/wuwa/characters/jiyan.png
https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/zzz/characters/miyabi.png
```

**Element Icons:**
```
https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/genshin/element/pyro.png
https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/hsr/element/fire.png
https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/wuwa/element/havoc.png
https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/zzz/element/ether.png
```

### Integration in Applications

#### JavaScript/TypeScript Example

```javascript
const ASSETS_BASE_URL = 'https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main';

// Get character portrait
function getCharacterPortrait(game, characterName) {
  return `${ASSETS_BASE_URL}/${game}/characters/${characterName}.png`;
}

// Get element icon
function getElementIcon(game, elementName) {
  return `${ASSETS_BASE_URL}/${game}/element/${elementName}.png`;
}

// Usage
const zhongliPortrait = getCharacterPortrait('genshin', 'zhongli');
const pyroIcon = getElementIcon('genshin', 'pyro');
```

#### React Component Example

```jsx
import React from 'react';

const CharacterCard = ({ game, character, element }) => {
  const baseUrl = 'https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main';
  
  return (
    <div className="character-card">
      <img 
        src={`${baseUrl}/${game}/characters/${character}.png`}
        alt={character}
        className="character-portrait"
      />
      <img 
        src={`${baseUrl}/${game}/element/${element}.png`}
        alt={element}
        className="element-icon"
      />
    </div>
  );
};
```

## 📊 Manifest Files

The repository includes two types of manifest files for programmatic access to asset metadata.

### Main Template (`main_template.json`)

Contains the game list configuration with paths to assets:

```json
[
  {
    "id": "genshin",
    "name": "Genshin Impact",
    "thumbnail": "genshin/coverico.png",
    "folderPath": "genshin",
    "elementfolderPath": "genshin/element/"
  },
  {
    "id": "hsr",
    "name": "Honkai Star Rail",
    "thumbnail": "hsr/coverico.png",
    "folderPath": "hsr",
    "elementfolderPath": "hsr/element/"
  }
  // ... more games
]
```

**Properties:**
- `id` - Unique game identifier
- `name` - Display name
- `thumbnail` - Path to game cover icon
- `folderPath` - Base path for game assets
- `elementfolderPath` - Path to element/type icons

### Game-Specific Manifests (`{game}/manifest.json`)

Each game folder contains a detailed manifest with character and tier data.

#### Structure

All manifests include:
- `tiers` - Array of tier definitions for tier lists
- `items` - Array of character objects

#### Tier Structure

```json
"tiers": [
  {
    "id": "t0",
    "name": "T0 (OP)",
    "color": "#ff7f7f"
  },
  {
    "id": "t1",
    "name": "T0.5",
    "color": "#ffbf7f"
  }
  // ... more tiers
]
```

#### Character Structure by Game

**Genshin Impact & Wuthering Waves:**
```json
{
  "id": "zhongli",
  "file": "characters/zhongli.png",
  "element": "Geo",
  "weapon": "Polearm"
}
```

**Zenless Zone Zero:**
```json
{
  "id": "miyabi",
  "file": "characters/miyabi.png",
  "element": "ice",
  "type": "anomaly"
}
```

**ZZZ Types:** `attack`, `defense`, `support`, `anomaly`, `stun`

### Using Manifests

#### Fetch Game List

```javascript
const response = await fetch(
  'https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/main_template.json'
);
const games = await response.json();
```

#### Fetch Game Characters

```javascript
const response = await fetch(
  'https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/genshin/manifest.json'
);
const { tiers, items } = await response.json();

// Filter characters by element
const pyroCharacters = items.filter(char => char.element === 'Pyro');
```

#### Dynamic Character Loading

```javascript
async function loadGameData(gameId) {
  const manifest = await fetch(
    `https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/${gameId}/manifest.json`
  ).then(r => r.json());
  
  return {
    characters: manifest.items.map(item => ({
      ...item,
      imageUrl: `https://raw.githubusercontent.com/snowspurpose/betterlist-assets/main/${gameId}/${item.file}`
    })),
    tiers: manifest.tiers
  };
}
```

## 🎨 Asset Specifications

- **Format**: PNG with transparency
- **Character Portraits**: Consistent aspect ratio and sizing
- **Element Icons**: Square format, optimized for use as badges/tags
- **Cover Icons**: Game-specific branding/logo representations

## 🔄 Updates and Maintenance

This repository is regularly updated to include:
- New character releases
- Character variant additions
- Asset quality improvements
- New game support

## 🤝 Contributing

To contribute new assets or report issues:

1. Ensure assets follow the naming convention
2. Verify image quality and format (PNG)
3. Submit a pull request with clear descriptions
4. Update the relevant `manifest.json` file

### Asset Guidelines

- **Character portraits**: High-quality, transparent background, centered composition
- **Element icons**: Clean, recognizable symbols at various sizes
- **Naming**: Use kebab-case, avoid special characters except hyphens
- **File size**: Optimize images without significant quality loss

## 📝 License

Please refer to the repository license for usage terms and conditions.

## 🎯 Use Cases

This asset repository is perfect for:

- **Tier List Generators**: Create visual tier lists for characters
- **Team Builders**: Design team composition tools
- **Character Databases**: Build searchable character catalogs
- **Discord Bots**: Integrate character data and visuals
- **Mobile Apps**: Use in companion apps and guides
- **Wiki Sites**: Enhance game wikis and databases
- **Content Creation**: Thumbnails, guides, and video content

## 🙏 Credits

Character data sourced from [hakush.in](https://hakush.in/) - thank you for providing comprehensive game databases!

## 🔗 Related Projects

If you're using these assets, consider linking back to this repository to help others discover it!

## 📮 Contact & Support

For questions, suggestions, or issues, please use the GitHub Issues tab.

---

**Note**: This is an unofficial fan-made asset repository. All character designs and game elements are property of their respective owners:
- Genshin Impact © HoYoverse
- Honkai: Star Rail © HoYoverse  
- Wuthering Waves © Kuro Games
- Zenless Zone Zero © HoYoverse

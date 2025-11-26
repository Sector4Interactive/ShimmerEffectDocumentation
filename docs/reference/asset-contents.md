# Asset Contents

Complete reference of all files and folders included in the Shimmer Effect Highlight asset package.

## Package Structure

```
Assets/Sector4/Shimmer Effect/
├── Materials/
│   └── Shimmer_Effect_Highlight.mat
├── Scenes/
│   ├── Demo Scene
│   └── Global Volume Profile
└── Shader/
    └── Shimmer_Effect_Highlight.shadergraph
```

---

## Materials Folder

### Shimmer_Effect_Highlight.mat

**Type:** Material Asset  
**Purpose:** Pre-configured material with default shimmer settings

**Default Configuration:**
- Base Color: White
- Highlight Color: Gold/Yellow
- Speed: 2.0
- WaveScale: 1.0
- Wave Tiling: Diagonal 1
- Emission: 0.1
- Alpha: 1.0
- Normal Map: On (no texture assigned)
- Smoothness Map: On (no texture assigned)
- Metallic Map: Off

**Usage:**
- Drag and drop directly onto objects for instant shimmer effect
- Use as a template for creating custom material variants
- Reference for default property values

**Best Practices:**
- Duplicate this material before customizing for specific use cases
- Keep the original as a reference template
- Name duplicates descriptively (e.g., "Gold_Coin_Shimmer", "Quest_Item_Shimmer")

---

## Scenes Folder

### Demo Scene

**Type:** Unity Scene  
**Purpose:** Complete example scene showcasing various configurations and use cases

**Contents:**
- Multiple example objects with different shimmer configurations
- Varied wave tiling patterns demonstrated
- Different color and emission settings
- Performance reference setup
- Example lighting setup
- Camera configuration

**What You'll Learn:**
- How to apply the shimmer effect to different object types
- Visual comparison of all wave tiling options
- Effect of different property values
- Proper scene setup for optimal results
- Best practices in action

**Usage Tips:**
- Open and explore in Play Mode to see animations
- Select objects to inspect their material settings in the Inspector
- Use as reference when configuring your own materials
- Copy configurations you like to your own scenes

**Scene Requirements:**
- Universal Render Pipeline (URP)
- Post-processing enabled (recommended)
- Shader Graph package

### Global Volume Profile

**Type:** Volume Profile Asset  
**Purpose:** Post-processing settings optimized for the shimmer effect

**Included Overrides:**
- **Bloom**: Configured for optimal shimmer glow
  - Intensity: Balanced for shimmer emission
  - Threshold: Set to complement emission values
  - Scatter: Tuned for pleasant glow spread
- **Color Adjustments** (optional): Recommended settings for vibrant visuals
- **Tonemapping**: HDR configuration for emission

**Usage:**
1. Add a Global Volume to your scene (GameObject > Volume > Global Volume)
2. Assign this profile to the Volume's Profile slot
3. Adjust intensity values to match your game's aesthetic

**Customization:**
- Start with these settings as a baseline
- Adjust bloom intensity based on your overall scene brightness
- Modify threshold if you have other emissive objects
- Test with your game's lighting conditions

**Without Post-Processing:**
The shimmer effect works without post-processing, but emission effects will be less pronounced. Bloom significantly enhances the glow.

---

## Shader Folder

### Shimmer_Effect_Highlight.shadergraph

**Type:** Shader Graph Asset  
**Purpose:** The core shader that powers the shimmer effect

**Technical Details:**
- **Pipeline:** Universal Render Pipeline (URP)
- **Workflow:** Shader Graph visual programming
- **Surface Type:** Opaque (with alpha support)
- **Lighting:** PBR-based with custom shimmer overlay
- **Render Face:** Front (configurable)

**Properties Exposed:**
- Base color and texture properties
- Normal, Smoothness, and Metallic map controls
- Custom shimmer effect parameters
- Wave tiling enum for animation patterns
- Emission control for HDR glow

**Customization:**
You can open and modify this shader graph if you need advanced customization:

1. Double-click `Shimmer_Effect_Highlight.shadergraph` in the Project window
2. The Shader Graph editor will open
3. Modify nodes and connections to customize behavior
4. Save to see changes in materials using this shader

**Advanced Use Cases:**
- Add custom properties
- Modify wave algorithms
- Create variant effects
- Integrate with custom render features
- Add additional texture support

**Caution:**
- Back up the original shader before making changes
- Test changes thoroughly
- Shader modifications affect all materials using this shader
- Requires Shader Graph knowledge for complex changes

**Shader Graph Requirements:**
- Shader Graph package (installed via Package Manager)
- Universal Render Pipeline
- Unity 2021.3 or higher (recommended)

---

## File Specifications

### Material File (.mat)

**Format:** Unity Material Asset  
**Dependencies:** 
- Shimmer_Effect_Highlight.shadergraph
- Universal Render Pipeline

**Size:** ~10 KB  
**Editable:** Yes, via Inspector

### Scene File

**Format:** Unity Scene  
**Dependencies:**
- All shader and material files
- URP pipeline
- Post-processing package

**Size:** ~500 KB - 2 MB (depending on included assets)  
**Editable:** Yes, in Unity Editor

### Shader Graph File (.shadergraph)

**Format:** Shader Graph Asset (JSON-based)  
**Dependencies:**
- Shader Graph package
- Universal Render Pipeline

**Size:** ~50-100 KB  
**Editable:** Yes, in Shader Graph editor

---

## Version Compatibility

### Unity Versions

**Minimum:** Unity 2021.3 LTS  
**Recommended:** Unity 2022.3 LTS or newer  
**Tested On:**
- Unity 2021.3 LTS
- Unity 2022.3 LTS
- Unity 2023.2

### Render Pipeline

**Required:** Universal Render Pipeline (URP)  
**URP Version:** 12.0 or higher  
**Not Compatible With:**
- Built-in Render Pipeline
- High Definition Render Pipeline (HDRP) - would require conversion

### Dependencies

**Required Packages:**
- Universal RP (com.unity.render-pipelines.universal)
- Shader Graph (com.unity.shadergraph)

**Optional but Recommended:**
- Post Processing (included in URP)

---

## File Locations

### After Import

All files are imported to:
```
Assets/Sector4/Shimmer Effect/
```

### Organization Tips

**For Your Project:**
```
Assets/
├── Sector4/
│   └── Shimmer Effect/          # Original asset (keep untouched)
└── YourGame/
    ├── Materials/
    │   ├── Shimmer/
    │   │   ├── Coins_Shimmer.mat
    │   │   ├── Quest_Items_Shimmer.mat
    │   │   └── PowerUps_Shimmer.mat
    └── Prefabs/
        └── ShimmerItems/
            ├── Gold_Coin.prefab
            └── Health_Potion.prefab
```

**Benefits:**
- Keep original asset separate and unmodified
- Organize your custom materials by category
- Easy to update asset if new version is released
- Clear separation between package and project assets

---

## Asset Information

**Package Name:** Shimmer Effect Highlight  
**Publisher:** Sector4  
**Version:** 1.0  
**Category:** Shaders & Effects  
**License:** Standard Unity Asset Store EULA

**Support:**
- Documentation: This website
- Email: [Check Asset Store page]
- Unity Forum Thread: [Check Asset Store page]

---

## Next Steps

- Learn how to [Install](../getting-started/installation.md) the asset
- Follow the [Quick Start](../getting-started/quick-start.md) guide
- Explore the [Demo Scene](#demo-scene) for examples
- Read the [FAQ](faq.md) for common questions

---

## Update History

### Version 1.0 (Initial Release)
- Core shimmer shader with 6 wave patterns
- PBR material property support
- Demo scene with examples
- Optimized Volume Profile
- Complete documentation

**Future Updates:**
Check the Asset Store page for update announcements and new features.

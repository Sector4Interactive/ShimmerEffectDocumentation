# Shimmer Effect Highlight -Documentation


#### Materials Folder
- **Shimmer_Effect_Highlight.mat**: Pre-configured material with default shimmer settings. Use this as a template or apply directly to your objects.

#### Scenes Folder
- **Demo Scene**: Complete example scene showing various configurations and use cases
- **Global Volume Profile**: Post-processing settings optimized for the shimmer effect

#### Shader Folder
- **Shimmer_Effect_Highlight.shadergraph**: The core shader graph file. Open in Shader Graph editor for advanced customization.

---

## Installation & Setup

### Step 1: Import the Asset
1. Import the asset package into your Unity project
2. The asset will be placed in `Assets/Sector4/Shimmer Effect/`

#### Normal Map On/Off
- **Type**: Dropdown (Enum)
- **Options**: On / Off
- **Default**: On
- **Description**: Toggle to enable or disable the Normal Map functionality
- **Usage**: 
  - **On**: Normal Map slot is active and will affect surface lighting


#### Smoothness Map On/Off
- **Type**: Dropdown (Enum)
- **Options**: On / Off
- **Default**: On
- **Description**: Toggle to enable or disable the Smoothness Map functionality
- **Usage**: 
  - **On**: Smoothness Map slot is active and controls surface glossiness
  - **Off**: Smoothness Map is disabled, uses default smoothness value

#### Metallic Map On/Off
- **Type**: Dropdown (Enum)
- **Options**: On / Off
- **Default**: Off
- **Description**: Toggle to enable or disable the Metallic Map functionality
- **Usage**: 
  - **On**: Metallic Map slot is active and defines metallic properties
  - **Off**: Metallic Map is disabled, treats material as non-metallic or uniform


### Shimmer Effect Controls

#### Base Color
- **Type**: Color (RGBA)
- **Default**: White (1, 1, 1, 1)
- **Description**: The underlying color of your material
- **Range**: Full RGB spectrum + Alpha
- **Usage**: Set to your desired base material color
- **Tips**: 
  - Keep at white if using a Base Map texture
  - Use alpha channel to control overall material transparency

#### Highlight Color
- **Type**: Color (RGB)
- **Default**: Yellow/Gold
- **Description**: The color of the shimmer/highlight effect as it passes over the surface
- **Range**: Full RGB spectrum
- **Usage**: Choose bright, vibrant colors for best visibility
- **Tips**: 
  - Yellow/Gold: Premium, valuable items
  - Cyan/Blue: Magical, tech, or cold effects
  - White: Intense, pure energy
  - Green: Nature, healing, or poison effects

#### Speed
- **Type**: Float
- **Default**: 2.0
- **Range**: 0.0 to 10.0 (recommended)
- **Description**: Controls how fast the shimmer wave animates across the surface
- **Usage**: 
  - Low values (0.5-1.5): Slow, elegant shimmer
  - Medium values (1.5-3.0): Standard animation speed
  - High values (3.0+): Fast, energetic effect
- **Tips**: Sync with game events (e.g., speed up when player is nearby)

#### Alpha
- **Type**: Float
- **Default**: 1.0
- **Range**: 0.0 to 1.0
- **Description**: Controls the overall opacity of the material
- **Usage**:
  - 1.0: Fully opaque
  - 0.5: Semi-transparent
  - 0.0: Fully transparent
- **Tips**: Use for fading effects or ghost-like appearances

#### WaveScale
- **Type**: Float
- **Default**: 1.0
- **Range**: 0.1 to 10.0
- **Description**: Adjusts the scale/size of the shimmer wave pattern
- **Usage**:
  - Small values (0.5-1.0): Tight, frequent shimmer bands
  - Large values (2.0-5.0): Wide, spread-out shimmer bands
- **Tips**: Adjust based on object size; larger objects may need larger wave scales

#### Wave Tiling
- **Type**: Dropdown (Enum)
- **Default**: Diagonal 1
- **Description**: Determines the direction and pattern of the shimmer wave movement
- **Options**: See [Wave Tiling Options](#wave-tiling-options) section below

#### Emission
- **Type**: Float
- **Default**: 0.1
- **Range**: 0.0 to 2.0
- **Description**: Controls the emission intensity of the shimmer highlight
- **Usage**:
  - 0.0: No emission (shimmer is just colored)
  - 0.1-0.5: Subtle glow effect
  - 0.5-1.0: Strong emission, HDR glow
  - 1.0+: Very intense, bloom-heavy effect
- **Tips**: 
  - Works best with Bloom post-processing enabled
  - Higher values create more pronounced glow
  - Can be animated for pulsing effects


## Wave Tiling Options

The **Wave Tiling** parameter offers six distinct animation patterns. Select the option that best fits your visual needs:

### 1. Diagonal 1 (Default)
- **Description**: Classic diagonal sweep across the surface
- **Best For**: General-purpose shimmer, UI elements, flat surfaces
- **Use Case**: Item highlights, button effects, general shimmer

### 2. Diagonal 2
- **Description**: Reverse diagonal sweep
- **Best For**: Alternate diagonal effect, creating variety
- **Use Case**: Paired with Diagonal 1 for alternating objects, opposite direction emphasis

### 3. Diagonal 3
- **Description**: Alternative diagonal pattern with unique sweep characteristics
- **Best For**: Creating visual variety, special highlighting needs
- **Use Case**: Differentiated objects, special states

### 4. Bottom To Top
- **Description**: Vertical scanning effect
- **Best For**: Tall objects, character bodies, vertical UI elements
- **Use Case**: 
  - Character power-up effects
  - Scanning/analyzing effects
  - Elevator UI elements
  - Vertical progress indicators

### 5. Back To Front
- **Description**: Wave travels from back to front in world space
- **Best For**: 3D objects with depth, creating depth perception
- **Use Case**:
  - 3D game objects
  - Objects viewed from a fixed camera angle
  - Emphasizing object volume

### 6. Pulse
- **Description**: Pulsing effect that emanates from center or cycles uniformly
- **Best For**: Attention-grabbing effects, beacon-like highlights
- **Visual**: ⊙ Radial/pulsing animation
- **Use Case**:
  - Quest markers
  - Important pickups
  - Alert states
  - Magical/energy objects
  - Breathing effects

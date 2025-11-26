# Material Properties

This page covers all the standard material properties available in the Shimmer Effect Highlight shader.

## Overview

The shader includes standard PBR (Physically Based Rendering) properties alongside the custom shimmer effect controls. This allows you to create realistic materials with stunning shimmer effects.

## Texture Maps Controls

<!-- ### Base Map

- **Type**: Texture2D (RGB)
- **Description**: The main color/albedo texture of your material
- **Usage**: 
  - Assign any texture to add surface detail
  - Leave empty to use solid Base Color
  - Supports standard Unity texture import settings
- **Tips**: 
  - Use high-quality textures for best results
  - Consider texture resolution vs. performance
  - UV mapping affects how the texture is displayed

!!! example "When to Use Base Map"
    - Objects with detailed surfaces (wood grain, metal scratches)
    - Character clothing or armor
    - Items with logos or patterns -->

<!-- ### Normal Map

Control surface bump details without adding geometry. -->

#### Normal Map On/Off

- **Type**: Dropdown (Enum)
- **Options**: On / Off
- **Default**: On
- **Description**: Toggle to enable or disable the Normal Map functionality

**Usage:**

- **On**: Normal Map slot is active and affects surface lighting
  
- **Off**: Normal Map slot is disabled


#### Smoothness Map On/Off

- **Type**: Dropdown (Enum)
- **Options**: On / Off
- **Default**: On
- **Description**: Toggle to enable or disable the Smoothness Map functionality

**Usage:**

- **On**: Smoothness Map slot is active and controls surface glossiness
  - Black areas = rough surface
  - White areas = smooth/glossy surface
  - Grayscale values = varying smoothness
  
- **Off**: Smoothness Map is disabled
  - Uses default smoothness value across entire surface



#### Metallic Map On/Off

- **Type**: Dropdown (Enum)
- **Options**: On / Off
- **Default**: Off
- **Description**: Toggle to enable or disable the Metallic Map functionality

**Usage:**

- **On**: Metallic Map slot is active and defines metallic properties
  - Black areas = non-metallic (dielectric)
  - White areas = fully metallic
  - Enables per-pixel metallic control
  
- **Off**: Metallic Map is disabled
  - Treats material as non-metallic or uniform
  - Simpler shader operations



<!-- ## Standard Material Properties

### Base Color

- **Type**: Color (RGBA)
- **Default**: White (1, 1, 1, 1)
- **Description**: The underlying color of your material
- **Range**: Full RGB spectrum + Alpha
- **Usage**: 
  - Set to your desired base material color
  - Multiplies with Base Map texture if present
  - Alpha channel controls overall material transparency -->



## Next Steps

<!-- - Learn about [Shimmer Controls](shimmer-controls.md) for effect customization -->
- Explore [Wave Tiling Options](wave-tiling.md) for animation patterns


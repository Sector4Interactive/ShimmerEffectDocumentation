# Quick Start

Get up and running with Shimmer Effect Highlight in just a few minutes!

## Your First Shimmer Effect

### Method 1: Using the Pre-configured Material

The fastest way to add a shimmer effect:

1. **Select Your Object**
   - In the Hierarchy, select the 3D object you want to apply the effect to

2. **Apply the Material**
   - In the Inspector, find the **Mesh Renderer** component
   - Expand the **Materials** section
   - Drag `Shimmer_Effect_Highlight.mat` from `Assets/Sector4/Shimmer Effect/Materials/` into the material slot

3. **Enter Play Mode**
   - Press the Play button to see your shimmer effect in action!

!!! success "That's It!"
    You now have a working shimmer effect on your object with default settings.

### Method 2: Creating a New Material

For more control, create your own material instance:

1. **Create Material**
   - Right-click in your Project window
   - Select **Create** → **Material**
   - Name it (e.g., "My_Shimmer_Material")

2. **Assign Shader**
   - Select your new material
   - In the Inspector, click the **Shader** dropdown
   - Search for and select **Shader Graphs/Shimmer_Effect_Highlight**

3. **Apply to Object**
   - Drag your new material onto the object in the scene

## Basic Customization

Now let's customize the shimmer effect:

### Change the Highlight Color

1. Select the material in the Project window
2. In the Inspector, find the **Highlight Color** property
3. Click the color picker and choose your desired color

!!! tip "Color Suggestions"
    - 🟡 **Yellow/Gold**: Premium items, treasure
    - 🔵 **Cyan/Blue**: Magical or tech effects
    - ⚪ **White**: Pure energy, divine items
    - 🟢 **Green**: Nature, healing, or poison

### Adjust Animation Speed

1. Find the **Speed** property
2. Adjust the value:
   - **0.5 - 1.5**: Slow, elegant shimmer
   - **1.5 - 3.0**: Standard speed (default is 2.0)
   - **3.0+**: Fast, energetic effect

### Change Wave Pattern

1. Locate the **Wave Tiling** dropdown
2. Select from available patterns:
   - **Diagonal 1**: Classic diagonal sweep (default)
   - **Bottom To Top**: Vertical scanning effect
   - **Pulse**: Radial pulsing effect
   - And more!

## Common Scenarios

### Highlighting a Collectible Item

```yaml
Base Color: Your item's base color
Highlight Color: Gold (#FFD700)
Speed: 1.5
Wave Tiling: Diagonal 1
Emission: 0.3
```

### Creating a Quest Marker

```yaml
Base Color: White
Highlight Color: Bright Yellow (#FFFF00)
Speed: 2.0
Wave Tiling: Pulse
Emission: 0.8
```

### Sci-Fi Scanning Effect

```yaml
Base Color: Dark Blue
Highlight Color: Cyan (#00FFFF)
Speed: 3.0
Wave Tiling: Bottom To Top
Emission: 0.5
```

## Testing in Play Mode

!!! warning "Runtime Only"
    The shimmer animation only plays in **Play Mode**. You won't see the animation in the Scene view while editing.

To test your effect:

1. Press the **Play** button in Unity
2. Observe the shimmer animation on your object
3. Exit Play Mode to adjust properties
4. Repeat until satisfied with the result

## Next Steps

Now that you have the basics down:
- 🌊 Understand [Wave Tiling Options](../user-guide/wave-tiling.md)




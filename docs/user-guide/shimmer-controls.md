# Shimmer Effect Controls

This page details all the properties that control the shimmer/highlight effect itself.

## Overview

The shimmer effect is controlled by several key properties that affect color, animation speed, wave patterns, and emission. Understanding these controls allows you to create the perfect effect for any situation.

---

## Core Properties

### Highlight Color

- **Type**: Color (RGB)
- **Default**: Yellow/Gold (#FFD700)
- **Description**: The color of the shimmer/highlight effect as it passes over the surface
- **Range**: Full RGB spectrum

**Usage:**

Choose colors that stand out against your base material and match your game's aesthetic.

**Recommended Colors by Purpose:**

| Purpose | Color | Hex Code | Use Case |
|---------|-------|----------|----------|
| Premium/Valuable | Gold | #FFD700 | Treasure, rare items |
| Magical | Cyan | #00FFFF | Magic items, spells |
| Tech/Sci-Fi | Bright Blue | #00BFFF | Technology, holograms |
| Energy | White | #FFFFFF | Pure energy, divine |
| Nature/Healing | Green | #00FF7F | Health items, nature |
| Poison/Corruption | Toxic Green | #39FF14 | Poison, corruption |
| Fire/Power | Orange-Red | #FF6600 | Fire, aggression |

**Tips:**

- Use bright, saturated colors for maximum visibility
- Contrast with base color for better effect
- Consider colorblind accessibility
- Match your game's established color language

!!! example "Color Psychology"
    - **Warm colors** (red, orange, yellow): Excitement, importance, danger
    - **Cool colors** (blue, cyan, purple): Calm, technology, magic
    - **White**: Purity, divinity, maximum attention
    - **Green**: Growth, healing, sometimes poison

---

### Speed

- **Type**: Float (Slider)
- **Default**: 2.0
- **Range**: 0.0 to 10.0 (recommended)
- **Description**: Controls how fast the shimmer wave animates across the surface

**Speed Guidelines:**

| Range | Effect | Best For |
|-------|--------|----------|
| 0.1 - 0.5 | Very Slow | Elegant effects, high-value items |
| 0.5 - 1.5 | Slow | Important but subtle highlights |
| 1.5 - 3.0 | Standard | General purpose, balanced visibility |
| 3.0 - 5.0 | Fast | Action items, urgent attention |
| 5.0+ | Very Fast | Extreme energy, overwhelming effects |

**Tips:**

- Slower speeds feel more premium and important
- Faster speeds grab attention but can be distracting
- Match speed to game pace (faster in action games)
- Can be animated dynamically via script
- Consider syncing with game events (speed up when player approaches)

**Example Script Integration:**

```csharp
// Speed up shimmer when player is nearby
float distance = Vector3.Distance(player.position, item.position);
float speed = Mathf.Lerp(5.0f, 1.0f, distance / 10.0f);
material.SetFloat("_Speed", speed);
```

---

### WaveScale

- **Type**: Float (Slider)
- **Default**: 1.0
- **Range**: 0.1 to 10.0
- **Description**: Adjusts the scale/size of the shimmer wave pattern

**Scale Effects:**

| Value Range | Visual Effect | Best For |
|-------------|---------------|----------|
| 0.1 - 0.5 | Very Tight Bands | Small objects, fine details |
| 0.5 - 1.0 | Tight Frequency | Standard small to medium objects |
| 1.0 - 2.0 | Medium Waves | Medium objects, default look |
| 2.0 - 5.0 | Wide Bands | Large objects, slower feeling |
| 5.0+ | Very Wide | Massive objects, subtle effect |

**Usage Tips:**

- **Small Objects** (UI buttons, coins): Use values 0.5 - 1.5
- **Medium Objects** (characters, props): Use values 1.0 - 3.0
- **Large Objects** (buildings, vehicles): Use values 3.0 - 7.0
- Scale inversely with object size for consistent visual density

**Object Size Matching:**

```csharp
// Auto-adjust wave scale based on object bounds
float objectSize = GetComponent<Renderer>().bounds.size.magnitude;
float waveScale = objectSize / 2.0f;
material.SetFloat("_WaveScale", waveScale);
```

!!! tip "Visual Balance"
    If you see too many shimmer bands on your object, increase WaveScale.
    If the effect looks too subtle or spread out, decrease WaveScale.

---

### Emission

- **Type**: Float (Slider)
- **Default**: 0.1
- **Range**: 0.0 to 2.0+ (HDR capable)
- **Description**: Controls the emission intensity of the shimmer highlight

**Emission Levels:**

| Value | Effect | Visual Result |
|-------|--------|---------------|
| 0.0 | No Emission | Color only, no glow |
| 0.1 - 0.3 | Subtle Glow | Gentle highlight, minimal bloom |
| 0.3 - 0.7 | Moderate | Clear glow, visible bloom |
| 0.7 - 1.0 | Strong | Pronounced glow, strong bloom |
| 1.0 - 2.0 | Very Intense | Extreme bloom, HDR effect |
| 2.0+ | Overwhelming | Maximum bloom, very bright |

**Usage Guidelines:**

- **Without Bloom**: Keep below 0.5 for reasonable results
- **With Bloom**: 0.3 - 1.0 range provides best balance
- **HDR Scenes**: Can push above 1.0 for extreme effects

**Bloom Requirements:**

!!! info "Post-Processing Setup"
    Emission effects are significantly enhanced with Bloom post-processing:
    
    1. Add a **Global Volume** to your scene
    2. Enable **Bloom** override
    3. Set Intensity to 0.3 - 0.5 for balanced effect
    4. Adjust Threshold to control which brightness levels bloom

**Tips:**

- Start low and increase gradually
- Higher values create more attention-grabbing effects
- Match emission to highlight importance
- Test with and without bloom to ensure it looks good in both cases
- Consider performance impact of bloom on target hardware

**Adaptive Emission Example:**

```csharp
// Pulse emission for alert state
float emission = 0.5f + Mathf.Sin(Time.time * 3.0f) * 0.3f;
material.SetFloat("_Emission", emission);
```

---

## Animation Control

### Wave Tiling

- **Type**: Dropdown (Enum)
- **Default**: Diagonal 1
- **Description**: Determines the direction and pattern of the shimmer wave movement
- **Options**: 6 different wave patterns

**Quick Reference:**

| Pattern | Direction | Best Use |
|---------|-----------|----------|
| Diagonal 1 | ↗️ | General purpose, UI elements |
| Diagonal 2 | ↖️ | Reverse diagonal, variety |
| Diagonal 3 | ⤢ | Alternative angle |
| Bottom To Top | ⬆️ | Vertical objects, scanning |
| Back To Front | → | 3D depth emphasis |
| Pulse | ⊙ | Attention-grabbing, radial |

For detailed information on each pattern, see the [Wave Tiling Options](wave-tiling.md) page.

---

## Property Combinations

### Preset Configurations

Here are some tested combinations for common scenarios:

#### Elegant Premium Item
```yaml
Highlight Color: Gold (#FFD700)
Speed: 1.2
WaveScale: 1.5
Wave Tiling: Diagonal 1
Emission: 0.3
```

#### Urgent Quest Marker
```yaml
Highlight Color: Bright Yellow (#FFFF00)
Speed: 3.0
WaveScale: 2.0
Wave Tiling: Pulse
Emission: 0.8
```

#### Magical Artifact
```yaml
Highlight Color: Cyan (#00FFFF)
Speed: 1.8
WaveScale: 1.0
Wave Tiling: Diagonal 3
Emission: 0.5
```

#### Sci-Fi Scanner
```yaml
Highlight Color: Electric Blue (#00BFFF)
Speed: 4.0
WaveScale: 0.8
Wave Tiling: Bottom To Top
Emission: 0.6
```

#### Subtle Power-Up
```yaml
Highlight Color: Soft Green (#00FF7F)
Speed: 2.5
WaveScale: 1.2
Wave Tiling: Pulse
Emission: 0.4
```

---

## Dynamic Control via Scripting

### Accessing Properties

All shimmer properties can be controlled via C# scripts:

```csharp
using UnityEngine;

public class ShimmerController : MonoBehaviour
{
    private Material shimmerMaterial;
    
    void Start()
    {
        // Get material from renderer
        shimmerMaterial = GetComponent<Renderer>().material;
    }
    
    public void SetHighlightColor(Color color)
    {
        shimmerMaterial.SetColor("_HighlightColor", color);
    }
    
    public void SetSpeed(float speed)
    {
        shimmerMaterial.SetFloat("_Speed", speed);
    }
    
    public void SetWaveScale(float scale)
    {
        shimmerMaterial.SetFloat("_WaveScale", scale);
    }
    
    public void SetEmission(float emission)
    {
        shimmerMaterial.SetFloat("_Emission", emission);
    }
}
```

### Animation Examples

**Pulsing Effect:**
```csharp
void Update()
{
    float pulse = Mathf.PingPong(Time.time, 1.0f);
    shimmerMaterial.SetFloat("_Emission", 0.3f + pulse * 0.4f);
}
```

**Distance-Based Intensity:**
```csharp
void Update()
{
    float distance = Vector3.Distance(player.position, transform.position);
    float normalizedDistance = Mathf.Clamp01(distance / 20.0f);
    float emission = Mathf.Lerp(1.0f, 0.2f, normalizedDistance);
    shimmerMaterial.SetFloat("_Emission", emission);
}
```

---

## Performance Considerations

- **Speed**: No performance impact, purely visual
- **WaveScale**: No performance impact
- **Emission**: Slight impact if using bloom post-processing
- **Multiple Objects**: Each object with the effect uses shader processing
- **Wave Tiling**: Different patterns have equivalent performance

!!! tip "Optimization"
    - Disable shimmer effect on objects far from camera
    - Use LOD (Level of Detail) system to swap to simpler materials at distance
    - Pool shimmer objects rather than instantiating/destroying frequently

---

## Next Steps

- Explore [Wave Tiling Options](wave-tiling.md) in detail
- Check out [Use Cases](../examples/use-cases.md) for practical applications
- See [Best Practices](../examples/best-practices.md) for optimization tips

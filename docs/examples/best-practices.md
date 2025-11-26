# Best Practices

Tips and recommendations for getting the most out of Shimmer Effect Highlight while maintaining optimal performance.

## Performance Optimization

### Object Count Management

**Recommended Limits:**
- **Mobile**: 10-20 shimmer objects simultaneously visible
- **Desktop**: 30-50 shimmer objects simultaneously visible
- **High-end**: 50+ shimmer objects with proper LOD

**Optimization Techniques:**

#### Distance-Based Culling
```csharp
using UnityEngine;

public class ShimmerDistanceCulling : MonoBehaviour
{
    public Material shimmerMaterial;
    public float maxDistance = 30f;
    private Transform playerTransform;
    private Renderer objectRenderer;
    private Material normalMaterial;
    
    void Start()
    {
        playerTransform = GameObject.FindGameObjectWithTag("Player").transform;
        objectRenderer = GetComponent<Renderer>();
        normalMaterial = objectRenderer.material;
    }
    
    void Update()
    {
        float distance = Vector3.Distance(playerTransform.position, transform.position);
        
        if (distance <= maxDistance)
        {
            if (objectRenderer.material != shimmerMaterial)
                objectRenderer.material = shimmerMaterial;
        }
        else
        {
            if (objectRenderer.material != normalMaterial)
                objectRenderer.material = normalMaterial;
        }
    }
}
```

#### Frustum Culling
Unity's built-in frustum culling automatically handles off-screen objects, but you can add additional logic:

```csharp
void Update()
{
    // Only update shimmer properties if object is visible
    if (objectRenderer.isVisible)
    {
        UpdateShimmerProperties();
    }
}
```

#### LOD System Integration
```csharp
using UnityEngine;

public class ShimmerLOD : MonoBehaviour
{
    public Material shimmerMaterial;
    public Material standardMaterial;
    public float lodDistance = 20f;
    
    private Transform player;
    private Renderer rend;
    
    void Start()
    {
        player = GameObject.FindGameObjectWithTag("Player").transform;
        rend = GetComponent<Renderer>();
    }
    
    void Update()
    {
        float distance = Vector3.Distance(player.position, transform.position);
        
        // Use shimmer when close, standard material when far
        rend.material = (distance < lodDistance) ? shimmerMaterial : standardMaterial;
    }
}
```

### Emission and Bloom Considerations

**Best Practices:**
- Keep emission values below 1.0 for most objects
- Reserve high emission (1.0+) for truly important items
- Balance bloom intensity in post-processing to avoid oversaturation
- Test on target hardware with expected object counts

**Bloom Settings Guide:**
```yaml
# Conservative (better performance)
Bloom Intensity: 0.2 - 0.3
Shimmer Emission: 0.2 - 0.5

# Balanced (recommended)
Bloom Intensity: 0.3 - 0.5
Shimmer Emission: 0.3 - 0.7

# High Impact (performance cost)
Bloom Intensity: 0.5 - 1.0
Shimmer Emission: 0.5 - 1.5
```

### Material Instancing

**Problem:** Creating material instances for every object increases memory usage.

**Solution:** Share materials when possible and use Material Property Blocks for per-object customization:

```csharp
using UnityEngine;

public class ShimmerPropertyBlock : MonoBehaviour
{
    private Renderer rend;
    private MaterialPropertyBlock propertyBlock;
    
    void Start()
    {
        rend = GetComponent<Renderer>();
        propertyBlock = new MaterialPropertyBlock();
    }
    
    public void SetShimmerColor(Color color)
    {
        // Modify per-object property without creating material instance
        propertyBlock.SetColor("_HighlightColor", color);
        rend.SetPropertyBlock(propertyBlock);
    }
    
    public void SetShimmerSpeed(float speed)
    {
        propertyBlock.SetFloat("_Speed", speed);
        rend.SetPropertyBlock(propertyBlock);
    }
}
```

**Benefits:**
- ✅ Reduced memory usage
- ✅ Better batching potential
- ✅ Cleaner memory management

---

## Visual Design Guidelines

### Color Selection

#### Contrast is Key
- Ensure highlight color contrasts with base color
- Test visibility in various lighting conditions
- Consider colorblind-friendly palettes

**Contrast Matrix:**
| Base Color | Good Highlight | Avoid |
|------------|----------------|-------|
| Dark | White, Yellow, Cyan | Gray, Dark Blue |
| Light | Blue, Purple, Red | White, Yellow |
| Blue | Yellow, Orange, White | Cyan, Light Blue |
| Red | Cyan, Yellow, White | Orange, Pink |

#### Color Consistency
Establish color meanings and stick to them:

```yaml
# Example color language
Gold: Premium/Valuable items
Blue: Common/Standard items
Purple: Rare/Epic items
Green: Positive effects (health, buffs)
Red: Negative effects (danger, warnings)
Yellow: Quest/Important interactions
Cyan: Technology/Magical
White: Divine/Pure/Maximum importance
```

### Animation Speed Guidelines

**Speed Psychology:**
- **Slow (0.5-1.5)**: Important, premium, deliberate
- **Medium (1.5-3.0)**: Standard, balanced attention
- **Fast (3.0-5.0)**: Urgent, action-required, high energy

**Context Matters:**
- Faster speeds in action sequences
- Slower speeds in calm/menu areas
- Match game pace and mood

### Wave Pattern Hierarchy

Use different patterns to create visual hierarchy:

```yaml
# Tier 1 - Most Important
Wave Tiling: Pulse
Use for: Quest objectives, critical items

# Tier 2 - Important
Wave Tiling: Diagonal 1 or Bottom To Top
Use for: Collectibles, power-ups

# Tier 3 - Standard
Wave Tiling: Diagonal 2 or 3
Use for: Common interactables
```

---

## User Experience

### Attention Management

**The 3-Object Rule:** Never have more than 3 highly attention-grabbing shimmer effects on screen simultaneously.

**Priority System:**
```csharp
public enum ShimmerPriority
{
    Low,      // Subtle, background effect
    Medium,   // Standard highlight
    High,     // Important, pulsing
    Critical  // Most important, highest emission
}

public void SetPriority(ShimmerPriority priority)
{
    switch(priority)
    {
        case ShimmerPriority.Low:
            SetShimmer(1.0f, 0.2f, "Diagonal1");
            break;
        case ShimmerPriority.Medium:
            SetShimmer(2.0f, 0.4f, "Diagonal1");
            break;
        case ShimmerPriority.High:
            SetShimmer(2.5f, 0.6f, "Pulse");
            break;
        case ShimmerPriority.Critical:
            SetShimmer(3.0f, 0.9f, "Pulse");
            break;
    }
}
```

### Accessibility Considerations

#### Motion Sensitivity
Provide option to reduce animation speed:

```csharp
public class AccessibilitySettings : MonoBehaviour
{
    public static float motionMultiplier = 1.0f; // 0.5 for reduced motion
    
    public void ApplyMotionSetting(Material shimmerMaterial, float baseSpeed)
    {
        shimmerMaterial.SetFloat("_Speed", baseSpeed * motionMultiplier);
    }
}
```

#### Colorblind Modes
Offer alternative color schemes:

```csharp
public void ApplyColorblindMode(ColorblindMode mode)
{
    switch(mode)
    {
        case ColorblindMode.Deuteranopia: // Green-blind
            // Avoid green highlights, use blue/yellow
            break;
        case ColorblindMode.Protanopia: // Red-blind
            // Avoid red highlights, use blue/yellow
            break;
        case ColorblindMode.Tritanopia: // Blue-blind
            // Avoid blue highlights, use red/yellow
            break;
    }
}
```

#### Photosensitivity
- Avoid fast pulsing effects (>4Hz)
- Limit high-contrast flashing
- Provide toggle for emission effects

```csharp
public void SetPhotosensitiveFriendly(bool enabled)
{
    if (enabled)
    {
        // Reduce emission, slow down speed
        material.SetFloat("_Emission", 0.2f);
        material.SetFloat("_Speed", Mathf.Min(currentSpeed, 2.0f));
    }
}
```

---

## Testing & Validation

### Testing Checklist

#### Visual Testing
- [ ] Test in all intended lighting conditions (day/night/indoor)
- [ ] Verify visibility from expected camera distances
- [ ] Check appearance from all relevant angles
- [ ] Test with bloom on and off
- [ ] Validate color contrast in-game

#### Performance Testing
- [ ] Profile with expected number of shimmer objects
- [ ] Test on minimum spec hardware
- [ ] Monitor frame rate in worst-case scenarios
- [ ] Check memory usage with material instances

#### UX Testing
- [ ] Verify players notice important shimmered objects
- [ ] Ensure no confusion about shimmer meaning
- [ ] Test that effects aren't overwhelming
- [ ] Validate accessibility settings work

### Common Issues and Solutions

#### Issue: Shimmer Not Visible
**Solutions:**
- Increase emission value
- Choose higher contrast highlight color
- Enable bloom post-processing
- Increase wave scale for larger bands

#### Issue: Effect Too Subtle
**Solutions:**
- Increase speed for more movement
- Brighten highlight color
- Increase emission
- Switch to Pulse wave pattern

#### Issue: Effect Too Distracting
**Solutions:**
- Reduce speed
- Lower emission
- Switch from Pulse to Diagonal pattern
- Reduce number of simultaneous shimmer objects

#### Issue: Performance Problems
**Solutions:**
- Implement distance culling
- Reduce emission (lower bloom cost)
- Use Material Property Blocks
- Implement LOD system
- Reduce total shimmer object count

---

## Scripting Best Practices

### Initialization
```csharp
using UnityEngine;

public class ShimmerController : MonoBehaviour
{
    private Material shimmerMaterial;
    private Renderer objectRenderer;
    
    // Cache material reference on Start, not every frame
    void Start()
    {
        objectRenderer = GetComponent<Renderer>();
        shimmerMaterial = objectRenderer.material; // Creates instance
    }
    
    // Alternative: shared material (no instancing)
    void StartShared()
    {
        objectRenderer = GetComponent<Renderer>();
        shimmerMaterial = objectRenderer.sharedMaterial; // Shares material
    }
}
```

### Property Updates
```csharp
// Good: Cache property IDs
private static readonly int SpeedProperty = Shader.PropertyToID("_Speed");
private static readonly int EmissionProperty = Shader.PropertyToID("_Emission");

void UpdateShimmer(float speed, float emission)
{
    shimmerMaterial.SetFloat(SpeedProperty, speed);
    shimmerMaterial.SetFloat(EmissionProperty, emission);
}

// Avoid: String-based property access every frame
void UpdateShimmerBad(float speed, float emission)
{
    shimmerMaterial.SetFloat("_Speed", speed); // Slower
    shimmerMaterial.SetFloat("_Emission", emission); // Slower
}
```

### Cleanup
```csharp
void OnDestroy()
{
    // Destroy material instance to prevent memory leaks
    if (shimmerMaterial != null)
    {
        Destroy(shimmerMaterial);
    }
}
```

### Object Pooling
```csharp
public class ShimmerObjectPool : MonoBehaviour
{
    public GameObject shimmerPrefab;
    private Queue<GameObject> pool = new Queue<GameObject>();
    
    public GameObject GetShimmerObject()
    {
        if (pool.Count > 0)
        {
            GameObject obj = pool.Dequeue();
            obj.SetActive(true);
            return obj;
        }
        return Instantiate(shimmerPrefab);
    }
    
    public void ReturnShimmerObject(GameObject obj)
    {
        obj.SetActive(false);
        pool.Enqueue(obj);
    }
}
```

---

## Platform-Specific Considerations

### Mobile Platforms

**Recommendations:**
- Keep emission below 0.5
- Limit to 10-15 visible shimmer objects
- Use simpler wave patterns (Diagonal over Pulse)
- Consider disabling bloom on low-end devices
- Test on actual devices, not just editor

**Mobile-Optimized Settings:**
```yaml
Speed: 2.0
WaveScale: 1.5
Emission: 0.3
Bloom Intensity: 0.2 (or disabled)
Max Visible Objects: 10-15
```

### VR Platforms

**Special Considerations:**
- Reduce emission to avoid eye strain
- Slower animation speeds (1.0-2.0)
- Be extra cautious with pulsing effects
- Test for motion sickness potential
- Ensure effect works from all viewing angles

**VR-Optimized Settings:**
```yaml
Speed: 1.5 (slower)
Emission: 0.2 (subtle)
Wave Tiling: Diagonal 1 (avoid Pulse)
Photosensitive Mode: Enabled
```

### Console Platforms

**Performance Targets:**
- Maintain 60 FPS (or 30 FPS for 4K)
- Test with console-specific bloom implementations
- Verify HDR compliance if supporting HDR

---

## Quality Assurance

### Pre-Release Checklist

- [ ] All shimmer objects have appropriate priority levels
- [ ] Color scheme is consistent across all categories
- [ ] Performance tested on minimum spec hardware
- [ ] Accessibility options implemented and tested
- [ ] No more than 3 high-priority shimmer objects visible simultaneously
- [ ] Wave patterns are appropriate for object types
- [ ] Emission values are reasonable and tested with bloom
- [ ] Material instances are properly cleaned up
- [ ] Distance culling implemented for large scenes
- [ ] Documentation for team on shimmer usage guidelines

---

## Next Steps

- Review [Use Cases](use-cases.md) for implementation ideas
- Check [Material Properties](../user-guide/material-properties.md) reference
- Explore [Shimmer Controls](../user-guide/shimmer-controls.md) details
- Read [FAQ](../reference/faq.md) for common questions

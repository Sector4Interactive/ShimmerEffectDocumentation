# Support

Need help with Shimmer Effect Highlight? Here's how to get assistance.

## Documentation

Before reaching out for support, please check these resources:

### 📚 Primary Documentation
- **[Getting Started](getting-started/installation.md)**: Installation and basic setup
- **[User Guide](user-guide/material-properties.md)**: Comprehensive property reference
- **[FAQ](reference/faq.md)**: Answers to common questions
- **[Best Practices](examples/best-practices.md)**: Optimization and tips

### 🎓 Learning Resources
- **Demo Scene**: Open and explore the included demo scene
- **[Use Cases](examples/use-cases.md)**: Real-world implementation examples
- **[Wave Tiling Options](user-guide/wave-tiling.md)**: Detailed pattern guide

---

## Self-Help Troubleshooting

### Common Issues & Quick Fixes

#### Material Appears Pink/Magenta
✅ **Solution:**
1. Verify URP is enabled: **Edit > Project Settings > Graphics**
2. Install Shader Graph: **Window > Package Manager > Shader Graph**
3. Reimport the asset

#### No Animation Visible
✅ **Solution:**
- Enter **Play Mode** - animations only run at runtime
- Shimmer is time-based and doesn't animate in Scene view

#### Effect Too Subtle
✅ **Solution:**
1. Increase **Emission** value (0.5-0.8)
2. Enable **Bloom** post-processing
3. Choose brighter **Highlight Color**
4. Increase **Speed** for more movement

#### Effect Too Strong
✅ **Solution:**
1. Reduce **Emission** (0.2-0.4)
2. Decrease **Speed** (1.0-1.5)
3. Switch from Pulse to Diagonal pattern
4. Lower bloom intensity

#### Performance Issues
✅ **Solution:**
1. Reduce number of shimmer objects
2. Implement distance culling
3. Lower emission values
4. See [Performance Optimization](examples/best-practices.md#performance-optimization)

---

## Getting Support

### Before Contacting Support

Please gather the following information:

- **Unity Version**: (e.g., 2022.3.10f1)
- **Render Pipeline**: URP version
- **Platform**: Windows/Mac/Linux, Mobile, Console
- **Asset Version**: Check Asset Store for version number
- **Issue Description**: Clear description of the problem
- **Steps to Reproduce**: How to recreate the issue
- **Screenshots/Videos**: Visual documentation of the problem
- **Console Errors**: Any error messages from Unity Console

### Support Channels

#### 1. Asset Store Page
The primary support channel is through the Unity Asset Store:

1. Visit the **Shimmer Effect Highlight** asset page
2. Click the **"Support"** or **"Contact Publisher"** button
3. Include all relevant information listed above

**Response Time:** Typically 1-3 business days

#### 2. Publisher Contact
- **Publisher**: GameReadyTools
- **Contact Method**: Via Unity Asset Store messaging system

#### 3. Community Support
- **Unity Forums**: Search for existing threads or create new topic
- **Discord/Community**: Check asset description for community channels

---

## Feature Requests

Have an idea for improving the asset? We'd love to hear it!

### How to Submit Feature Requests

1. Visit the Asset Store page
2. Contact the publisher with:
   - **Feature Description**: Clear explanation of what you'd like
   - **Use Case**: Why this feature would be valuable
   - **Priority**: How important is this to your workflow

### Popular Requested Features
Feature requests help guide future development. Common requests include:
- Additional wave patterns
- HDRP version
- Built-in RP compatibility
- Mobile optimization presets
- Additional effect variations

---

## Bug Reports

Found a bug? Help us fix it!

### Bug Report Template

```
**Bug Title:** [Short description]

**Unity Version:** [Your Unity version]
**URP Version:** [Your URP version]
**Asset Version:** [Asset version from store]
**Platform:** [Windows/Mac/Mobile/etc.]

**Description:**
[Clear description of the bug]

**Steps to Reproduce:**
1. [First step]
2. [Second step]
3. [Third step]

**Expected Behavior:**
[What should happen]

**Actual Behavior:**
[What actually happens]

**Screenshots/Console Errors:**
[Attach images or paste error messages]

**Frequency:**
[Always / Sometimes / Rarely]
```

### Critical vs Non-Critical Bugs

**Critical** (Report immediately):
- Shader compilation errors
- Crashes
- Data loss
- Complete feature failure

**Non-Critical** (Can be reported normally):
- Visual glitches
- Minor inconsistencies
- Performance variations
- Documentation errors

---

## Asset Updates

### Checking for Updates

1. Open Unity
2. Go to **Window > Package Manager**
3. Select **My Assets** from dropdown
4. Find "Shimmer Effect Highlight"
5. Check if "Update" button is available

### Update Notes

Always check the **Asset Store page** for:
- Version history
- Changelog
- Breaking changes
- New features

### After Updating

1. **Backup your project** before updating
2. Read the changelog for breaking changes
3. Test in a separate branch if possible
4. Re-test all your shimmer implementations

---

## Additional Resources

### Unity Documentation
- [Universal Render Pipeline](https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@latest)
- [Shader Graph](https://docs.unity3d.com/Packages/com.unity.shadergraph@latest)
- [Post-Processing](https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@latest/manual/post-processing-ssao.html)

### Community Resources
- Unity Forums: General URP and shader discussions
- Unity Answers: Technical Q&A
- YouTube: Unity shader tutorials and URP guides

### Learning Materials
- Unity Learn: Free Unity courses
- Shader Graph tutorials: Visual shader creation
- URP optimization guides: Performance tips

---

## Business Inquiries

### Bulk Licensing
For team/studio licenses or bulk purchases, contact the publisher through the Asset Store.

### Custom Development
For custom shader development or modifications beyond the asset's scope, inquire about consulting services through the publisher.

### Integration Support
For assistance integrating the asset into large projects or specialized workflows, ask about premium support options.

---

## Feedback

Your feedback helps improve the asset!

### How to Provide Feedback

**Positive Experiences:**
- Leave a review on the Asset Store page
- Share your projects using the asset (with permission)
- Recommend to other developers

**Constructive Criticism:**
- Contact publisher with specific suggestions
- Explain what could be improved and why
- Provide examples or alternatives

**Showcase Your Work:**
If you create something awesome with this asset, we'd love to see it! Share:
- Screenshots
- Videos
- Demo builds
- Release announcements

---

## Response Times

**Expected Response Times:**
- **Asset Store Support**: 1-3 business days
- **Critical Bugs**: Priority handling
- **General Questions**: 2-5 business days
- **Feature Requests**: Acknowledged within 1 week

**Please Note:**
- Support is provided in English
- Response times may vary during holidays
- Complex issues may require additional time

---

## Legal & Licensing

### License Questions
For questions about:
- Commercial use rights
- Redistribution
- Multi-seat licensing
- Terms of service

Contact the publisher through the Asset Store.

### EULA
Standard Unity Asset Store End User License Agreement applies. Read the full EULA on the Asset Store page.

---

## Quick Reference Card

| Issue Type | First Action |
|------------|--------------|
| Can't install | Check URP setup, Shader Graph |
| Not animating | Enter Play Mode |
| Pink material | Verify URP, install packages |
| Visual issue | Check FAQ, adjust properties |
| Performance | See Best Practices guide |
| Bug | Prepare bug report template |
| Feature idea | Contact via Asset Store |
| General help | Read documentation first |

---

## Thank You!

Thank you for using Shimmer Effect Highlight! Your support and feedback help make this asset better for everyone.

**Happy Developing!** ✨

---

*Last Updated: November 2025*  
*Documentation Version: 1.0*

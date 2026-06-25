# ✨ GestureForge

## AI-Powered Gesture Controlled Particle Morphing System

---

## 📖 Overview

**GestureForge** is an interactive web application that uses AI-powered hand tracking to control a dynamic 3D particle system in real-time. By simply moving your hand in front of your webcam, you can morph thousands of glowing particles into different shapes, control their colors, and scale them with intuitive gestures.

---

## 🎯 Features

### Core Gesture Controls

| Gesture | Action |
|---------|--------|
| 👊 **Fist** | Morph to **Cloud** (default) |
| ☝️ **One Finger** | Morph to **Heart** |
| ✌️ **Two Fingers** | Morph to **Saturn** (with rings) |
| 🤟 **Three Fingers** | Morph to **Flower** |
| ✋ **Open Hand** | Morph to **Fireworks** (explosive burst) |
| 🖐️ **Pinch** (Thumb + Index) | Scale particles (expand/contract) |
| ↔️ **Move Hand** | Change particle colors (hue shift) |

### Visual Effects

- ✨ **15,000 glowing particles** with additive blending
- 🌈 **Real-time color shifting** based on hand position
- 🌀 **Organic particle motion** with wave effects
- 💫 **Twinkle effect** on individual particles
- 🌊 **Camera breathing** for immersive feel
- ⚡ **Flash effect** on shape changes
- 🎨 **Per-particle color variation** for depth

### Technical Features

- 🎥 **Real-time webcam integration** with MediaPipe
- 🖐️ **AI-powered hand landmark detection** (21 points)
- 🔄 **Smooth shape morphing** with interpolation
- 📱 **Responsive design** for all screen sizes
- 🎮 **Click to reset camera** rotation
- ⚡ **GPU accelerated** rendering

---

## 🛠️ Technology Stack

### Frontend
- **HTML5** - Structure
- **CSS3** - Styling with gradients and glass-morphism
- **JavaScript (ES Modules)** - Application logic

### 3D Rendering
- **Three.js** (v0.160.0) - 3D particle engine
- **Custom Shaders** - Vertex and fragment shaders for particle effects

### AI & Computer Vision
- **MediaPipe Tasks Vision** (v0.10.3) - Hand landmark detection
- **HandLandmarker** - 21-point hand tracking model

### Build Tools
- **Import Maps** - Module dependency management
- **CDN** - All libraries loaded from CDN

---

## 🚀 Getting Started

### Prerequisites
- A modern web browser (Chrome, Firefox, Edge, Safari)
- A working webcam
- Internet connection (for loading AI models)

### Installation

1. **Clone or download** the HTML file
2. **Open** the file in your browser
3. **Allow camera access** when prompted
4. **Wait** for the AI model to load (few seconds)
5. **Start gesturing!** 🖐️

### Quick Start
```html
<!-- Just open the HTML file in your browser -->
<!-- No server required! Works directly from file system -->
```

### Browser Compatibility
| Browser | Version | Support |
|---------|---------|---------|
| Chrome | 90+ | ✅ Full |
| Firefox | 88+ | ✅ Full |
| Edge | 90+ | ✅ Full |
| Safari | 14+ | ✅ Full |

---

## 🎮 How to Use

### 1. Setup
1. Position yourself in front of your webcam
2. Ensure good lighting for hand detection
3. Wait for "Loading AI Vision..." to disappear
4. You'll see your mirrored video feed in the bottom-right corner

### 2. Basic Gestures
- **Show different finger counts** to change shapes
- **Move your hand left/right** to change colors
- **Pinch thumb and index** to scale particles
- **Click anywhere** to reset the camera view

### 3. Advanced Tips
- For best results, keep your hand **well-lit** and **centered**
- The system works best with **clear background** behind your hand
- Experiment with **slow movements** for smooth transitions
- Try **combining gestures** (e.g., pinch while moving)

---

## 🎨 Shape Gallery

### 🌥️ Cloud
A soft, organic nebula-like formation with tendrils
- *Default shape*
- *Best for ambient visualization*

### ❤️ Heart
A 3D heart shape using parametric equations
- *Perfect for romantic or emotional contexts*
- *Rotates to face camera*

### 🪐 Saturn
A planet with rings
- *70% sphere, 30% ring particles*
- *Ring is tilted for 3D effect*

### 🌸 Flower
A floral pattern using rose curve mathematics
- *3-4 petals with organic variation*
- *Depth variation for 3D feel*

### 🎆 Fireworks
An explosive radial burst
- *Uniform sphere distribution*
- *Streaks for dynamic effect*

---

## 🔧 Customization

### Adjusting Particle Count
```javascript
const CONFIG = {
    particleCount: 15000,  // Change this value
    // ...
};
```

### Changing Morph Speed
```javascript
const CONFIG = {
    lerpSpeed: 0.07,  // Higher = faster morph
    // ...
};
```

### Modifying Colors
```javascript
// In the animation loop
color.setHSL(
    hue,           // 0-1 (controlled by hand)
    0.9,           // Saturation
    0.5 + 0.3 * expansion // Brightness
);
```

### Adding New Shapes
1. Add a new case to the `generateShape()` function
2. Define your particle positions
3. Add the shape name to the gesture mapping
4. Update the UI with new gesture info

---

## 📁 File Structure

```
GestureForge/
├── index.html              # Single-file application
│   ├── HTML Structure      # UI elements
│   ├── CSS Styles          # Visual design
│   └── JavaScript          # Application logic
│       ├── Three.js Setup  # 3D engine
│       ├── Particle System # Particle management
│       ├── Shape Generators # Shape definitions
│       ├── MediaPipe AI    # Hand tracking
│       └── Animation Loop  # Rendering
└── README.md              # This file
```

---

## 🧠 How It Works

### 1. Hand Detection Pipeline
```
Webcam → MediaPipe HandLandmarker → 21 Landmark Points
         ↓
    Process Landmarks
         ↓
   Calculate Gestures
```

### 2. Particle System Flow
```
Shape Definition → Target Positions → Smooth Morphing
         ↓
   Expansion + Rotation + Color
         ↓
   Render to Screen (60fps)
```

### 3. Gesture Recognition
- **Finger Counting**: Detects raised fingers using wrist-relative Y position
- **Pinch Detection**: Measures distance between thumb and index tips
- **Position Tracking**: Tracks palm center for color control

---

## 🎯 Performance Optimization

### Current Optimizations
- ✅ GPU-accelerated rendering
- ✅ Efficient particle updates (15k particles)
- ✅ Shader-based effects (no CPU overhead)
- ✅ Reduced pixel ratio on mobile
- ✅ Minimal DOM operations

### Performance Tips
- Use **GPU** delegate in MediaPipe
- Keep **particle count** reasonable (10k-20k)
- Avoid **expensive calculations** per frame
- Use **BufferGeometry** for efficient updates

---

## 🐛 Troubleshooting

### Common Issues

| Issue | Solution |
|-------|----------|
| Camera not working | Check browser permissions |
| AI model not loading | Check internet connection |
| Slow performance | Reduce particle count |
| Gestures not recognized | Improve lighting |
| No video feed | Refresh page |
| Particles not moving | Check console for errors |

### Debug Mode
Open browser console (F12) to see:
- Hand landmark data
- Shape transitions
- Performance metrics
- Error messages

---

## 🚧 Future Improvements

### Planned Features
- [ ] Multiple hand support (two hands)
- [ ] Custom shape upload
- [ ] Particle trails and motion blur
- [ ] Audio-reactive mode
- [ ] Export/Share snapshots
- [ ] Touch/mouse fallback
- [ ] More gesture types (swipe, circle, etc.)
- [ ] Particle physics simulation
- [ ] Virtual reality support
- [ ] Mobile optimization

---

## 🤝 Contributing

### Want to contribute?

1. **Fork** the repository
2. **Create** a feature branch
3. **Add** your improvements
4. **Submit** a pull request

### Development Setup
```bash
# No build tools needed!
# Just edit the HTML file directly
# Use Live Server or similar for development
```

---

## 📄 License

**MIT License** - Free for personal and commercial use

---

## 🙏 Acknowledgments

- **MediaPipe** - For amazing hand tracking
- **Three.js** - For powerful 3D rendering
- **All contributors** - For testing and feedback

---

## 📞 Contact & Support

- **Issues**: Report on GitHub
- **Questions**: Open a discussion
- **Suggestions**: Feature requests welcome

---

## 🌟 Credits

**Created with ❤️ by [Your Name]**

Special thanks to:
- The MediaPipe team for their amazing AI models
- The Three.js community for great documentation
- Everyone who tested and provided feedback

---

## 📊 Project Status

| Aspect | Status |
|--------|--------|
| Core Features | ✅ Complete |
| Gesture Recognition | ✅ Working |
| Particle System | ✅ Optimized |
| UI/UX | ✅ Polished |
| Documentation | ✅ Full |
| Mobile Support | ✅ Responsive |
| Browser Support | ✅ Modern browsers |

---

## 🎥 Demo

[Live Demo](https://your-demo-link.com)

*Note: Requires webcam access*

---

## 📝 Changelog

### v1.0.0 (Current)
- Initial release
- 5 gesture-controlled shapes
- Real-time color control
- Pinch scaling
- 10+ visual effects
- Responsive design
- Full documentation

---

**✨ GestureForge - Shape the future with your hands!**

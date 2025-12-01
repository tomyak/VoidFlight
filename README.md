# Void Flight

A WebGL-based flight simulator featuring procedurally generated terrain, realistic gravity physics, and intuitive fly-by-sight controls.

## Features

### Flight Mechanics
- **Fly-by-sight controls** - Ship automatically tracks your camera view
- **Gravity physics** - Nose down increases speed, nose up decreases speed
- **Smooth tracking** - Ship gradually follows where you look for realistic flight feel
- **Speed range** - 0.5 to 2.0 MACH with manual throttle override

### Visual Systems
- **Procedural terrain** - Infinite world generation with varied landscapes
- **Mountains and valleys** - Dynamic elevation with jagged peaks
- **Urban areas** - Procedurally placed buildings with lit windows
- **Day/night cycle** - 5-minute cycle with dynamic lighting
- **Volumetric fog** - Atmospheric depth with configurable density
- **Headlight system** - Quad spotlight array with focus/search modes

### Navigation
- **HUD** - Altitude and speed readouts
- **Compass** - 360° heading indicator with N/E/S/W markers
- **Artificial horizon** - Pitch and roll indicator
- **Velocity vector** - Cyan reticule showing ship nose direction
- **Minimap** - Top-down view showing buildings (cyan) and mountains (red)

### Creatures
- **Animated monsters** - Black humanoid figures with reflective eyes
- **AI behavior** - Walking, idle breathing, procedural animation
- **Terrain following** - Monsters navigate the landscape

## Controls

### Desktop
- **Mouse** - Look around to steer (ship follows your view)
- **W/S** - Increase/decrease throttle
- **Arrow Keys** - Direct camera control
- **0-9** - Set headlight intensity (0=off, 9=max)
- **+/=** - Toggle headlight mode (focus/search)

### Mobile
- **Device Orientation** - Tilt phone to look and steer
- **Touch Controls** - On-screen joystick and throttle (if enabled)

## How to Run

1. Open `index.html` in a modern web browser
2. Click "Start" to begin
3. Grant device orientation permission (mobile only)
4. Look around to fly - the ship follows your gaze
5. Point down to dive and gain speed, up to climb and slow down

## Technical Details

### Technology Stack
- **Three.js** (r128) - 3D graphics rendering
- **Perlin Noise** - Procedural terrain generation
- **Canvas API** - Texture generation and minimap rendering

### Performance
- **Chunk-based rendering** - 6-chunk render distance
- **View frustum culling** - Only render visible terrain
- **Dynamic LOD** - Optimized geometry for distant objects
- **Fog optimization** - Reduced density for better visibility

### World Generation
- **Chunk size** - 200 units
- **Render distance** - 1200 units (6 chunks)
- **Camera far plane** - 5000 units
- **Terrain features** - Buildings, mountains, valleys generated using multi-octave noise

## Configuration

Key parameters in `CONFIG` object (line 249):

```javascript
{
    chunkSize: 200,        // Size of each terrain chunk
    renderDistance: 6,     // Chunks to render around player
    minSpeed: 0.5,         // Minimum flight speed
    maxSpeed: 2.0,         // Maximum flight speed
    dayDuration: 300000,   // Day/night cycle (5 minutes)
    minLight: 1.5,         // Nighttime ambient light
    maxLight: 5.5          // Daytime ambient light
}
```

### Adjustable Physics

**Gravity strength** (line 632):
```javascript
const gravityFactor = 0.002; // Increase for stronger gravity
```

**Ship tracking speed** (line 695):
```javascript
const trackingSpeed = 0.08; // 0.0-1.0, higher = more responsive
```

**Fog density** (line 326):
```javascript
scene.fog = new THREE.FogExp2(CONFIG.bgColor, 0.0015);
```

## Project Structure

```
CyberFlight/
├── index.html      # Main application (terrain, flight, rendering)
├── monster.js      # Standalone monster demo
└── README.md       # This file
```

## Browser Compatibility

- Chrome/Edge 90+
- Firefox 88+
- Safari 14+
- Mobile browsers with WebGL support

**Note:** Device orientation requires HTTPS on iOS 13+

## License

Open source - feel free to modify and extend.

# 🕷️ SpideyHand — Hand-Tracking AR Experience

> Real-time hand tracking meets Spider-Man. Shoot webs, trigger beats, and warp reality — all through your webcam.

**GitHub:** [LihanCanCode/HandWeb](https://github.com/LihanCanCode/HandWeb)

---

## 📋 Project Description

**SpideyHand** is an advanced hand-tracking augmented reality (AR) application that transforms your webcam feed into an immersive, interactive visual experience. Powered by **MediaPipe Hands**, it renders real-time neon skeletal overlays, physical particle effects, and a full Spider-Man themed mode — complete with web shooting, synthesized sound effects, and a live beat engine.

---

## ✨ Features

### 🌐 Core AR Engine
- **Real-time Hand Tracking** — MediaPipe Hands with up to 2-hand simultaneous detection
- **Neon Skeleton Rendering** — Glowing connectors and landmark dots per theme
- **Fingertip Spark Particles** — Constant particle emission from fingertip landmarks
- **Matrix Rain Background** — Animated katakana rain that accelerates with hand speed
- **Motion Blur Trail** — Ghost-frame compositing for smooth movement trails
- **FPS Counter** — Live performance metrics in the HUD

### 👋 Gesture System
| Gesture | Action |
|---|---|
| **Pinch** (thumb + index) | Creates a visual shockwave ripple |
| **Open Hand** | Tracked as spread percentage |
| **Thwip** (index + pinky + thumb extended, middle + ring curled) | Fires a Spider-Man web |

### 🎨 Visual Themes (6 total)
| Theme | Color Profile |
|---|---|
| **Rainbow** | Full HSL spectrum, shifts over time |
| **Cyberpunk** | Neon pink `#ff003c` + cyan `#00f0ff` |
| **Lava** | Fiery red-orange with pulsing brightness |
| **Ocean** | Deep teal and aqua blues |
| **Galaxy** | Deep purple with sine-wave color drift |
| **Spider** ⭐ | Icy blue-white `#d5f4ff` with full Spider-Man mode |

### ⚡ Two-Hand Interactions
- **Lightning Arcs** — Jagged electric bolts between fingertips when hands are close
- **Gradient Connection Lines** — Flowing colour-gradient lines linking both hands
- **Mandala** — Rotating geometric pattern drawn from all 10 fingertip positions

---

## 🕷️ Spider Mode (Special)

When the **Spider** theme is active, the entire experience shifts:

### Web Shooting
1. Make the **Thwip** gesture (Spider-Man hand sign)
2. A web strand shoots from your palm toward the screen
3. A full **comic-book spider web** expands where it lands:
   - 10 radial spokes, 7 concentric rings
   - Natural Bezier curve sag (thicker outer rings, thinner inner)
   - **Grow-in animation** — scales from 0→1 in ~0.25s on impact
   - **Fade-out** — smoothly dissolves over the last 0.55s of a 2-second lifetime
   - Rendered on a dedicated `#webCanvas` layer (no blend-mode conflicts)
4. Web debris particles burst when the web dissolves

### Spider HUD (top-left panel)
Replaces the generic HUD with a themed readout:

| Field | Description |
|---|---|
| **Targets Tracked** | Number of hands detected |
| **Web Status** | `READY` (green) → `THWIPPING!` (red pulse) |
| **Gesture** | `THWIP ✦` / `PINCH` / `OPEN HAND` / `FIST` |
| **Webs Fired** | Session counter — resets when leaving Spider mode |
| **Web Active** | `⬤ LIVE` (red pulsing dot) / `— IDLE` |

### Spider-Verse Background Music 🎵
Fully synthesized via **Web Audio API** — no external audio files. Plays automatically in Spider mode:

| Layer | Sound |
|---|---|
| **808 Kick** | Deep sine sweep 180Hz→38Hz with click transient |
| **Snare** | Bandpass noise + triangle body tone |
| **Hi-hats** | High-pass noise (closed 16th + open hat off-beats) |
| **Bass Line** | Square-wave synth in E minor walking pattern |
| **Atmospheric Pad** | Detuned E minor chord (slow 2.5s fade-in) |

Beat is scheduled with the Web Audio look-ahead pattern (zero drift, precise timing at **88 BPM**).

### Spider Hand Web Overlay
In Spider mode, a glowing web mesh is drawn over the detected hand itself:
- Thin skeleton bones in translucent web-blue
- Radial spokes from palm to fingertips
- 3 concentric curved rings (fingertips, knuckles, base knuckles)

---

## 🎵 Audio System

| Sound | Trigger |
|---|---|
| **Thwip** | Noise burst + frequency sweep on web shoot |
| **Spider-Verse Beat** | Looping drum/bass/pad in Spider mode |
| **Dual-Hand Hum** | Sub-bass hum when both hands are visible (non-Spider modes) |

> Note: Pinch no longer triggers a sound (visual shockwave only).

All audio passes through a **DynamicsCompressor → MasterGain** chain to prevent clipping.

---

## 🚀 Getting Started

### Prerequisites
- Node.js 14+
- Modern browser with webcam access (Chrome recommended)

### Setup
```bash
git clone https://github.com/LihanCanCode/HandWeb.git
cd HandWeb
node server.js
```
Then open **http://localhost:8000** in your browser.

### Usage
1. Click **Enter Experience** (required to initialize AudioContext)
2. Grant camera permissions
3. Move your hands in front of the webcam
4. Switch themes using the pill-buttons at the bottom
5. In Spider mode — make the Thwip gesture to shoot webs!

---

## 🗂️ Project Structure

```
HandWeb/
├── index.html      # Entire application (AR engine, audio, UI)
├── server.js       # Minimal Node.js static file server
└── README.md       # This file
```

---

## 🛠️ Architecture Notes

### Canvas Stack (z-index order)
```
video          z:0   Raw camera feed (mirrored, darkened)
bgCanvas       z:1   Matrix rain effect (persistent trails)
webCanvas      z:3   Spider web overlays (clear each frame)
mainCanvas     z:5   Skeleton, particles, effects (screen blend)
UI overlays    z:10  HUD panels, theme buttons
```

### Beat Scheduler
Uses the **Web Audio look-ahead scheduler** pattern:
- `setInterval` every 25ms checks if notes need scheduling
- Schedules 100ms ahead into the future
- Prevents audio stuttering caused by JavaScript timer imprecision

---

## 📱 Browser Support
| Browser | Status |
|---|---|
| Chrome | ✅ Recommended |
| Edge | ✅ Supported |
| Firefox | ✅ Supported |
| Safari | ⚠️ May need permissions adjustment |

---

## 🔒 Required Permissions
- **Camera** — for MediaPipe hand tracking
- **Audio** — for Web Audio API (granted on first click)

---

## 🎨 Adding Custom Themes

1. Open `index.html`
2. Add an entry to the `themes` object:
```javascript
'MyTheme': (t, index, total) => `hsl(${300 + index * 20}, 80%, 60%)`
```
3. Add a button to the `#themes` div in HTML:
```html
<button class="theme-btn" data-theme="MyTheme">MyTheme</button>
```

---

## 📄 License
MIT License — see LICENSE for details.

## 🎓 Acknowledgments
- **[MediaPipe](https://mediapipe.dev/)** — Real-time hand landmark detection
- **Web Audio API** — Full audio synthesis engine
- **Google Fonts** — Inter typeface

---

**SpideyHand** — Your friendly neighbourhood AR experience. 🕸️

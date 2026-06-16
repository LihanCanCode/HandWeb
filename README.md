# HandConnect: Hand-Tracking AR Experience

## 📋 Project Description
HandConnect is an advanced hand-tracking augmented reality (AR) application that transforms your webcam feed into an interactive neon visual experience. Using MediaPipe for real-time hand detection, it creates stunning visual effects that respond to your hand movements, gestures, and interactions.

## ✨ Key Features
* **Real-time Hand Tracking:** Uses MediaPipe Hands for accurate detection and landmark tracking
* **Interactive Gestures:** Pinch your fingers to create shockwave effects with sound
* **Multiple Visual Themes:** Rainbow, Cyberpunk, Lava, Ocean, and Galaxy themes
* **Dynamic Audio Effects:** Sound effects that respond to hand movements and gestures
* **Matrix Rain Background:** Animated background that reacts to hand speed
* **Lightning Effects:** Electric arcs between hands when they're close together
* **Mandala Visualization:** Geometric patterns based on hand positions
* **Performance Metrics:** Real-time FPS and latency display

## 🚀 Installation
### Prerequisites
* Node.js 14.0 or higher
* Modern web browser with camera access
* Git (for cloning the repository)

### Setup
1. Clone the repository
   ```bash
   git clone https://github.com/Deepsicaa/HandConnect.git
   cd HandConnect
   ```
2. Start the server
   ```bash
   node server.js
   ```
3. Open your browser and navigate to http://localhost:8000

## 🎮 Usage
### Getting Started
* Grant camera permissions when prompted by your browser
* Click "Enter Experience" to start the AR experience
* Use your hands to interact with the visual effects

### Gestures
* **Pinch:** Thumb and index finger together to create shockwaves with sound
* **Open Hand:** Spread fingers wide to see the spread percentage
* **Fist:** Make a fist to change the gesture detection

### Themes
Click on the theme buttons at the bottom of the screen to change the visual style:
* **Rainbow:** Dynamic rainbow colors
* **Cyberpunk:** Neon pink and cyan
* **Lava:** Fiery red and orange
* **Ocean:** Calming blue and teal
* **Galaxy:** Deep purple and blue

## 🛠️ Project Structure
```
HandConnect/
├── index.html          # Main application file
├── server.js           # Node.js server
└── README.md           # This documentation
```

## 📱 Browser Support
* Chrome (latest)
* Firefox (latest)
* Safari (latest)
* Edge (latest)

## 🔒 Permissions
The application requires the following permissions:
* **Camera:** For hand tracking
* **Audio:** For sound effects

## ⚡ Performance Optimization
### For Users
* Close other browser tabs and applications for best performance
* Use a well-lit environment for better hand detection
* Ensure your webcam is positioned correctly

### For Developers
* The application uses `requestAnimationFrame` for smooth animations
* Canvas rendering is optimized with proper clearing and compositing
* Audio processing is lightweight and only active when needed

## 🎨 Customization
### Adding New Themes
1. Open `index.html`
2. Add a new theme to the `themes` object in the JavaScript section
3. Add a new button to the themes section in the HTML

#### Example Theme
```javascript
'NewTheme': (t, index, total) => `hsl(${120 + index * 30}, 70%, 60%)`
```

## 🤝 Contribution Guidelines
Contributions are welcome! Please follow these steps:
1. Fork the repository
2. Clone your fork
3. Create a new branch for your feature or bug fix
4. Make your changes
5. Commit your changes with a clear commit message
6. Push to your fork
7. Create a pull request

### Code Style Guidelines
* Follow existing code style and naming conventions
* Add comments for new features
* Test changes on multiple devices
* Update documentation as needed

## 📄 License
This project is licensed under the MIT License - see the LICENSE file for details.

## 🎓 Acknowledgments
* **MediaPipe:** For the hand tracking technology
* **Google Fonts:** For the Inter font family
* **CDNJS:** For hosting the MediaPipe libraries

## 📞 Contact
Project Maintainer: Deepsicaa

GitHub: [Deepsicaa](https://github.com/Deepsicaa)

For questions, issues, or feature requests, please open an issue on the GitHub repository.

---
**HandConnect** - Experience the future of hand-tracking AR!

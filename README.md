
## ✨ Features

### 🎥 Real-Time Processing
- ✅ **Live Camera Feed** – WebRTC camera capture with permission handling
- ✅ **5 Processing Modes**:
  - Raw feed passthrough
  - Grayscale conversion
  - Canny edge detection (full 4-stage algorithm)
  - Sobel operator (gradient-based detection)
  - Binary threshold processing
- ✅ **15-30 FPS Performance** – Optimized for smooth real-time processing

### 🎨 Shader Effects & Rendering
- ✅ **WebGL Texture Rendering** – Hardware-accelerated display
- ✅ **Live Shader Effects**:
  - None (raw output)
  - Invert colors
  - Sepia tone
  - Brightness adjustment (-100 to +100)
  - Contrast adjustment (-100 to +100)
- ✅ **Smooth Transitions** – 0.2s fade between effects

### 📊 Analytics & Monitoring
- ✅ **FPS Counter** – Real-time frame rate (color-coded)
- ✅ **Performance Metrics** – Processing time per frame
- ✅ **Resolution Display** – Live camera resolution
- ✅ **Timestamp Tracking** – Frame capture time logging

### 🎮 Interactive Controls
- ✅ **Processing Mode Toggle** – Switch algorithms in real-time
- ✅ **Adjustable Parameters**:
  - Canny thresholds (low/high)
  - Sobel threshold
  - Brightness & contrast sliders
- ✅ **Play/Pause Processing** – Control frame capture
- ✅ **Start/Stop Camera** – Full camera control

### 🌓 Design & UX
- ✅ **Dark/Light Theme** – Accessible theme switching
- ✅ **Responsive Layout** – Desktop, tablet, mobile support
- ✅ **Technical Aesthetic** – Developer-friendly UI
- ✅ **Keyboard Navigation** – Fully accessible controls

### 🚀 Backend & API
- ✅ **Express.js Server** – Efficient Node.js backend
- ✅ **WebSocket Support** – Optional frame streaming
- ✅ **REST API Endpoints** – Frame management endpoints
- ✅ **CORS Enabled** – Cross-origin support

---

## 🛠 Technology Stack

| Layer | Technology |
|-------|-----------|
| **Frontend Framework** | React 18+ with TypeScript |
| **Build Tool** | Vite |
| **Styling** | Tailwind CSS + PostCSS |
| **Graphics** | WebGL 1.0 + GLSL shaders |
| **UI Components** | Radix UI + shadcn/ui |
| **Backend** | Express.js (Node.js) |
| **ORM** | Drizzle ORM |
| **State** | React Hooks |
| **Language** | TypeScript (strict mode) |

---

## 📁 Project Structure

```
flam-assignment-submission-main/
├── client/                              # Frontend application
│   ├── index.html                       # Entry HTML
│   └── src/
│       ├── App.tsx                      # Root component
│       ├── main.tsx                     # React entry
│       ├── index.css                    # Global styles
│       ├── components/
│       │   ├── ControlPanel.tsx         # Processing controls
│       │   ├── StatsOverlay.tsx         # FPS & metrics
│       │   ├── CameraPermissionModal.tsx
│       │   ├── ThemeToggle.tsx
│       │   └── ui/                      # Radix UI components
│       ├── lib/
│       │   ├── camera.ts                # WebRTC capture
│       │   ├── imageProcessing.ts       # Algorithms (Canny, Sobel)
│       │   ├── webglRenderer.ts         # WebGL rendering
│       │   └── utils.ts
│       ├── pages/
│       │   └── ComputerVision.tsx       # Main page
│       └── hooks/
│           └── use-toast.ts
│
├── server/                              # Backend
│   ├── index.ts                         # Express setup
│   ├── routes.ts                        # API endpoints
│   ├── storage.ts                       # Data persistence
│   └── vite.ts                          # Vite integration
│
├── shared/                              # Shared types
│   └── schema.ts                        # TypeScript interfaces
│
├── Configuration
│   ├── package.json
│   ├── tsconfig.json
│   ├── vite.config.ts
│   ├── tailwind.config.ts
│   ├── postcss.config.js
│   ├── drizzle.config.ts
│   └── components.json
│
└── Documentation
    ├── README.md (this file)
    ├── design_guidelines.md
    └── replit.md
```

---

## 🚀 Installation & Setup

### Prerequisites
- **Node.js** 16+ (18+ recommended)
- **npm** 8+ or **yarn**
- Modern browser with WebGL support
- Camera device (laptop/desktop with webcam)

### Step 1: Clone Repository
```bash
git clone https://github.com/yourusername/flam-assignment-submission-main.git
cd flam-assignment-submission-main
```

### Step 2: Install Dependencies
```bash
npm install
```

### Step 3: Start Development Server
```bash
npm run dev
```

The application will open at:
- **Frontend**: http://localhost:5173
- **Backend API**: http://localhost:5000/api

### Step 4: Grant Camera Permission
When prompted by your browser, click **Allow** to enable camera access.

### Step 5: Start Processing
Click **"Start Camera"** button to begin real-time processing.

---

## 💻 Usage Guide

### Basic Workflow

1. **Enable Camera**
   ```
   Click "Start Camera" → Browser requests permission → Camera feed displays
   ```

2. **Select Processing Mode**
   - Raw Feed – No processing
   - Grayscale – Color → Grayscale conversion
   - Edge Detection – Canny algorithm (recommended)
   - Sobel – Gradient-based edges
   - Threshold – Binary image generation

3. **Adjust Parameters** (appears based on mode)
   - **Canny**: Low/High threshold sliders
   - **Sobel**: Edge threshold slider
   - **Threshold**: Binary threshold value

4. **Apply Shader Effects**
   - Select effect from dropdown
   - Adjust intensity with sliders
   - Real-time visual updates

5. **Monitor Performance**
   - FPS counter (top-left overlay)
   - Processing time per frame
   - Frame resolution
   - Timestamp

6. **Control Playback**
   - **Pause** – Freeze current frame
   - **Resume** – Continue processing
   - **Stop** – End capture and close camera

### Keyboard Shortcuts
| Key | Action |
|-----|--------|
| `B` | Toggle sidebar visibility |
| `Space` | Play/Pause processing |

---

## 🏗 Architecture

### Data Flow
```
┌─────────────────┐
│  Camera Input   │ WebRTC MediaStream
└────────┬────────┘
         │
    ┌────▼────────────────────┐
    │ Frame Extraction        │ camera.ts
    │ (Video → Canvas)        │
    └────┬───────────────────┘
         │
    ┌────▼────────────────────┐
    │ Image Processing        │ imageProcessing.ts
    │ • Grayscale             │
    │ • Canny Detection       │
    │ • Sobel Operator        │
    │ • Threshold             │
    └────┬───────────────────┘
         │
    ┌────▼────────────────────┐
    │ WebGL Rendering         │ webglRenderer.ts
    │ • Texture Upload        │
    │ • Shader Application    │
    │ • Effect Blending       │
    └────┬───────────────────┘
         │
    ┌────▼────────────────────┐
    │ Canvas Display          │
    │ + Stats Overlay         │
    └────────────────────────┘
```

### Key Modules

#### [`client/src/lib/camera.ts`](client/src/lib/camera.ts)
**WebRTC Camera Management** – Equivalent to Android Camera2 API
- Permission request handling
- Video stream capture
- Frame extraction from video element
- Error handling and fallbacks

#### [`client/src/lib/imageProcessing.ts`](client/src/lib/imageProcessing.ts)
**Image Processing Algorithms** – OpenCV-equivalent implementations
```typescript
// Canny Edge Detection (4-stage)
1. Gaussian Blur – Noise reduction
2. Sobel Operator – Gradient calculation
3. Non-Maximum Suppression – Thinning edges
4. Double Threshold + Hysteresis – Final edge map

// Sobel Operator – Gradient-based detection
// Grayscale – Color space transformation
// Threshold – Binary image generation
```

#### [`client/src/lib/webglRenderer.ts`](client/src/lib/webglRenderer.ts)
**WebGL Rendering Engine** – Hardware-accelerated display
- WebGL 1.0 context management
- Texture pooling and reuse
- GLSL shader compilation and linking
- Real-time parameter updates
- Frame rate monitoring

#### [`client/src/components/ControlPanel.tsx`](client/src/components/ControlPanel.tsx)
**Interactive Control Interface**
- Processing mode selection
- Algorithm parameter adjustment
- Shader effect controls
- Real-time parameter binding

#### [`client/src/components/StatsOverlay.tsx`](client/src/components/StatsOverlay.tsx)
**Performance Monitoring**
- FPS counter (color-coded: green >30, yellow 15-30, red <15)
- Resolution display
- Processing time tracking
- Frame timestamp logging

#### [`server/index.ts`](server/index.ts) & [`server/routes.ts`](server/routes.ts)
**Express Backend**
- RESTful API endpoints
- WebSocket server for frame streaming
- Request logging and monitoring
- CORS and middleware setup

---

## ⚡ Performance Metrics

| Metric | Target | Status |
|--------|--------|--------|
| **Frame Rate** | 15-30 FPS | ✅ Achieved |
| **Processing Time** | <33ms/frame | ✅ <33ms avg |
| **Max Resolution** | 1280x720 | ✅ Supported |
| **Browser Support** | WebGL 1.0+ | ✅ Modern browsers |
| **Theme Switch** | <100ms | ✅ Instant |

### Optimization Techniques
- Canvas rendering via `requestAnimationFrame`
- WebGL texture pooling and reuse
- Optimized shader compilation
- Minimal DOM updates during processing
- Efficient ImageData creation and reuse

---

## 🎨 Design System

### Color Palette (Dark Mode - Primary)

```
Background Base:      #1a1f26 (hsl 220 15% 12%)
Background Elevated:  #272d35 (hsl 220 15% 16%)
Interactive:          #323a44 (hsl 220 15% 20%)
Primary Accent:       #5eead4 (Emerald - active states)
Text Primary:         #f2f2f7 (hsl 220 10% 95%)
Text Secondary:       #a6a9b3 (hsl 220 10% 65%)
Border:               #404856 (hsl 220 15% 25%)
Error/Warning:        #f85454 (hsl 0 84% 60%)
```

### Typography
- **Technical Data**: JetBrains Mono (monospace)
- **UI Labels**: System font stack
- **Headings**: High contrast for hierarchy

### Components
- **Glass-morphism**: backdrop-blur-xl for floating elements
- **Shadows**: Minimal, functional shadows only
- **Spacing**: Tailwind-based (4, 8, 12, 16 units)
- **Animations**: Purposeful 0.15-0.3s ease transitions

See [design_guidelines.md](design_guidelines.md) for detailed specifications.

---

## 🔌 API Reference

### REST Endpoints

#### `GET /api/stats`
Returns server statistics.
```json
{
  "uptime": 3600000,
  "framesProcessed": 1250,
  "avgProcessingTime": 28.5
}
```

#### `POST /api/frames/save`
Save processed frame.
```json
{
  "imageData": "base64-encoded-string",
  "metadata": {
    "resolution": "1280x720",
    "processingMode": "edge_detection",
    "timestamp": 1234567890
  }
}
```

### WebSocket Events

#### `frame:processed`
Emitted when frame processing completes.
```javascript
socket.on('frame:processed', (frameData) => {
  console.log('Frame ready:', frameData);
});
```

---

## 🧪 Development

### Build for Production
```bash
npm run build
```
Output directory: `dist/public/`

### Type Checking
```bash
npm run check
```

### Development Server with Hot Reload
```bash
npm run dev
```

### Code Quality

The project uses:
- ✅ **TypeScript strict mode** – Full type safety
- ✅ **Functional components** – React best practices
- ✅ **React Hooks** – Modern state management
- ✅ **Error boundaries** – Graceful error handling
- ✅ **Ref management** – Canvas/video element access

### File Naming Conventions
- **Components**: PascalCase (e.g., `ControlPanel.tsx`)
- **Utilities**: camelCase (e.g., `imageProcessing.ts`)
- **Types/Interfaces**: PascalCase (e.g., `ProcessingParams`)

---

## 📦 Deployment

### Ready for Production ✅

All MVP features complete and thoroughly tested.

**Deployment Checklist**:
- ✅ Camera capture with permission handling
- ✅ Real-time image processing (5 modes)
- ✅ WebGL rendering with shader effects
- ✅ Live statistics and FPS monitoring
- ✅ Interactive controls with parameter adjustment
- ✅ WebSocket streaming infrastructure
- ✅ API endpoints for frame management
- ✅ Architecture review passed
- ✅ Performance targets met

### Deploy to Production

```bash
# Build
npm run build

# Run production server
npm start

# Or deploy to cloud platforms:
# Vercel, Netlify, AWS, Heroku, DigitalOcean, etc.
```

### Environment Variables
Create `.env` if needed:
```env
VITE_API_URL=http://localhost:5000
NODE_ENV=production
```

---

## 🔧 Troubleshooting

### Camera Not Accessible
**Error**: "Camera permission denied"

**Solution**:
1. Check browser permissions for camera
2. Ensure device has camera hardware
3. Use HTTPS (required for camera access in production)
4. Try different browser (Chrome recommended for WebGL)
5. Check camera isn't in use by another application

### Low Frame Rate
**Error**: FPS counter shows <15 FPS

**Solution**:
1. Reduce canvas resolution
2. Switch to grayscale mode (fastest)
3. Close other browser tabs
4. Check GPU drivers are updated
5. Try a different browser
6. Monitor CPU/GPU usage in DevTools

### WebGL Not Supported
**Error**: "WebGL not available"

**Solution**:
1. Update browser to latest version
2. Check GPU drivers
3. Enable WebGL in browser settings
4. Try incognito/private browsing mode
5. Use Chrome (most reliable WebGL support)

### Shader Compilation Errors
**Error**: "Shader compilation failed"

**Solution**:
1. Check browser console for detailed errors
2. Verify GLSL syntax in shader source
3. Ensure WebGL1 compatibility (no WebGL2 features)
4. Test with simpler shader first
5. Check GPU vendor compatibility

---

## 🤝 Contributing

### Development Workflow
1. Create feature branch: `git checkout -b feature/your-feature`
2. Make changes with clear commits
3. Test thoroughly (FPS, performance, UI)
4. Submit pull request with description

### Commit Message Format
```
type(scope): brief description

- More detailed explanation if needed
- Focus on what changed and why
```

**Examples**:
```
feat(camera): add permission request modal
fix(webgl): resolve shader compilation on Firefox
perf(renderer): optimize texture upload pooling
docs(readme): add API reference section
```

### Testing Checklist
- [ ] Frame rate stable (15-30 FPS)
- [ ] All processing modes functional
- [ ] Shader effects apply correctly
- [ ] Camera permission flow works
- [ ] Mobile responsive layout
- [ ] Dark/light theme toggle works
- [ ] No console errors

---

## 📄 License

MIT License – See LICENSE file for details

This project is a technical demonstration. See [attached_assets/](attached_assets/) for original assessment requirements.

---



---

## 🙏 Acknowledgments

Built as a technical assessment demonstrating:
- Real-time image processing
- WebGL graphics programming
- Modern React patterns
- TypeScript best practices
- Full-stack JavaScript architecture




Made with ❤️ by Pranabh Dubey

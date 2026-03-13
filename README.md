# Cut - Browser-Based Video Editor

A fully functional, production-ready browser-based video editing application built entirely with client-side technologies. Zero backend required - all processing happens in your browser!

## ✨ Features

- 🎬 **Video Editing**: Import, trim, split, and arrange video clips
- 🎵 **Audio Support**: Visual waveform display for audio tracks
- 💬 **Text Layers**: Add and customize text overlays
- 🎨 **Fill Layers**: Create solid color backgrounds
- ⌨️ **Keyboard Shortcuts**: Professional editor shortcuts for faster workflow
- 💾 **Auto-Save**: Automatic project saving to IndexedDB
- 🎯 **Timeline Editing**: Drag-and-drop clips with snap-to-grid
- 🔍 **Zoom Controls**: Adjustable timeline zoom for precision editing
- ▶️ **Real-time Preview**: Canvas-based video playback engine

## 🛠 Tech Stack

- **React + TypeScript** - UI framework
- **Tailwind CSS** - Styling with dark theme
- **Zustand + Immer** - Global state management with undo/redo
- **IndexedDB (idb)** - Client-side project persistence
- **Lucide React** - Icons
- **Web APIs**: WebCodecs, Web Audio API, Canvas API

## 🚀 Getting Started

### Prerequisites

- Node.js 18+ 
- pnpm (recommended) or npm

### Installation

```bash
# Install dependencies
pnpm install

# Start development server
pnpm dev

# Build for production
pnpm build
```

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Space` | Play/Pause |
| `←/→` | Step 1 frame backward/forward |
| `Shift + ←/→` | Step 1 second backward/forward |
| `\` | Go to start |
| `S` | Split clip at playhead |
| `T` | Add text track |
| `Delete/Backspace` | Delete selected clip |
| `Cmd/Ctrl + Z` | Undo |
| `Cmd/Ctrl + Shift + Z` | Redo |
| `Cmd/Ctrl + I` | Import files |
| `+/-` | Zoom in/out timeline |
| `G` | Toggle snap to grid |
| `K` | Add keyframe |

## 📁 Project Structure

```
src/
├── app/
│   ├── components/
│   │   ├── Toolbar.tsx          # Top toolbar with controls
│   │   ├── CanvasPreview.tsx    # Video preview canvas
│   │   ├── Inspector.tsx        # Property inspector panel
│   │   ├── Timeline.tsx         # Timeline container
│   │   ├── TrackRow.tsx         # Individual track
│   │   └── ClipBlock.tsx        # Timeline clip block
│   ├── hooks/
│   │   ├── useKeyboardShortcuts.ts
│   │   ├── usePlayback.ts       # RAF playback engine
│   │   └── useAutoSave.ts       # IndexedDB auto-save
│   ├── store/
│   │   └── useProjectStore.ts   # Zustand store
│   └── App.tsx
└── styles/
    ├── fonts.css
    └── theme.css
```

## 🎯 Features Roadmap

- [x] Basic timeline editing
- [x] Video/audio import
- [x] Text layers
- [x] Real-time preview
- [x] Keyboard shortcuts
- [x] Auto-save
- [ ] FFmpeg export
- [ ] Effects & transitions
- [ ] Advanced keyframe animation
- [ ] Multi-track audio mixing
- [ ] Color grading

## 📝 License

MIT

## 🙏 Acknowledgments

Built with ❤️ using modern web technologies. No servers required!
# Cut Video Editor - Architecture

## Overview

Cut is a browser-based video editor built entirely with client-side technologies. All video processing, rendering, and state management happens in the browser - no backend required.

## Core Components

### 1. State Management (Zustand + Immer)

**Location:** `src/app/store/useProjectStore.ts`

The entire application state is managed through a single Zustand store with Immer middleware for immutable updates.

**Key State:**
- `tracks[]` - Timeline tracks (video, audio, text, fill)
- `clips{}` - All clips indexed by ID
- `currentTime` - Playhead position
- `playing` - Playback state
- `zoom` - Timeline zoom level
- `selectedClipId` - Currently selected clip

**Key Actions:**
- `importClip()` - Process and add media files
- `splitClipAtPlayhead()` - Split clips
- `trimClip()` - Trim in/out points
- `moveClip()` - Reposition clips
- `deleteClip()` - Remove clips

### 2. Playback Engine

**Location:** `src/app/hooks/usePlayback.ts`

Uses `requestAnimationFrame` for smooth playback:
1. Advances playhead based on elapsed time
2. Determines active clips at current time
3. Renders video frames to canvas
4. Composites text and fill layers
5. Handles blend modes and opacity

**Video Synchronization:**
```typescript
if (Math.abs(videoElement.currentTime - sourceTime) > 0.1) {
  videoElement.currentTime = sourceTime;
}
```

### 3. Timeline UI

**Components:**
- `Timeline.tsx` - Container with ruler and controls
- `TrackRow.tsx` - Individual track with header
- `ClipBlock.tsx` - Draggable/resizable clip representation

**Interactions:**
- Drag clips to move
- Drag edges to trim
- Click to select
- Double-click for in-place editing

### 4. Canvas Preview

**Location:** `src/app/components/CanvasPreview.tsx`

1920x1080 canvas that composites all layers:
1. Fill layers (solid colors)
2. Video clips (via `<video>` elements)
3. Text overlays (canvas text rendering)

Blend modes and opacity applied per-clip.

### 5. Auto-Save System

**Location:** `src/app/hooks/useAutoSave.ts`

Persists project state to IndexedDB:
- Debounced saves (5 second delay)
- Serializes tracks and clips
- Excludes non-serializable data (File, VideoElement)
- Restores on app load

### 6. Media Processing

**Video Files:**
1. Create `<video>` element with `createObjectURL`
2. Wait for `loadedmetadata` event
3. Extract duration, dimensions
4. Generate thumbnails via canvas
5. Store video element reference

**Audio Files:**
1. Read file as ArrayBuffer
2. Decode with Web Audio API
3. Downsample waveform to ~1000 points
4. Store for visualization

## Data Flow

```
User Action
    ↓
Component Event Handler
    ↓
Zustand Action
    ↓
Immer State Update
    ↓
Component Re-render
    ↓
Canvas Re-draw (if playing)
```

## Key Design Decisions

### Why No Backend?
- Instant local editing
- No upload delays
- Privacy (files never leave device)
- Simplified deployment

### Why Zustand + Immer?
- Simple, minimal boilerplate
- Immutable updates without complexity
- Easy undo/redo foundation
- Great TypeScript support

### Why Canvas Instead of DOM?
- Precise pixel-level control
- Hardware-accelerated rendering
- Consistent cross-browser output
- Easy export to video

### Why IndexedDB?
- Large storage capacity
- Async, non-blocking
- Structured data support
- Good browser support

## Performance Considerations

**Optimizations:**
- RAF for 60fps playback
- Thumbnail caching
- Lazy waveform generation
- Virtual scrolling (future)

**Limitations:**
- Large files (>2GB) may crash
- Limited by browser memory
- Single-threaded processing

**Future Improvements:**
- Web Workers for processing
- Streaming playback
- Progressive thumbnail loading

## Browser API Usage

- **Canvas API** - Video compositing
- **Web Audio API** - Audio decoding, waveforms
- **IndexedDB** - Project persistence
- **File API** - Media import
- **createObjectURL** - Video playback
- **requestAnimationFrame** - Smooth playback

## Export Architecture (Future)

Planned approach:
1. Use FFmpeg.wasm for encoding
2. Render each frame to canvas
3. Extract frame data as ImageData
4. Feed to FFmpeg encoder
5. Generate MP4/WebM output
6. Download via Blob URL

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

Built with ❤️ by the open-source community.
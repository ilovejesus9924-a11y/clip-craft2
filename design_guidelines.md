# Design Guidelines: Free Video Editor Web App

## Design Approach
**Reference-Based Approach:** Drawing inspiration from modern video editing platforms (CapCut, Adobe Premiere Rush, DaVinci Resolve) with emphasis on professional-grade UX in a browser-based environment. Focus on clarity, efficiency, and intuitive workflows for both beginners and experienced editors.

## Core Design Principles
- **Dark-first interface:** Standard for video editing to reduce eye strain and make video content pop
- **Spatial organization:** Clear zones for preview, timeline, tools, and assets
- **Immediate feedback:** Real-time visual updates for all editing actions
- **Progressive disclosure:** Advanced features accessible but not overwhelming

## Typography
- **Primary Font:** Inter or SF Pro Display (via Google Fonts CDN)
- **Monospace Font:** JetBrains Mono for timecode displays
- **Hierarchy:**
  - App title/branding: 18px, semibold
  - Section headers: 14px, medium
  - Button labels: 13px, medium
  - Timeline markers/timecodes: 11px, regular
  - Helper text: 12px, regular

## Layout System
**Spacing primitives:** Use Tailwind units of 2, 4, 6, and 8 for consistent rhythm (p-2, gap-4, h-6, m-8)

**Application Structure:**
- **Top Bar (h-14):** Logo, project name, export button (fixed position)
- **Main Workspace (flex-1):** 
  - Left sidebar (w-64): Asset library, effects panel (toggleable)
  - Center area (flex-1): Video preview window with aspect ratio controls
  - Right sidebar (w-72): Properties panel for selected clips/effects
- **Bottom Timeline (h-64):** Horizontal scrolling timeline with zoom controls

## Component Library

### Navigation & Controls
- **Top toolbar:** Icon buttons with tooltips (Import, Undo, Redo, Export)
- **Zoom slider:** For timeline granularity (hours to frames)
- **Playback controls:** Play/pause, skip forward/back, scrubber

### Asset Management
- **Upload zone:** Drag-and-drop area with prominent "Import Media" button
- **Asset thumbnails:** Grid layout (grid-cols-2 gap-2) with duration badges
- **Format indicators:** Small icons showing file type (MP4, MOV, etc.)

### Video Preview
- **Preview canvas:** Centered with letterboxing, responsive aspect ratio
- **Aspect ratio buttons:** Pill-style toggle group (9:16, 1:1, 16:9, 4:5)
- **Preview overlay:** Timecode display, safe area guides (toggleable)

### Timeline Components
- **Track layers:** Stacked horizontal lanes (h-12 each) for video/audio
- **Clip cards:** Rounded rectangles with thumbnail previews, trim handles at edges
- **Playhead:** Vertical line (w-0.5) with draggable handle at top
- **Ruler:** Time markers every 1/5/10 seconds based on zoom level

### Effects & Tools Panel
- **Category tabs:** Horizontal tab bar (Filters, Adjust, Text, Transitions)
- **Effect thumbnails:** 2-column grid with preview images
- **Adjustment sliders:** Full-width with numerical input fields
- **Apply button:** Primary action at bottom of panel

### Properties Panel
- **Accordion sections:** Collapsible groups (Transform, Color, Audio)
- **Parameter controls:** Mix of sliders, number inputs, color pickers
- **Keyframe timeline:** Mini timeline for animation controls

### Export Modal
- **Quality presets:** Large cards for 1080p, 720p, 480p
- **Advanced settings:** Collapsible section (codec, bitrate, format)
- **Progress bar:** During export with percentage and estimated time
- **Download button:** Appears when complete

## Icons
Use **Heroicons** (outline style) via CDN for consistency:
- Toolbar: DocumentPlusIcon, ArrowUturnLeftIcon, ArrowDownTrayIcon
- Playback: PlayIcon, PauseIcon, ForwardIcon, BackwardIcon
- Effects: SparklesIcon, AdjustmentsHorizontalIcon, PhotoIcon
- Tools: ScissorsIcon, PlusIcon, TrashIcon

## Animations
**Minimal and purposeful:**
- Timeline scrubbing: Smooth 60fps playback
- Panel toggles: 200ms ease-in-out slide
- Drag-and-drop: Subtle elevation change
- Loading states: Spinner or skeleton screens for video processing

## Accessibility
- Keyboard shortcuts for all major actions (Space = play/pause, I/O = in/out points, Delete = remove clip)
- Focus indicators on all interactive elements
- ARIA labels for icon-only buttons
- Timecode readable by screen readers

## Images
**No hero image needed** - this is a utility application launching directly into the editor interface. The video preview canvas serves as the primary visual focus area.

## Key Layout Decisions
- Single-page application with persistent UI (no page transitions)
- Resizable panels with drag handles between major sections
- Timeline takes precedence at bottom (always visible, never collapsed)
- Modal overlays for export, settings, and help documentation
- No traditional footer - export actions integrated into top bar
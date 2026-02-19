# Code Editor with Advanced Keyboard Event Handling

A high-performance browser-based code editor that handles complex VS Code-style keyboard shortcuts and input scenarios.

## Features

- **Keyboard Shortcuts**: Ctrl+S (Save), Ctrl+Z (Undo), Ctrl+Shift+Z (Redo), Tab/Shift+Tab (Indent/Outdent), Ctrl+/ (Comment), Ctrl+K, Ctrl+C (Chord)
- **Event Dashboard**: Real-time logging of keyboard events (keydown, keyup, input, composition)
- **Undo/Redo**: Full history stack management
- **Performance Optimization**: Debounced syntax highlighting
- **Cross-Platform**: Works with both Ctrl (Windows/Linux) and Cmd (Mac) modifiers
- **Accessibility**: Proper ARIA roles and keyboard navigation

## Setup

### Prerequisites
- Node.js 18+
- Docker and Docker Compose (optional)

### Local Development

```bash
npm install
npm start
```

The application will run on `http://localhost:3000`

### Docker

```bash
docker-compose up --build
```

## Project Structure

- `server.js` - Express server that serves the application
- `public/index.html` - Main HTML file with the editor UI
- `package.json` - Project dependencies
- `Dockerfile` - Docker image configuration
- `docker-compose.yml` - Docker Compose configuration
- `.env.example` - Environment variables documentation

## Implementation Details

### Keyboard Events
The editor uses:
- `keydown` event for capturing keyboard shortcuts before they're processed
- `input` event for tracking text changes
- `compositionstart/compositionend` for IME (Input Method Editor) support

### State Management
- Undo/Redo stacks for history management
- Event log array for the debugging dashboard

### Performance
- Debounced syntax highlighting (150ms+)
- Event delegation for efficient event handling

## Verification Functions

The application exposes two global functions for testing:
- `window.getEditorState()` - Returns `{ content: string, historySize: number }`
- `window.getHighlightCallCount()` - Returns the number of times syntax highlighting was executed

## License

MIT

# Claude JSONL History Viewer

A single-file web application for browsing Claude Code conversation histories. This application provides a visual interface for exploring Claude AI conversations, including user messages, assistant responses, tool calls, and metadata.

> [中文文档](README_CN.md) | English Documentation

## Features

### 🎯 Core Features
- **Single-file application**: No build process required, open HTML file directly in browser, no external CSS dependencies
- **File system access**: Uses modern browser File System Access API to read local directories and JSONL files
- **Multi-language support**: Complete Chinese/English interface switching

### 📊 Data Parsing
- **JSONL format support**: Parses standard Claude conversation JSONL format
- **Session grouping**: Automatically groups conversation sessions by sessionId
- **Message type recognition**: Supports user, assistant, system, summary, and other message types
- **Tool call visualization**: Special handling for common tools (TodoWrite, Edit, MultiEdit, etc.)

### 🎨 Interface Features
- **File tree navigation**: Collapsible project structure browsing
- **Message color coding**: Different colors for different message types
- **Syntax highlighting**: JSON data syntax highlighting
- **Text comparison**: Text diff comparison for Edit/MultiEdit tools
- **Todo rendering**: Visual display for TodoWrite tool

## Quick Start

### Usage
1. **Open application**: Download to local and open `claude-code-history-viewer.html` directly in browser
2. **Select directory**: Click "Select" button to choose project folder containing Claude JSONL files
3. **Browse conversations**: Click JSONL files in left file tree to view conversation details

### Interface Preview

![Application Interface Screenshot](sample.png)

### Browser Requirements
- **Chrome 86+** or **Edge 86+** (recommended)
- Requires File System Access API support
- Not supported: Safari and Firefox (limited API support)

## Architecture Design

### Component Architecture
- **ClaudeCodeHistoryApp**: Main application container managing layout and state
- **DataManager**: Central data management with IndexedDB persistence
- **StyleManager**: Centralized style management with embedded Tailwind CSS
- **FileBrowser**: File tree navigation component
- **MessageViewer**: Conversation display component
- **LanguageManager**: Multi-language management component

### Core Functionality
- **Directory traversal**: Recursively scans project directory structure
- **JSONL parsing**: Session grouping and message extraction
- **Content extraction**: Type-specific content processing
- **Tool rendering**: Special tool visualization
- **Data persistence**: Uses IndexedDB to save directory handles

## Technical Features

### Internationalization Support
- Chinese/English translations
- Automatic browser language detection
- Dynamic language switching

### Performance Optimizations
- Asynchronous file preview loading
- Incremental JSONL parsing
- Non-blocking IndexedDB operations
- Embedded CSS avoids external dependencies

### Security Considerations
- HTML content escaping to prevent XSS attacks
- File access permission management
- Data stored locally, no server upload

## Development Guide

### Custom Development
To extend functionality, focus on these components:
- **DataManager**: Add new data parsing logic
- **MessageViewer**: Add new rendering components
- **LanguageManager**: Add new translation texts
- **StyleManager**: Add new style definitions

### Testing Methods
- Open HTML file directly in browser for testing
- Use real Claude JSONL files for validation
- Check browser console for error messages

## License

This project is for learning and research purposes only.

## Contributing

Welcome to submit issues and improvement suggestions!

---

**Note**: This project requires modern browser support. Please ensure using Chrome 86+ or Edge 86+ versions for the best experience.
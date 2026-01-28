# Rich Text Editor - Toolbar Configuration Guide

## Overview

The RTE (Rich Text Editor) now uses a **simplified, modular toolbar system** that makes it easy to customize which tools appear in your editor.

## Default Behavior

By default, the editor shows only **essential tools**:
- **Clipboard**: Undo, Redo
- **Formatting**: Bold, Italic, Underline

This keeps the interface clean and minimal for basic editing needs.

## Customizing the Toolbar

You can easily add more toolbar groups by importing `AVAILABLE_TOOLBAR_GROUPS` and selecting which groups you want:

```javascript
import { RTE } from 'editor-structure/rte-package/src/editor.js'
import { AVAILABLE_TOOLBAR_GROUPS } from 'editor-structure/rte-package/src/config/defaults.js'

// Pick the groups you want
const customToolbar = [
  AVAILABLE_TOOLBAR_GROUPS.clipboard,  // Undo, Redo, Cut, Copy, Paste
  AVAILABLE_TOOLBAR_GROUPS.formatting, // Bold, Italic, Underline, Strikethrough, etc.
  AVAILABLE_TOOLBAR_GROUPS.paragraph,  // Headings, Lists, Blockquote
  AVAILABLE_TOOLBAR_GROUPS.insert,     // Link, Image, Video, Table
  AVAILABLE_TOOLBAR_GROUPS.view        // Source Code, Fullscreen
]

// Apply to your editor
const editor = new RTE(container, {
  toolbar: customToolbar
})
```

## Available Toolbar Groups

### `clipboard`
- Undo, Redo, Cut, Copy, Paste (with options for Word/Plain Text)

### `formatting`
- Bold, Italic, Underline, Strikethrough
- Superscript, Subscript, Inline Code
- Clear Formatting

### `paragraph`
- Heading selector (H1-H6, Paragraph)
- Bullet list styles (disc, circle, square)
- Number list styles (decimal, alpha, roman)
- Blockquote, Horizontal Rule

### `alignment`
- Text alignment (Left, Center, Right, Justify)

### `indent`
- Increase/Decrease indent

### `insert`
- Link, Unlink
- Image, Audio, Video
- Table, Code Block
- Emoji, Special Characters

### `typography`
- Font family selector
- Font size selector
- Text color, Highlight color

### `view`
- Toggle source code view
- Toggle fullscreen mode

## Examples

### Minimal Editor (Default)
```javascript
// No config needed - uses defaults
const editor = new RTE(container, {})
```
Shows: Undo, Redo, Bold, Italic, Underline

### Blog Editor
```javascript
const toolbar = [
  AVAILABLE_TOOLBAR_GROUPS.clipboard,
  AVAILABLE_TOOLBAR_GROUPS.formatting,
  AVAILABLE_TOOLBAR_GROUPS.paragraph,
  AVAILABLE_TOOLBAR_GROUPS.insert
]

const editor = new RTE(container, { toolbar })
```

### Full-Featured Editor
```javascript
const toolbar = Object.values(AVAILABLE_TOOLBAR_GROUPS)

const editor = new RTE(container, { toolbar })
```

## FontAwesome Icons

All toolbar icons use **FontAwesome 5** (Free). Make sure to import FontAwesome CSS:

```javascript
import '@fortawesome/fontawesome-free/css/all.css'
```

## Notes

- Groups are displayed in the order you add them to the array
- You can mix and match any combination of groups
- The toolbar automatically handles overflow for smaller screens
- All icons are semantic and accessible

# HTML Visual Editor

A browser-based visual HTML editor powered by [GrapesJS](https://grapesjs.com/). It is implemented as a standalone page with no frontend build step, making it suitable for local HTML editing, complex table authoring, HTML import, and export.

English | [简体中文](README.zh-CN.md)

## Features

- GrapesJS-powered visual drag-and-drop editing canvas
- Component library with basic, layout, typography, form, navigation, and table components
- Create a blank canvas
- Import HTML files
  - Select a file with the **Import** button
  - Drag `.html` or `.htm` files into the empty editor area
  - Preserve imported CSS, media queries, and responsive styles
- Export a complete HTML document
- Preview pages in a new browser window
- View and copy HTML + CSS
- Undo and redo
- Desktop, tablet, and mobile device preview modes
- Style, layer, trait, and table tool panels
- Empty initial canvas with no sample page
- Empty-state guidance with an HTML file drop zone
- Warn before refreshing or closing the page when there are unexported changes

## Complex Tables

The built-in table tools support:

- Multi-row and multi-column headers
- Row merging with `rowspan`
- Column merging with `colspan`
- Ctrl-click multi-selection of cells
- Merge cells
- Split cells
- Insert and delete rows
- Insert and delete columns
- Rowspan- and colspan-aware grid operations
- Nested tables inside cells

Select a `td` or `th` cell on the canvas, then open the **Table** panel on the right to use these operations.

## Quick Start

### Open Directly

Double-click `index.html` to launch the editor in a browser.

### Run with a Local Static Server

Using a static server is recommended for development and testing. For example, with Python:

```bash
python -m http.server 8080
```

Then open:

```text
http://localhost:8080
```

You can also use VS Code Live Server or any other static file server.

## Basic Usage

### Create a Page

1. Click the component-library button on the right side of the top toolbar.
2. Choose a component from the library.
3. Drag the component onto the canvas.
4. Select the component and edit it through the Style, Layer, or Trait panel.

Selecting a canvas component automatically hides the component library and restores the Style panel.

### Import HTML

HTML can be imported in either of these ways:

- Click **Import** and choose an HTML file.
- Drag an HTML file into the empty editor area.

The importer reads the document body and style elements while preserving the original CSS structure, media queries, and responsive rules as far as possible.

### Export HTML

Click **Export HTML** to download a complete HTML document containing:

- The HTML page structure
- CSS generated through GrapesJS
- Original CSS preserved from an imported document
- Responsive media queries

## Technical Notes

- HTML5
- CSS3
- JavaScript
- GrapesJS
- `FileReader` for reading imported HTML files
- `DOMParser` for parsing HTML documents
- GrapesJS Component API for managing canvas components
- GrapesJS CSS Composer for editable base CSS rules

The project does not require Node.js, npm, or a frontend build pipeline. It can be deployed to any static file server.

## Imported CSS Handling

Passing a complete webpage stylesheet through GrapesJS's CSS parser can change media-query behavior, selector precedence, or layout. The editor therefore uses two complementary paths:

1. The original imported CSS is injected directly into the canvas to preserve the source page's visual appearance.
2. Key base rules are also registered with GrapesJS CSS Composer so their values can be read and edited in the Style panel.

This balances faithful rendering of imported pages with visual editing support.


## License

This project is licensed under the [MIT License](LICENSE).

The bundled GrapesJS files and any third-party resources remain subject to their respective licenses.

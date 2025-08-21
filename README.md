# VEDA Content Editor

A powerful MDX editor component for React applications, built specifically for NASA's VEDA (Visualization, Exploration, and Data Analysis) project. This editor provides rich-text editing capabilities with support for custom components like interactive maps and charts.

## Features

- 📝 **Rich MDX Editing**: Full-featured markdown and MDX editing with live preview
- 🗺️ **Interactive Map Component**: Embed and configure maps with various datasets and layers
- 📊 **Chart Component**: Create and customize data visualizations
- 🎨 **WYSIWYG Interface**: User-friendly interface with toolbar controls
- 📱 **Responsive Design**: Works seamlessly across different screen sizes
- 🔍 **Source Mode**: View generated MDX source (read-only to prevent data loss)
- 🎯 **Custom Components**: Support for NASA VEDA-specific components

## Installation

```bash
npm install veda-content-editor
```

or

```bash
yarn add veda-content-editor
```

## Usage

### Basic Setup

```jsx
import { VEDAContentEditor } from 'veda-content-editor';
import 'veda-content-editor/style.css';

function App() {
  const handleChange = (content) => {
    console.log('Content updated:', content);
  };

  const vedaConfig = {
    envMapboxToken: 'your-mapbox-token',
    envApiStacEndpoint: 'your-stac-endpoint',
    envApiRasterEndpoint: 'your-raster-endpoint',
  };

  return (
    <VEDAContentEditor
      initialContent="# Welcome to VEDA Editor"
      onChange={handleChange}
      vedaConfig={vedaConfig}
    />
  );
}
```

### Full Example with All Props

```jsx
import { VEDAContentEditor } from 'veda-content-editor';
import 'veda-content-editor/style.css';

function App() {
  const initialContent = `
# My Document

This is a **VEDA** content editor with support for:

- Rich text formatting
- Custom components
- Interactive maps
- Data visualizations
  `;

  const datasets = [
    {
      id: 'dataset-1',
      name: 'Sample Dataset',
      layers: [
        { id: 'layer-1', name: 'Layer 1' },
        { id: 'layer-2', name: 'Layer 2' }
      ]
    }
  ];

  const vedaConfig = {
    envMapboxToken: process.env.REACT_APP_MAPBOX_TOKEN,
    envApiStacEndpoint: process.env.REACT_APP_STAC_ENDPOINT,
    envApiRasterEndpoint: process.env.REACT_APP_RASTER_ENDPOINT,
  };

  return (
    <div style={{ width: '100%', height: '100vh' }}>
      <VEDAContentEditor
        initialContent={initialContent}
        onChange={(content) => console.log(content)}
        placeholder="Start typing..."
        className="my-custom-class"
        allAvailableDatasets={datasets}
        vedaConfig={vedaConfig}
      />
    </div>
  );
}
```

## Props

| Prop | Type | Required | Description |
|------|------|----------|-------------|
| `initialContent` | `string` | No | Initial MDX content to display in the editor |
| `onChange` | `(content: string) => void` | No | Callback function triggered when content changes |
| `placeholder` | `string` | No | Placeholder text when editor is empty |
| `className` | `string` | No | Additional CSS classes for the editor container |
| `allAvailableDatasets` | `Array<Dataset>` | No | Available datasets for map components |
| `vedaConfig` | `VedaConfig` | Yes | Configuration object with API endpoints and tokens |

### VedaConfig Object

```typescript
interface VedaConfig {
  envMapboxToken: string;      // Mapbox API token for map rendering
  envApiStacEndpoint: string;  // STAC API endpoint
  envApiRasterEndpoint: string; // Raster API endpoint
}
```

## Custom Components

### Map Component

The editor supports embedding interactive maps with the following features:
- Dataset and layer selection
- Zoom and center controls
- Date/time selection for temporal data
- Comparison mode for viewing changes over time
- Attribution and captions

### Chart Component

Create data visualizations with:
- Line charts
- Time series data
- Custom color schemes
- Axis labels and formatting
- Data highlighting

## Toolbar Features

- **Text Formatting**: Bold, italic, underline, strikethrough
- **Headings**: H1-H6 support
- **Lists**: Ordered and unordered lists
- **Code**: Inline code and code blocks
- **Links**: Create and edit hyperlinks
- **Images**: Insert and manage images
- **Tables**: Create and edit tables
- **Custom Components**: Insert maps and charts via toolbar buttons
- **Source Mode**: View generated MDX (read-only)

## Environment Variables

When using this package, ensure your application provides the following environment variables:

```env
VITE_MAPBOX_TOKEN=your-mapbox-token
VITE_API_STAC_ENDPOINT=your-stac-endpoint
VITE_API_RASTER_ENDPOINT=your-raster-endpoint
```

Or pass them directly through the `vedaConfig` prop.

## Styling

The editor comes with default styles. Import the CSS file:

```jsx
import 'veda-content-editor/style.css';
```

### Full Width Layout

To make the editor take full viewport width and height:

```jsx
<div style={{ width: '100%', height: '100vh' }}>
  <VEDAContentEditor {...props} />
</div>
```

## Known Issues

- **Source Mode**: Currently read-only to prevent loss of custom components when editing raw MDX
- **Custom Components**: Must be inserted using toolbar buttons; manual MDX editing of custom components is not supported

## Development

### Building from Source

```bash
# Clone the repository
git clone https://github.com/ajinkyakulkarni/veda-content-editor.git
cd veda-content-editor

# Install dependencies
npm install

# Build the package
npm run build:lib

# Run in development mode
npm run dev
```

### Testing Locally

To test the package locally in another project:

```bash
# In the veda-content-editor directory
npm link

# In your test project
npm link veda-content-editor
```

## Recent Updates

### Version 0.1.18
- Fixed environment variable loading issues
- Resolved duplicate context provider problems
- Simplified UI by removing unnecessary tabs
- Fixed input styling issues (black textbox problem)
- Fixed React hooks errors when collapsing editors
- Made source view read-only to prevent component loss
- Added full-width support
- Improved overall stability and performance

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

MIT

## Support

For issues and questions, please [open an issue](https://github.com/ajinkyakulkarni/veda-content-editor/issues) on GitHub.

## Credits

Built for NASA's VEDA project by the development team.
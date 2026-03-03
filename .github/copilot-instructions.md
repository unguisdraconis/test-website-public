# Copilot Instructions for test-website-public

## Project Overview
This is a minimal test website demonstrating D3.js v7 bar chart implementation. The entire application is a single `index.html` file containing embedded HTML, CSS, and JavaScript - no build system or external dependencies required.

## Core Architecture
- **Data Format**: Objects with `{ name: string, value: number }` structure
- **Visualization**: D3.js bar chart with scales (bandwidth for X, linear for Y)
- **CDN**: D3.js v7 loaded from `https://d3js.org/d3.v7.min.js` (do not remove or change without testing)
- **Styling**: Minimal CSS with `.bar` fill (steelblue) and hover effect (orange)

## Key Patterns

### Adding D3 Visualizations
- **Scale Setup**: Use `scaleBand()` for categorical axes, `scaleLinear()` for numerical axes
- **SVG Structure**: Configure margins and width/height before appending content groups
- **Data Binding**: Use `.data(array).enter().append()` pattern for D3 selections
- **Example**: See [index.html](index.html#L57-L76) for x/y scale configuration

### Modifying the Chart
- **Dataset Location**: Line 48-53 - update `data` array directly
- **Dimensions**: SVG dimensions at line 28, margins at line 35
- **Axes**: Generated at lines 87-97; customize by modifying axis generators
- **Styling**: CSS classes (`.bar`, `.axis-label`) at lines 19-34

## Deployment
- No build step required - serve `index.html` directly over HTTP/HTTPS
- All resources (D3) are CDN-based; works offline-capable by caching
- Git tracks `.gitattributes` for platform-specific line ending handling

## Common Tasks
- **Add new data series**: Extend data array, add new SVG group with separate scales
- **Change chart type**: Replace `selectAll(".bar").append("rect")` section with new D3 shape methods (e.g., `.append("circle")` for scatter plot)
- **Add interactivity**: Attach `.on("click", callback)` or `.on("mouseover", callback)` to selections

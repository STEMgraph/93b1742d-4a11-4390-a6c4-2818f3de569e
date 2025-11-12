<!---
{
  "id": "93b1742d-4a11-4390-a6c4-2818f3de569e",
  "teaches": "Advanced SVG: Coordinate Systems, Viewports, and Scaling",
  "depends_on": ["293aa994-02be-42eb-8859-f7e21029a875"],
  "author": "Stephan Bökelmann",
  "first_used": "2025-06-04",
  "keywords": ["SVG", "viewport", "coordinate system", "scaling", "markup"]
}
--->

# Advanced SVG: Coordinate Systems, Viewports, and Scaling

> In this exercise you will learn how SVG handles coordinate systems, viewports, and transformations. Furthermore we will explore how the rendering process maps your SVG markup onto the displayed graphics and how to control this mapping for more flexible designs.

## Introduction

Every time an SVG file is rendered, the rendering engine reads the XML markup and converts the defined shapes, paths, and text into visual elements. This process involves interpreting coordinate values, applying transformations, and mapping everything onto the pixel grid of your display. To achieve this, SVG introduces a flexible system of *viewports*, *user coordinate systems*, and *transformation matrices*.

By default, the `width` and `height` attributes of the `<svg>` element define the viewport — the rectangular area into which your drawing is rendered. Inside this viewport, all coordinates are interpreted relative to a user coordinate system that typically starts at the top-left corner `(0,0)` and extends along the x and y axes.

The `viewBox` attribute allows you to decouple the coordinate system from the physical display size. It defines a rectangle in user coordinates that will be mapped to fit the viewport. This mapping can be scaled and shifted, which enables you to work with logical coordinates that are independent of actual screen pixels.

Transformations (like `translate`, `scale`, `rotate`, and `skew`) further modify how individual elements are rendered inside the coordinate space. These transformations are applied via transformation matrices during rendering and allow for powerful composition of complex scenes.

Understanding these mechanisms is crucial when designing scalable graphics, responsive designs, or technical diagrams where precision and scaling behavior matter.

### Further Readings and Other Sources

* [MDN Web Docs: SVG Coordinate Systems](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/viewBox)
* [W3C SVG Specification: Coordinate Systems](https://www.w3.org/TR/SVG2/coords.html)
* [A visual explanation of viewBox on CSS-Tricks](https://css-tricks.com/scale-svg/)
* [SVG Transformations Tutorial (YouTube)](https://www.youtube.com/watch?v=pm2tSxmzJW0)

## Tasks

### Task 1: Using the Default Coordinate System

1. Create a new SVG file:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <svg xmlns="http://www.w3.org/2000/svg" width="400" height="400">
       <rect x="0" y="0" width="400" height="400" fill="lightgray" />
       <circle cx="100" cy="100" r="50" fill="red" />
   </svg>
   ```
2. Save and preview your file. Observe how the circle is positioned directly by absolute coordinates.

### Task 2: Introducing the viewBox Attribute

1. Modify the `<svg>` element to include a viewBox:

   ```xml
   <svg xmlns="http://www.w3.org/2000/svg" width="400" height="400" viewBox="0 0 200 200">
   ```
2. The coordinate system is now scaled so that `(0,0)` to `(200,200)` maps into the `400x400` viewport.
3. Add a new circle to verify scaling:

   ```xml
   <circle cx="150" cy="150" r="30" fill="blue" />
   ```
4. Save and preview. Notice how coordinates are scaled automatically.

### Task 3: Panning and Zooming with viewBox

1. Change the viewBox to zoom into the top-left corner:

   ```xml
   viewBox="0 0 100 100"
   ```
2. Save and preview. The shapes now appear larger because the 100x100 user coordinates are stretched over the 400x400 viewport.
3. Shift the viewBox to pan the visible area:

   ```xml
   viewBox="50 50 100 100"
   ```
4. Save and observe how different parts of the drawing come into view.

### Task 4: Apply Transformations

1. Add a group with a translation transformation:

   ```xml
   <g transform="translate(50, 50)">
       <rect x="0" y="0" width="50" height="50" fill="green" />
   </g>
   ```
2. The rectangle's coordinates are now relative to the translated origin.
3. Combine transformations:

   ```xml
   <g transform="translate(50,50) rotate(45)">
       <rect x="0" y="0" width="50" height="50" fill="purple" />
   </g>
   ```
4. Save and observe both translation and rotation applied together.

### Task 5: Combining Viewport and Transformations

1. Set up the following complete SVG structure:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <svg xmlns="http://www.w3.org/2000/svg" width="400" height="400" viewBox="-100 -100 200 200">
       <rect x="-100" y="-100" width="200" height="200" fill="lightgray" />
       <circle cx="0" cy="0" r="50" fill="orange" />
       <g transform="scale(1.5)">
           <rect x="-20" y="-20" width="40" height="40" fill="red" />
       </g>
   </svg>
   ```
2. Save and observe how the negative coordinates and scaling affect rendering.

## Advice

Mastering SVG's coordinate systems, viewports, and transformations is key to producing flexible, scalable graphics that adapt to different output sizes and resolutions. The combination of `viewBox` and transformations allows you to think logically about your design's geometry while ensuring precise rendering on any device. Practice modifying the viewBox and applying transformations to build an intuitive sense for how these mappings work. With these skills, you are now equipped to design complex layouts, responsive graphics, and precise technical diagrams entirely in SVG markup.

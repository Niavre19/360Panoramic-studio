# Spherical Image Studio — Prototype Ver.

A standalone browser-based spherical image and 360° HDRI environment-map workspace.

> This repository package preserves the supplied source unchanged. `#Spherical-Image NEO.html` is copied byte-for-byte to `index.html`.

## Workspaces

This version contains two primary workspaces:

1. **Spherical Projection**
2. **360 Panoramic**

It predates the separate `2D → HDRI Editor` workspace found in the later NEO v2 source.

---

## 1. Spherical Projection

### Input

Supported bitmap formats:

- PNG
- JPG / JPEG
- WebP
- BMP
- GIF

### UV Mapping

UV fit modes:

- Cover UV
- Stretch to full UV
- Contain inside UV

Controls include:

- scale
- horizontal stretch
- vertical stretch
- horizontal offset
- vertical offset
- UV rotation
- seam blending
- seam blend width
- Reset UV
- Center Image
- Original Size

### Sphere & Scene

- sphere base color
- scene background
- roughness
- light strength
- No Light
- auto rotation
- UV grid
- Mercator grid
- grid thickness / color
- orbit reset

### Preview Modes

- Interactive Sphere Preview
- Mercator Projection
- Equal Projection
- 2D UV Map Preview

The UV layout is equirectangular.

### Native WebGL

The 3D renderer is implemented directly in WebGL.

The source explicitly identifies it as:

```text
Native WebGL engine: no external library
```

There is no Three.js/CDN dependency for the sphere renderer.

### Tab 1 Export

Formats:

- PNG
- JPG
- WebP

Resolution:

```text
600–3000 px width
600–3000 px height
```

The current orbit frame becomes the sphere-frame export.

---

## 2. 360 Panoramic

An equirectangular 360° × 180° HDRI processing pipeline.

### Input

Bitmap:

- PNG
- JPG/JPEG
- WebP
- BMP
- GIF

HDR:

- Radiance `.hdr`
- OpenEXR `.exr`

A 2:1 equirectangular source is recommended.

### Radiance HDR Import

Supported Radiance data includes:

- RGBE
- XYZE
- modern RLE
- legacy/raw scanlines

### OpenEXR Import

The supplied offline codec supports implemented OpenEXR v2 image layouts including:

- single-part scanline
- one-level tiled image
- RGB / RGBA / Y
- HALF / FLOAT / UINT
- NONE / ZIP / ZIPS / PIZ compression

### Spherical Geometry

- heading / yaw
- pitch correction
- roll / horizon correction
- Set Horizon Level

### Seam & Poles

- periodic seam correction
- seam width
- color continuity
- luminance continuity
- zenith / nadir repair

### Radiance Controls

- exposure
- white-balance temperature
- tint
- highlight recovery / expansion
- shadow recovery
- estimated headroom

Tone mapping is display-only for HDR/EXR workflows.

### Diagnostics

- normal preview
- luminance false color
- clipping warning
- latitude/longitude grid
- horizon
- compass directions
- seam boundary
- zenith / nadir markers

Diagnostics are never embedded in the HDRI master.

### Views

- Equirectangular
- 360 View
- Lighting Test

### Validation

The app validates items such as:

- 2:1 output
- spherical mapping
- seam continuity
- pole integrity
- HDR source fidelity
- output encoding
- resolution

### Export

Master resolutions:

```text
1024 × 512
2048 × 1024
```

Formats:

- Radiance HDR — linear RGBE
- OpenEXR — linear HALF RGB
- PNG — tone-mapped reference

HDR/EXR generation uses an export-preview step first.

---

## Offline / Local Design

The source reports that this version can run directly from:

```text
file://
```

with no server or CDN dependency for its main processing.

Core features use local browser APIs.

---

## External Resources

The only HTTP/HTTPS URL found in the supplied source is:

```text
https://www.instagram.com/ervinf.dsg
```

No external runtime JavaScript library is required.

---

## Theme

Light/Dark mode is supported.

Theme preference is stored under:

```text
spherePrototypeTheme
```

in `localStorage`.

---

## Browser Requirements

Important browser features:

- WebGL
- Canvas 2D
- File API
- Blob/Object URLs
- typed arrays
- DataView
- TextEncoder/TextDecoder
- DecompressionStream for ZIP/ZIPS EXR import
- requestAnimationFrame
- localStorage
- browser downloads

A modern desktop browser with WebGL enabled is recommended.

---

## Running

Open `index.html` directly, or serve it with:

```bash
python -m http.server 8080
```

No build step is required.

---

## Project Structure

```text
.
├── index.html
├── README.md
└── .gitignore
```

---

## Current Implementation Notes

- Page title: `Spherical Image Studio — Prototype Ver.`
- Two primary workspaces are present.
- Native WebGL replaces an external 3D engine.
- Spherical Projection exports PNG/JPG/WebP.
- Tab 1 export range is 600–3000 px per side.
- 360 Panoramic supports Radiance HDR and OpenEXR.
- 360 master output is exact 2:1.
- 360 master size is limited to 1K or 2K.
- Diagnostic overlays are preview-only.
- Only the creator Instagram link is external.
- Source copyright is preserved.

## License

No additional project-wide license is added by this packaging step.

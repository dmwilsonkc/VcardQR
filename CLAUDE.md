# VcardQR

A client-side web application that converts vCard (.vcf) contact information into scannable QR codes for easy contact sharing.

## Project Overview

- **Type**: Single-file web application (vanilla HTML/CSS/JavaScript)
- **Purpose**: Generate QR codes from vCard data for business cards, banners, and printed materials
- **Privacy**: All processing happens locally in the browser - no data leaves the page

## File Structure

```
VcardQR/
├── index.html    # Complete application (HTML, CSS, JavaScript)
├── LICENSE       # MIT License
└── CLAUDE.md     # This file
```

## Technology Stack

- **Styling**: Tailwind CSS (CDN)
- **QR Code**: QRCode.js v1.0.0 (CDN)
- **No build process** - edit index.html directly

## Key Features

- Multiple input methods: file upload, paste, drag-and-drop, clipboard
- QR encoding options: full vCard, MECARD format, or URL to hosted .vcf
- Customizable QR version and error correction levels
- Export as PNG or SVG
- Form-based vCard builder with full field support

## Development

### Running Locally

Open `index.html` in a browser. No server required for basic testing, though some features (clipboard API) work better with a local server:

```bash
python3 -m http.server 8000
```

### Deployment

Deploy to Firebase Hosting:

```bash
firebase deploy --only hosting:qrproject-macrc
```

Or push to GitHub for GitHub Pages deployment.

## Code Organization

All code is in `index.html`:

- **Lines 1-50**: Head, Tailwind CDN, styles
- **Lines 50-200**: Header and input section (file upload, textarea, tabs)
- **Lines 200-400**: Options panel (encoding mode, QR settings)
- **Lines 400-500**: Output section (QR display, download buttons)
- **Lines 500+**: JavaScript (vCard parsing, MECARD conversion, QR generation)

## Important Functions

- `generateQRCode()` - Main QR generation logic
- `convertToMecard(vcard)` - Converts vCard to compact MECARD format
- `downloadQR(format)` - Exports QR as PNG or SVG
- `loadSampleVCard()` - Loads example vCard for testing

## vCard Format

The app supports vCard 3.0 format. Example:

```
BEGIN:VCARD
VERSION:3.0
FN:John Doe
TEL:+1-555-555-5555
EMAIL:john@example.com
END:VCARD
```

## Notes

- External CDN dependencies: Tailwind CSS, QRCode.js
- Uses modern browser APIs: Clipboard, FileReader, Canvas, Drag/Drop
- Mobile-responsive design with Tailwind

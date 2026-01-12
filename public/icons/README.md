# Icon Generation Instructions

## Quick Icon Setup

You have two options for adding PWA icons:

### Option 1: Use Online Generator (Recommended)

1. Create a 512x512px image with your team logo/branding
2. Go to https://www.pwabuilder.com/imageGenerator
3. Upload your image
4. Download the generated icons
5. Extract and place them in the `public/icons/` folder

### Option 2: Use ImageMagick (Command Line)

If you have ImageMagick installed:

```bash
# From a single source image (source.png)
magick source.png -resize 72x72 icons/icon-72x72.png
magick source.png -resize 96x96 icons/icon-96x96.png
magick source.png -resize 128x128 icons/icon-128x128.png
magick source.png -resize 144x144 icons/icon-144x144.png
magick source.png -resize 152x152 icons/icon-152x152.png
magick source.png -resize 192x192 icons/icon-192x192.png
magick source.png -resize 384x384 icons/icon-384x384.png
magick source.png -resize 512x512 icons/icon-512x512.png
```

## Required Sizes

- 72x72 - Android Chrome minimum
- 96x96 - Android Chrome standard
- 128x128 - Android Chrome large
- 144x144 - Windows tile
- 152x152 - iOS Safari
- 192x192 - Android Chrome standard (recommended)
- 384x384 - Android Chrome high-res
- 512x512 - Android splash screen

## Temporary Placeholder

For now, the app will work without icons, but you'll want to add them before deploying for the best user experience.

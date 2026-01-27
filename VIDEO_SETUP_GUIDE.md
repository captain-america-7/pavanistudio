# Video Setup Guide for Pavani Studios

## Background Video for Hero Section

Your hero section now supports background video! Here's how to add your wedding footage:

### Video Requirements
- **Duration**: 10-15 seconds loop
- **Resolution**: 1920x1080 (Full HD) minimum
- **File Size**: Under 5MB for best performance
- **Format**: MP4 (H.264) + WebM (VP9) for browser compatibility
- **Content**: Cinematic B-roll of wedding moments (slow motion works great!)

### Where to Place Videos
1. Create a `videos` folder in your project root:
   ```
   pavanistudio/
   ├── videos/
   │   ├── hero-wedding.mp4
   │   └── hero-wedding.webm
   ├──images/
   ├── css/
   └── ...
   ```

2. Add your video files:
   - `hero-wedding.mp4` (required)
   - `hero-wedding.webm` (optional but recommended for better browser support)

### Video Optimization

If you have raw footage, convert it using these tools:

**Option 1: Online Converter (Easy)**
- Upload to https://cloudconvert.com/
- Convert to MP4, set quality to "Good" (not Maximum)
- Download and rename to `hero-wedding.mp4`

**Option 2: HandBrake (Desktop App)**
1. Download HandBrake (free)
2. Open your video
3. Preset: "Web" → "Gmail Medium 5 Minutes 720p30"
4. Save as `hero-wedding.mp4`

**Option 3: FFmpeg (Command Line)**
```bash
# Convert to optimized MP4
ffmpeg -i input.mp4 -c:v libx264 -crf 28 -preset slow -vf scale=1920:1080 -an hero-wedding.mp4

# Convert to WebM (optional)
ffmpeg -i input.mp4 -c:v libvpx-vp9 -crf 30 -b:v 0 -vf scale=1920:1080 -an hero-wedding.webm
```

### Automatic Fallback
Don't worry! If the video doesn't load or isn't available:
- The site automatically shows your hero background image (`images/hero-bg.jpg`)
- No broken experience for users
- Works perfectly on mobile devices

### Testing
1. Add videos to `/videos/` folder
2. Open your site
3. Video should autoplay (muted) in the background
4. If no video, image fallback appears automatically

### Recommended Video Content
- Slow-motion wedding ceremony moments
- Couple walking hand-in-hand
- Reception decorations with soft lighting
- Cinematic venue shots

**Tip**: Use footage without people's faces for privacy and broader appeal!

# WebP Image Optimization Guide

## Why WebP?
WebP images are 25-35% smaller than JPG/PNG while maintaining the same visual quality. This means:
- ⚡ Faster page load times
- 📱 Better mobile experience  
- 💰 Lower bandwidth costs
- 🚀 Improved SEO rankings

## Quick Setup (3 Steps)

### Step 1: Convert Your Images

**Option A: Online Converter (Easiest)**
1. Go to https://cloudconvert.com/jpg-to-webp
2. Upload your JPG images
3. Click "Convert"
4. Download the WebP files
5. Keep the same filenames (e.g., `portfolio-user-1.jpg` → `portfolio-user-1.webp`)

**Option B: Bulk Conversion (Node.js - Recommended)**
```bash
# Install converter
npm install -g sharp-cli

# Convert all JPGs to WebP (run in project directory)
npx sharp-cli --input "images/*.jpg" --output "images/{name}.webp" --webp

# Convert PNGs too
npx sharp-cli --input "images/*.png" --output "images/{name}.webp" --webp
```

### Step 2: Use `<picture>` Tag for Best Support

Replace regular `<img>` tags with:

```html
<!-- Before -->
<img src="images/portfolio-user-1.jpg" alt="Wedding">

<!-- After (with WebP support) -->
<picture>
  <source srcset="images/portfolio-user-1.webp" type="image/webp">
  <img src="images/portfolio-user-1.jpg" alt="Wedding" loading="lazy">
</picture>
```

Browsers automatically use WebP if supported, fall back to JPG if not!

### Step 3: Enable Lazy Loading
Already added to your site! Images load only when needed:
```html
<img src="image.jpg" loading="lazy">
```

## Automatic WebP Serving (Advanced)

If using Apache server, add this to `.htaccess`:

```apache
<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteCond %{HTTP_ACCEPT} image/webp
  RewriteCond %{DOCUMENT_ROOT}/$1.webp -f
  RewriteRule ^(images/.+)\.(jpe?g|png)$ $1.webp [T=image/webp,E=accept:1]
</IfModule>

<IfModule mod_headers.c>
  Header append Vary Accept env=REDIRECT_accept
</IfModule>
```

This automatically serves WebP to supporting browsers WITHOUT changing HTML!

## Testing

1. Convert 1-2 images to WebP
2. Check file sizes (should be ~30% smaller)
3. Test in browser - images should look identical
4. Convert all images once confirmed working

## Recommended Workflow

1. **New Photos**: Convert to WebP before uploading
2. **Existing Photos**: Convert in batches during low-traffic times
3. **Keep Originals**: Store JPG/PNG as backups

Your site already has lazy loading enabled, so adding WebP will further boost performance!

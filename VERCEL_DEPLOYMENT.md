# Vercel Deployment Guide for TRCN CBT PWA

## Files in This Project

- **mytrcn.html** - Main PWA application (includes inlined service worker)
- **vercel.json** - Vercel configuration (caching, headers, routing)
- **.vercelignore** - Files to ignore during deployment

## Deployment Instructions

### Option 1: Deploy Using Vercel CLI (Recommended)

```bash
npm install -g vercel
cd c:/Users/user/OneDrive
vercel
```

Follow the prompts:
- Link to existing project or create new
- Select your Vercel account
- Confirm deployment

### Option 2: Deploy via GitHub (Git Integration)

1. Push this folder to GitHub:
```bash
cd c:/Users/user/OneDrive
git init
git add .
git commit -m "TRCN CBT PWA for Vercel"
git remote add origin https://github.com/YOUR_USERNAME/your-repo.git
git push -u origin main
```

2. Import project in Vercel:
- Go to https://vercel.com/new
- Select "Import Git Repository"
- Paste your GitHub repo URL
- Click "Import"
- Click "Deploy"

### Option 3: Deploy via Vercel Web Dashboard

1. Go to https://vercel.com/new
2. Select "Create a blank project" or "Import"
3. Upload this folder as a project
4. Vercel will auto-detect the configuration

## What the Configuration Does

### Cache Headers
- **HTML files**: No caching (always fetches latest)
- **Assets (JS, CSS, images, fonts)**: 1 year cache (immutable)
- This ensures users get updates while keeping app fast

### Security Headers
- **X-Content-Type-Options**: Prevents MIME sniffing
- **X-Frame-Options**: Prevents clickjacking
- **X-XSS-Protection**: XSS protection

### Routing
- All routes rewrite to `mytrcn.html` (SPA routing)
- Works seamlessly with client-side routing

## After Deployment

### Your app will be available at:
```
https://your-project.vercel.app
```

### Test the PWA:
1. Visit your Vercel URL in mobile browser
2. You'll see "Install App" prompt (Android)
3. Or tap menu → "Add to Home Screen" (iOS)
4. App works offline after first load

### Monitor Deployment:
1. Go to https://vercel.com/dashboard
2. Select your project
3. View logs, analytics, and settings
4. Set custom domain if needed

## Offline Functionality

The service worker is already configured to:
- Pre-cache the app shell on first visit
- Cache assets automatically
- Use smart fallback strategies
- Work perfectly offline after initial load

## Performance Optimization

Your PWA on Vercel includes:
- ✅ Gzip compression (automatic)
- ✅ Edge caching for assets
- ✅ Global CDN distribution
- ✅ Instant deployment with rollbacks
- ✅ HTTPS by default
- ✅ Smart service worker caching

## Troubleshooting

### Service Worker Not Working
- Clear browser cache: DevTools → Application → Clear site data
- Rebuild service worker: Hard refresh (Ctrl+Shift+R)

### PWA Not Installing
- Make sure HTTPS is enabled (automatic on Vercel)
- Check manifest in HTML (should be base64 encoded)
- Test in Chrome DevTools → Application → Manifest

### Cache Issues
- Asset cache: 1 year (update if you change static files)
- HTML cache: No cache (always fresh)
- Use updated filenames or version numbers for assets

## Custom Domain Setup

To add a custom domain:
1. Go to Vercel dashboard
2. Select project → Settings → Domains
3. Add your domain
4. Update DNS records as shown by Vercel
5. Domain will be live in minutes

## Environment Variables

If you need environment variables:
1. Project Settings → Environment Variables
2. Add key-value pairs
3. Redeployment happens automatically

---

**Deployment Status**: Ready for Vercel ✅
**Service Worker**: Inlined (no separate files needed) ✅
**Offline Support**: Enabled ✅
**PWA Ready**: Yes ✅

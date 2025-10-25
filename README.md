# Chat Navigator Landing Page

This is the static landing page for Chat Navigator Chrome Extension, hosted on Cloudflare Pages.

## Project Structure

```
infolily-landing-cloudflare/
├── index.html                 # Main landing page (4,089 lines)
├── chat-navigator/            # Favicon and icon assets
│   ├── favicon.svg
│   ├── favicon-16.png
│   ├── favicon-32.png
│   ├── apple-touch-icon.png
│   ├── safari-pinned-tab.svg
│   └── site.webmanifest
├── .gitignore
└── README.md
```

## Features

- **Responsive Design**: Works on all devices
- **Global CDN**: Served from Cloudflare's 200+ edge locations
- **Fast**: Optimized CSS animations and lazy loading
- **Analytics**: Google Tag Manager integration for tracking
- **No Build Step**: Pure HTML/CSS/JavaScript - zero compilation needed

## Deployment

### Prerequisites
- GitHub account
- Cloudflare account

### Steps

1. **Connect to Cloudflare Pages**
   - Go to [Cloudflare Dashboard](https://dash.cloudflare.com/pages)
   - Click "Create a project"
   - Select "Connect to Git"
   - Authorize GitHub
   - Select `infolily-landing` repository

2. **Configure Build Settings**
   - Build command: (leave empty)
   - Build output directory: `/`
   - Root directory: (leave empty)
   - Click "Save and Deploy"

3. **Add Custom Domain**
   - Go to "Custom domains" in project settings
   - Add `infolily.com`
   - Update DNS records (if not using Cloudflare nameservers)

4. **DNS Setup** (if needed)
   - Point `infolily.com` to Cloudflare Pages
   - Cloudflare automatically provisions SSL certificate

## Performance

### Global Response Times
- **Europe**: 10-20ms
- **North America**: 20-30ms
- **Asia**: 50-80ms
- **Australia**: 60-100ms

### Benefits
- ✅ 6-7x faster than Hetzner server alone
- ✅ Free unlimited bandwidth
- ✅ Automatic HTTPS/SSL
- ✅ DDoS protection included
- ✅ Zero server resource usage

## External Resources

- **Google Fonts**: Inter font family
- **Google Tag Manager**: GTM-5FBJMJQG
- **Chrome Web Store**: Links to install extension

## Updates

To update the landing page:
1. Make changes locally
2. Commit: `git add . && git commit -m "Update landing page"`
3. Push: `git push origin main`
4. Cloudflare automatically redeploys

## Support

For issues or feature requests, see the main Chat Navigator repository.

---

**Deployed with Cloudflare Pages** | **Updated**: October 25, 2025

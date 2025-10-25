# Cloudflare Pages Deployment Guide

## ✅ Project Ready!

Your landing page is ready to be deployed to Cloudflare Pages. This guide walks you through the manual setup steps.

**Repository**: https://github.com/mezbahalam/infolily-landing

---

## Step-by-Step Deployment

### Step 1: Access Cloudflare Dashboard

1. Go to [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. Login with your Cloudflare account
3. Navigate to **"Pages"** (left sidebar)

### Step 2: Create a New Pages Project

1. Click **"Create a project"** button
2. Click **"Connect to Git"**
3. You may need to authorize GitHub access (follow prompts)
4. Select your GitHub organization/account

### Step 3: Select Repository

1. Search for **"infolily-landing"**
2. Click to select it
3. Click **"Install & Authorize"** (if prompted)

### Step 4: Configure Build Settings

**Build command**: (leave empty)
- This is pure HTML - no build step needed

**Build output directory**: `/`
- Everything is in root directory

**Root directory**: (leave empty)
- Standard deployment

**Click "Save and Deploy"**

> ⏳ Cloudflare will now build and deploy your site (takes ~2-5 minutes)

### Step 5: View Deployment

After deployment completes:
1. You'll get a temporary URL like `https://xxx-yyy.pages.dev`
2. Test the site works correctly
3. Check that:
   - Page loads quickly
   - All animations work
   - Links to Chrome Web Store work
   - Footer links point to `api-cn.infolily.com`

### Step 6: Add Custom Domain

#### Option A: Using Cloudflare DNS (Recommended)

1. In your Cloudflare Pages project, go to **"Custom domains"**
2. Click **"Set up a custom domain"**
3. Enter: `infolily.com`
4. Click **"Continue"**
5. Cloudflare handles DNS automatically
6. Wait for DNS propagation (usually 1-5 minutes)

#### Option B: Using External DNS Provider

If your domain DNS is managed elsewhere:

1. In your Cloudflare Pages project, go to **"Custom domains"**
2. Click **"Set up a custom domain"**
3. Enter: `infolily.com`
4. Get the CNAME record provided by Cloudflare
5. Add CNAME record in your DNS provider:
   ```
   Name: infolily.com (or @)
   Value: [cname-value-from-cloudflare].pages.dev
   ```
6. Wait for DNS propagation

### Step 7: Verify Domain & SSL

1. Wait for domain status to show "✓ Verified"
2. SSL certificate auto-provisioned by Cloudflare
3. Both `http://infolily.com` and `https://infolily.com` should work
4. HTTP automatically redirects to HTTPS

### Step 8: Test Live Site

```bash
# Test from command line
curl -I https://infolily.com

# Should return 200 OK
# Check response headers for Cloudflare cache info
```

---

## After Deployment

### Auto-Updates

Every time you push to GitHub:
```bash
cd /Users/mezbah/microstartup/infolily-landing-cloudflare
git add .
git commit -m "Update landing page"
git push origin master
```

Cloudflare automatically:
1. Detects the push
2. Redeploys the site
3. Clears cache
4. Usually live within 1-2 minutes

### Monitor Deployments

1. Go to Cloudflare Pages project
2. Click **"Deployments"** tab
3. See build status and history
4. View logs if there are issues

---

## Performance Verification

After deployment, verify performance:

### Check Global Performance
```bash
# Use Cloudflare's Speed Test
# https://www.cloudflare.com/speed/

# Or test from different regions
curl -w "@curl-format.txt" -o /dev/null -s https://infolily.com
```

### Expected Response Times
- **Europe**: 10-20ms
- **North America**: 20-30ms
- **Asia**: 50-80ms
- **Australia**: 60-100ms

### Verify Analytics

1. In Cloudflare Pages project, view **"Analytics"**
2. You should see:
   - Request counts
   - Cache status
   - Response times
   - Geographic distribution

---

## DNS Configuration Examples

### If using Cloudflare DNS:

You need to point your domain registrar to Cloudflare nameservers:
```
ns1.cloudflare.com
ns2.cloudflare.com
```

Then add the Pages project domain in Cloudflare dashboard.

### If using external DNS (GoDaddy, Namecheap, etc.):

Add CNAME record:
```
Host: infolily.com (or @ for apex domain)
Value: [cloudflare-pages-cname].pages.dev
TTL: 3600 (1 hour) or automatic
```

---

## Troubleshooting

### Domain shows "CNAME validation required"
- Ensure CNAME record is added to DNS
- Wait 5-10 minutes for DNS propagation
- Use `dig` command to verify:
  ```bash
  dig infolily.com CNAME
  ```

### Site shows 404 errors
- Ensure `index.html` is in root directory
- Check that GitHub push was successful
- Verify Cloudflare build status shows success

### Google Tag Manager not tracking
- Check GTM container ID is correct: `GTM-5FBJMJQG`
- Verify no browser extensions blocking GTM
- Check browser console for errors

### Links to /privacy-policy not working
- They should point to `https://api-cn.infolily.com/privacy-policy`
- This is intentional - pages are hosted on Rails API, not Cloudflare
- If you want to host them on Cloudflare, create `privacy-policy.html` and `terms.html`

---

## Maintenance

### Monthly Tasks

1. **Monitor Performance**
   - Check analytics in Cloudflare dashboard
   - Look for any 404 or 5xx errors

2. **Review Google Analytics**
   - Check visitor traffic
   - Monitor bounce rate
   - Track conversion to Chrome Web Store

3. **Update as Needed**
   - Make changes to `index.html`
   - Push to GitHub
   - Site auto-redeploys

### SSL Certificate

- ✅ Automatically provisioned by Cloudflare
- ✅ Auto-renews 30 days before expiry
- ✅ No action needed from you

---

## Advanced Options (Optional)

### Enable Caching Headers

If you want to cache the page longer in browsers:

Add `_headers` file in root:
```
/
  Cache-Control: public, max-age=3600
```

### Custom Error Pages

Create `404.html` for custom 404 page (optional)

### Page Rules

In Cloudflare dashboard → Page Rules:
- Force HTTPS
- Browser cache TTL
- Security settings

---

## Questions?

Refer to:
- [Cloudflare Pages Documentation](https://developers.cloudflare.com/pages/)
- [Cloudflare Community](https://community.cloudflare.com/)

---

**Next Steps**: Follow "Step 1: Access Cloudflare Dashboard" above to begin deployment.

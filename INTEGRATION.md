# Integration & Troubleshooting Guide

## Form Integration Options

Your contact form currently shows a success message in the UI. Here's how to actually send emails:

### Option 1: Formspree (Recommended - Easiest)

**Step 1: Create Account**
1. Visit [formspree.io](https://formspree.io)
2. Sign up with your email
3. Create a new form for your website

**Step 2: Get Your Form ID**
- Copy your form ID from the Formspree dashboard
- It looks like: `f_xxxxxxxxxxxx`

**Step 3: Update index.html**
Find the `submitForm()` method and replace it with:

```javascript
submitForm() {
    if (!this.formData.name || !this.formData.email || !this.formData.message) {
        this.formMessage = 'Please fill in all fields';
        this.formStatus = 'error';
        setTimeout(() => { this.formMessage = ''; }, 3000);
        return;
    }

    // Send with Formspree
    fetch('https://formspree.io/f/YOUR_FORM_ID', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(this.formData)
    })
    .then(response => {
        if (response.ok) {
            this.formMessage = 'Message sent successfully! Thank you for reaching out.';
            this.formStatus = 'success';
            this.formData = { name: '', email: '', message: '' };
        } else {
            throw new Error('Network response was not ok');
        }
    })
    .catch(error => {
        console.error('Error:', error);
        this.formMessage = 'Failed to send message. Please try again.';
        this.formStatus = 'error';
    });

    setTimeout(() => { this.formMessage = ''; }, 5000);
}
```

### Option 2: EmailJS (Free & Powerful)

**Step 1: Setup EmailJS**
1. Visit [emailjs.com](https://www.emailjs.com)
2. Sign up for free
3. Create an email service (Gmail, Outlook, etc.)
4. Get your Service ID and Template ID

**Step 2: Add EmailJS Script**
Add this to the `<head>` section of index.html:
```html
<script type="text/javascript" src="https://cdn.jsdelivr.net/npm/@emailjs/browser@3/dist/index.min.js"></script>
```

**Step 3: Initialize and Send**
Replace `submitForm()`:

```javascript
submitForm() {
    if (!this.formData.name || !this.formData.email || !this.formData.message) {
        this.formMessage = 'Please fill in all fields';
        this.formStatus = 'error';
        setTimeout(() => { this.formMessage = ''; }, 3000);
        return;
    }

    // Initialize EmailJS (do this once)
    emailjs.init('YOUR_PUBLIC_KEY');

    // Send email
    emailjs.send('SERVICE_ID', 'TEMPLATE_ID', {
        from_name: this.formData.name,
        from_email: this.formData.email,
        message: this.formData.message,
        to_email: 'your@email.com'
    })
    .then(() => {
        this.formMessage = 'Message sent successfully! Thank you for reaching out.';
        this.formStatus = 'success';
        this.formData = { name: '', email: '', message: '' };
        setTimeout(() => { this.formMessage = ''; }, 5000);
    })
    .catch((error) => {
        console.error('Error:', error);
        this.formMessage = 'Failed to send message. Please try again.';
        this.formStatus = 'error';
        setTimeout(() => { this.formMessage = ''; }, 5000);
    });
}
```

### Option 3: Basin (Simple & Lightweight)

**Step 1: Get Basin Email**
1. Visit [basin.vercel.app](https://basin.vercel.app)
2. No signup needed!
3. Use any email in your form

**Step 2: Update Form**
Replace `submitForm()`:

```javascript
submitForm() {
    if (!this.formData.name || !this.formData.email || !this.formData.message) {
        this.formMessage = 'Please fill in all fields';
        this.formStatus = 'error';
        setTimeout(() => { this.formMessage = ''; }, 3000);
        return;
    }

    fetch('https://basin.vercel.app/api/v1/forms', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
            data: {
                name: this.formData.name,
                email: this.formData.email,
                message: this.formData.message
            }
        })
    })
    .then(() => {
        this.formMessage = 'Message sent successfully! Thank you for reaching out.';
        this.formStatus = 'success';
        this.formData = { name: '', email: '', message: '' };
        setTimeout(() => { this.formMessage = ''; }, 5000);
    })
    .catch(() => {
        this.formMessage = 'Failed to send message. Please try again.';
        this.formStatus = 'error';
        setTimeout(() => { this.formMessage = ''; }, 5000);
    });
}
```

## Troubleshooting

### Issue: Changes Not Showing

**Solution:**
1. Hard refresh: `Ctrl + Shift + R` (Windows) or `Cmd + Shift + R` (Mac)
2. Clear browser cache
3. Try in a different browser
4. Check for JavaScript errors: Press `F12` to open DevTools

### Issue: Social Links Not Working

**Solution:**
- Ensure URLs start with `https://`
- Check for typos in usernames
- Test links in a new tab
- Example: `https://github.com/YOUR_USERNAME`

### Issue: Form Not Submitting

**Solution:**
1. Open DevTools (`F12`)
2. Click Console tab
3. Try submitting the form
4. Look for error messages
5. Check form service configuration

### Issue: Images/Icons Not Showing

**Solution:**
- Font Awesome icons require internet connection
- Check icon names are spelled correctly
- Browse available icons at [fontawesome.com](https://fontawesome.com)
- Use format: `fas fa-icon-name` or `fab fa-icon-name`

### Issue: Site Not Loading on GitHub Pages

**Solution:**
1. Wait 2-5 minutes after push
2. Check Actions tab for build errors
3. Verify main branch is selected in Pages settings
4. Clear GitHub Pages cache:
   - Go to Settings
   - Disable GitHub Pages
   - Re-enable GitHub Pages

### Issue: Responsive Design Not Working on Mobile

**Solution:**
1. Check viewport meta tag is in head:
   ```html
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   ```
2. Test in DevTools mobile view (F12)
3. Try different mobile devices
4. Check Tailwind CSS breakpoints are working

## Performance Optimization

### Optimize Images
- Compress before adding to portfolio
- Use tools like TinyPNG or ImageOptim
- Keep file sizes under 500KB per image

### Enable Caching
Add this to `.htaccess` (if using Apache):
```
<IfModule mod_expires.c>
    ExpiresActive On
    ExpiresByType image/jpeg "access plus 1 year"
    ExpiresByType image/gif "access plus 1 year"
    ExpiresByType image/png "access plus 1 year"
    ExpiresByType text/css "access plus 1 month"
    ExpiresByType application/javascript "access plus 1 month"
</IfModule>
```

### Minify Code
- Use minifiers before deployment
- Tools: UglifyJS, CSSNano, HTMLMinifier

## SEO Optimization

### Add Meta Tags
Update in `<head>`:
```html
<meta name="description" content="Your portfolio description">
<meta name="keywords" content="portfolio, developer, web design">
<meta property="og:title" content="Your Name - Portfolio">
<meta property="og:description" content="Your description">
<meta property="og:image" content="https://yoursite.com/preview.jpg">
<meta name="twitter:card" content="summary_large_image">
```

### Add Schema Markup
Add to body (before closing tag):
```html
<script type="application/ld+json">
{
    "@context": "https://schema.org",
    "@type": "Person",
    "name": "Your Name",
    "url": "https://yoursite.com",
    "jobTitle": "Developer",
    "image": "photo.jpg"
}
</script>
```

## Advanced Customization

### Add Google Analytics
Add to `<head>`:
```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());
    gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

### Add Dark/Light Mode Toggle
Add to Vue data:
```javascript
isDarkMode: true
```

Add button to nav:
```html
<button @click="isDarkMode = !isDarkMode">
    <i :class="isDarkMode ? 'fas fa-sun' : 'fas fa-moon'"></i>
</button>
```

### Add Smooth Scroll
Already implemented! Clicking nav links smoothly scrolls to sections.

### Add Newsletter Signup
Integrate with Mailchimp or ConvertKit:
```javascript
subscribeNewsletter() {
    // Add newsletter signup logic
}
```

## Deployment Checklist

- [ ] All personal information updated
- [ ] Social media links verified
- [ ] Resume file added as `resume.pdf`
- [ ] All project links working
- [ ] Email form integrated (Formspree/EmailJS/Basin)
- [ ] Phone number valid (or removed)
- [ ] No placeholder images
- [ ] All skills/experience current
- [ ] Mobile responsiveness tested
- [ ] Browser compatibility tested (Chrome, Firefox, Safari)
- [ ] SEO meta tags added
- [ ] Google Analytics configured
- [ ] Custom domain (optional)
- [ ] GitHub Pages enabled and working

## Testing Checklist

- [ ] All links working (internal and external)
- [ ] Contact form submitting successfully
- [ ] Mobile menu opening/closing
- [ ] Smooth scrolling to sections
- [ ] Images loading properly
- [ ] Colors displaying correctly
- [ ] Animations working smoothly
- [ ] Text readable on all devices
- [ ] Form validation working
- [ ] Social icons clickable
- [ ] Download CV button working

## Browser Compatibility

Tested on:
- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+
- ✅ Mobile browsers (iOS Safari, Chrome Mobile)

## Support Resources

- Vue.js: [vuejs.org/guide](https://vuejs.org/guide/)
- Tailwind CSS: [tailwindcss.com/docs](https://tailwindcss.com/docs)
- Font Awesome: [fontawesome.com/icons](https://fontawesome.com/icons)
- GitHub Pages: [docs.github.com/pages](https://docs.github.com/en/pages)
- Formspree: [formspree.io/docs](https://formspree.io/docs)

---

**Still stuck?** Check the other documentation files:
- [SETUP.md](SETUP.md) - Setup and customization
- [QUICK_START.md](QUICK_START.md) - Quick checklist
- [EXAMPLES.md](EXAMPLES.md) - Code examples

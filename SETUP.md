# Vue.js Portfolio Setup Guide

## Overview

Your portfolio is now powered by **Vue.js 3**, a modern, easy-to-use JavaScript framework. The site is fully responsive and works perfectly with GitHub Pages as a static website.

## Why Vue.js?

✅ **Easy to learn** - Simple syntax and clear documentation  
✅ **Wide support** - One of the most popular JS frameworks  
✅ **GitHub Pages compatible** - No build step required; runs directly in the browser via CDN  
✅ **Reactive data** - Change your content in one place and it updates everywhere  

## Getting Started

### 1. **Edit Your Profile Data**

All your content is stored in `index.html` within the Vue app's `data()` object. You can also use `data.json` as a reference.

To update your information:

1. Open `index.html` in your editor
2. Find the `data()` section in the script tag (around line 400)
3. Update the following fields:

```javascript
profile: {
    name: 'Aurora',           // Brand name shown in nav
    fullName: 'Alex Aurora',  // Your name
    title: 'Your Title',      // Professional title
    tagline: 'Your tagline...',
    emoji: '👨‍💻',             // Profile emoji
    cvUrl: 'resume.pdf',      // Path to your CV
    social: {
        github: 'https://github.com/yourname',
        linkedin: 'https://linkedin.com/in/yourname',
        twitter: 'https://twitter.com/yourname',
        instagram: 'https://instagram.com/yourname'
    },
    // ... and many more fields below
}
```

### 2. **Update Each Section**

#### Hero/Home Section
- `fullName` - Your name
- `title` - Your professional title
- `tagline` - Brief description
- `social.github/linkedin/twitter/instagram` - Your social links
- `cvUrl` - Link to your resume PDF

#### About Section
- `bio` - Array of paragraphs about you
- `stats` - Your achievements (projects, clients, years, awards)
- `emoji` - Your profile emoji

#### Experience Section
- `experience` - Array of job positions with dates, company, and description

#### Skills Section
- `skills` - Organized by category (Frontend, Backend, etc.)
- Each skill has a name, level (0-100%), and gradient colors
- `tools` - DevOps and tools you use

#### Services Section
- `services` - Array of services you offer with descriptions and icons

#### Portfolio Section
- `portfolio` - Your projects with descriptions, technologies, and links

#### Testimonials Section
- `testimonials` - Client reviews with names and quotes

#### Blog Section
- `blog` - Your blog posts with dates and excerpts

#### Contact Section
- `contactInfo` - Email, phone, and location
- Form submission is handled automatically

## Customization Guide

### Change Colors

The Aurora theme uses gradient colors. Find and replace these hex codes:

- `#00ffaa` - Aurora Green
- `#00aaff` - Aurora Blue
- `#aa00ff` - Aurora Purple
- `#ff00aa` - Aurora Pink

To use custom colors, just update the `gradientFrom` and `gradientTo` properties in any section.

### Update Social Links

Replace the placeholder URLs in the `social` object:

```javascript
social: {
    github: 'https://github.com/YOUR_USERNAME',
    linkedin: 'https://linkedin.com/in/YOUR_USERNAME',
    twitter: 'https://twitter.com/YOUR_USERNAME',
    instagram: 'https://instagram.com/YOUR_USERNAME'
}
```

### Add New Portfolio Projects

Add a new object to the `portfolio` array:

```javascript
{
    title: 'Project Name',
    description: 'Brief project description',
    icon: 'fas fa-icon-name',  // Font Awesome icon
    gradientFrom: '#00ffaa',
    gradientTo: '#00aaff',
    technologies: [
        { name: 'React', color: '#00ffaa' },
        { name: 'Node.js', color: '#00aaff' }
    ],
    liveUrl: 'https://your-project.com',
    githubUrl: 'https://github.com/your-project'
}
```

### Form Handling

The contact form currently:
- ✅ Shows validation messages
- ✅ Displays success/error feedback
- 📝 Logs to console

To send emails, integrate with:
- **EmailJS** (free tier available)
- **Formspree** (simple integration)
- **Basin** (no server required)

Example with Formspree:
```javascript
submitForm() {
    // Replace the console.log with:
    fetch('https://formspree.io/f/YOUR_FORM_ID', {
        method: 'POST',
        body: JSON.stringify(this.formData),
        headers: { 'Content-Type': 'application/json' }
    })
    .then(() => {
        this.formMessage = 'Message sent successfully!';
        this.formStatus = 'success';
        this.formData = { name: '', email: '', message: '' };
    })
    .catch(() => {
        this.formMessage = 'Failed to send message';
        this.formStatus = 'error';
    });
}
```

## Deploying to GitHub Pages

### 1. Create a GitHub Repository

```bash
cd your-portfolio-folder
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/personal-portfolio.git
git push -u origin main
```

### 2. Enable GitHub Pages

1. Go to your repository on GitHub
2. Settings → Pages
3. Select "main" branch as the source
4. Save

Your site will be live at: `https://YOUR_USERNAME.github.io/personal-portfolio`

### 3. Custom Domain (Optional)

1. Go to Settings → Pages
2. Add your custom domain
3. Update DNS settings with your registrar

## File Structure

```
personal-portfolio/
├── index.html          # Main file with Vue app
├── data.json          # Reference data (optional)
├── README.md          # Original template info
├── SETUP.md           # This setup guide
└── resume.pdf         # Your resume (add this)
```

## Tips & Best Practices

1. **Test Locally** - Open `index.html` directly in your browser to test
2. **Use Font Awesome Icons** - Browse available icons at [fontawesome.com](https://fontawesome.com)
3. **Keep Data Organized** - Update `data.json` first, then copy to `index.html`
4. **Mobile Testing** - Always test on mobile devices
5. **Update Regularly** - Keep your portfolio fresh with new projects and blog posts

## Vue.js Basics (for reference)

Your portfolio uses these Vue features:

- **`{{ variable }}`** - Display data
- **`v-for="item in array"`** - Loop through items
- **`v-if="condition"`** - Show/hide elements
- **`@click="method"`** - Handle clicks
- **`@submit.prevent`** - Form submission
- **`:class`** - Dynamic classes
- **`:style`** - Dynamic styles
- **`v-model`** - Form input binding

## Troubleshooting

**Changes not showing?**
- Hard refresh your browser (Ctrl+Shift+R or Cmd+Shift+R)
- Clear cache if needed

**Social links not working?**
- Ensure URLs start with `https://`
- Check for typos in usernames

**GitHub Pages not updating?**
- Wait 2-5 minutes for deployment
- Check Actions tab for build errors

**Form not submitting?**
- Check console for errors (F12)
- Ensure you've integrated a form service

## Need Help?

- Vue.js Docs: [vuejs.org](https://vuejs.org)
- Font Awesome Icons: [fontawesome.com](https://fontawesome.com)
- GitHub Pages: [pages.github.com](https://pages.github.com)
- Tailwind CSS: [tailwindcss.com](https://tailwindcss.com)

## License

This template is based on Aurora by OSSPH. Feel free to use and modify for your personal portfolio.

---

Happy building! 🚀

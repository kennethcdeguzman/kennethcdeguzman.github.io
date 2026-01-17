# Portfolio Configuration Examples

This file shows you how to customize different parts of your portfolio.

## Profile Object Structure

```javascript
profile: {
    // Basic Information
    name: 'Aurora',                          // Brand name (shown in nav)
    fullName: 'Alex Aurora',                 // Your actual name
    title: 'Full-Stack Developer',           // Your professional title
    tagline: 'Crafting digital experiences', // Short description
    emoji: '👨‍💻',                             // Profile emoji
    cvUrl: 'resume.pdf',                     // Path to your CV
    
    // Social Links
    social: {
        github: 'https://github.com/username',
        linkedin: 'https://linkedin.com/in/username',
        twitter: 'https://twitter.com/username',
        instagram: 'https://instagram.com/username'
    },
    
    // ... other sections below
}
```

## 1. Experience Section

### Example: Full Entry
```javascript
experience: [
    {
        position: 'Senior Full-Stack Developer',
        company: 'Tech Innovations Inc.',
        dates: '2021 - Present',
        color: '#00ffaa',                    // Aurora Green
        description: 'Lead development of enterprise-scale web applications...'
    },
    {
        position: 'Full-Stack Developer',
        company: 'Digital Solutions Agency',
        dates: '2019 - 2021',
        color: '#00aaff',                    // Aurora Blue
        description: 'Developed custom web applications for various clients...'
    }
]
```

### Tips
- Update `dates` to your actual employment dates
- Use year ranges like "2021 - Present" or "2019 - 2021"
- Keep descriptions to 1-2 sentences
- Use different colors for visual distinction

## 2. Skills Section

### Example: Complete Skills
```javascript
skills: [
    {
        category: 'Frontend Development',
        color: '#00ffaa',
        items: [
            { name: 'React / Next.js', level: 95, color1: '#00ffaa', color2: '#00aaff' },
            { name: 'TypeScript', level: 90, color1: '#00aaff', color2: '#aa00ff' },
            { name: 'Tailwind CSS', level: 85, color1: '#aa00ff', color2: '#ff00aa' },
            { name: 'Vue.js', level: 85, color1: '#ff00aa', color2: '#00ffaa' }
        ]
    },
    {
        category: 'Backend Development',
        color: '#00aaff',
        items: [
            { name: 'Node.js / Express', level: 90, color1: '#00ffaa', color2: '#00aaff' },
            { name: 'Python / Django', level: 85, color1: '#00aaff', color2: '#aa00ff' },
            { name: 'PostgreSQL / MongoDB', level: 88, color1: '#aa00ff', color2: '#ff00aa' }
        ]
    }
]
```

### Tips
- Level is 0-100 (percentage)
- color1 and color2 create a gradient in the progress bar
- Add as many skills as you want
- Remove categories you don't use

## 3. Portfolio Section

### Example: Project Entry
```javascript
portfolio: [
    {
        title: 'E-Commerce Platform',
        description: 'Full-stack e-commerce solution with payment integration',
        icon: 'fas fa-shopping-cart',        // Font Awesome icon
        gradientFrom: '#00ffaa',
        gradientTo: '#00aaff',
        technologies: [
            { name: 'React', color: '#00ffaa' },
            { name: 'Node.js', color: '#00aaff' },
            { name: 'MongoDB', color: '#aa00ff' }
        ],
        liveUrl: 'https://ecommerce-demo.com',
        githubUrl: 'https://github.com/username/ecommerce'
    }
]
```

### Font Awesome Icons
Popular project icons:
- `fas fa-shopping-cart` - E-Commerce
- `fas fa-users` - Social/Community
- `fas fa-gamepad` - Gaming
- `fas fa-chart-line` - Analytics
- `fas fa-code` - Code/Development
- `fas fa-mobile-alt` - Mobile App
- `fas fa-globe` - Website
- `fas fa-music` - Music/Media

Browse more at [fontawesome.com](https://fontawesome.com/icons)

## 4. Services Section

### Example: Service Entry
```javascript
services: [
    {
        title: 'Web Development',
        description: 'Custom web applications built with modern frameworks...',
        icon: 'fas fa-laptop-code',
        gradientFrom: '#00ffaa',
        gradientTo: '#00aaff'
    }
]
```

### Popular Service Icons
- `fas fa-laptop-code` - Web Development
- `fas fa-mobile-alt` - Mobile Development
- `fas fa-palette` - Design
- `fas fa-cloud` - Cloud/DevOps
- `fas fa-chart-line` - Consulting
- `fas fa-cogs` - System Integration

## 5. Testimonials Section

### Example: Testimonial Entry
```javascript
testimonials: [
    {
        name: 'John Doe',
        title: 'CEO, TechStart',
        initials: 'JD',                       // First letters of name
        quote: 'Alex delivered an exceptional product that exceeded our expectations...',
        gradientFrom: '#00ffaa',
        gradientTo: '#00aaff',
        starColor: '#00ffaa'                 // Star color (same as gradient start)
    }
]
```

### Tips
- Use real client names and testimonials
- Keep quotes to 2-3 sentences
- Initials are displayed in avatar circle
- Star color should match the gradient starting color

## 6. Blog Section

### Example: Blog Post Entry
```javascript
blog: [
    {
        title: 'The Future of Web Development',
        date: 'March 15, 2024',
        excerpt: 'Exploring emerging trends and technologies...',
        gradientFrom: '#00ffaa',
        gradientTo: '#00aaff',
        url: 'https://yourblog.com/post1'     // Link to full article
    }
]
```

### Tips
- Use format: "Month DD, YYYY" for dates
- Excerpts should be 1-2 sentences
- Link to your full blog posts
- Add as many posts as you want

## 7. Contact Info

### Example: Contact Entry
```javascript
contactInfo: [
    {
        label: 'Email',
        value: 'your@email.com',
        icon: 'fas fa-envelope',
        gradientFrom: '#00ffaa',
        gradientTo: '#00aaff'
    },
    {
        label: 'Phone',
        value: '+1 (555) 123-4567',
        icon: 'fas fa-phone',
        gradientFrom: '#00aaff',
        gradientTo: '#aa00ff'
    },
    {
        label: 'Location',
        value: 'San Francisco, CA',
        icon: 'fas fa-map-marker-alt',
        gradientFrom: '#aa00ff',
        gradientTo: '#ff00aa'
    }
]
```

## Color Gradients Guide

The Aurora theme uses beautiful color gradients. Here are the standard combinations:

```javascript
// Green to Blue
gradientFrom: '#00ffaa'
gradientTo: '#00aaff'

// Blue to Purple
gradientFrom: '#00aaff'
gradientTo: '#aa00ff'

// Purple to Pink
gradientFrom: '#aa00ff'
gradientTo: '#ff00aa'

// Pink to Green
gradientFrom: '#ff00aa'
gradientTo: '#00ffaa'

// Single color repeating
gradientFrom: '#00ffaa'
gradientTo: '#00ffaa'
```

### Custom Colors
You can use any hex color:
```javascript
gradientFrom: '#FF6B6B'  // Red
gradientTo: '#4ECDC4'    // Teal
```

## Bio Section

### Example: Multiple Paragraphs
```javascript
bio: [
    'With over 7 years of experience in web development and design, I specialize in creating immersive digital experiences that captivate users and drive business growth.',
    
    'My journey began with a fascination for the intersection of art and technology. Today, I work with cutting-edge technologies to build scalable, performant applications.',
    
    'I believe in continuous learning and staying ahead of technology trends to deliver innovative solutions.'
]
```

### Tips
- Each item is a separate paragraph
- Keep paragraphs to 2-3 sentences
- Add as many paragraphs as you need

## Stats Section

### Example: Achievement Stats
```javascript
stats: [
    { value: '100+', label: 'Projects Completed', color: '#00ffaa' },
    { value: '50+', label: 'Happy Clients', color: '#00aaff' },
    { value: '7+', label: 'Years Experience', color: '#aa00ff' },
    { value: '15+', label: 'Awards Won', color: '#ff00aa' }
]
```

### Tips
- Value can be numbers or text
- Keep labels short (2-3 words)
- Use descriptive metrics
- Change color to match your theme

## Tools & Technologies

### Example: Tools List
```javascript
tools: [
    { name: 'Docker', icon: 'fab fa-docker', color: '#00ffaa' },
    { name: 'AWS', icon: 'fab fa-aws', color: '#00aaff' },
    { name: 'Git', icon: 'fab fa-git', color: '#aa00ff' },
    { name: 'CI/CD', icon: 'fas fa-infinity', color: '#ff00aa' },
    { name: 'GitHub', icon: 'fab fa-github', color: '#00ffaa' }
]
```

### Popular Tool Icons
- `fab fa-docker` - Docker
- `fab fa-aws` - AWS
- `fab fa-git` - Git
- `fab fa-github` - GitHub
- `fab fa-gitlab` - GitLab
- `fas fa-infinity` - CI/CD
- `fab fa-kubernetes` - Kubernetes

## Complete Example

Here's a minimal example to get you started:

```javascript
profile: {
    name: 'MyPortfolio',
    fullName: 'Your Name',
    title: 'Your Title',
    tagline: 'Your tagline here',
    emoji: '👨‍💻',
    cvUrl: 'resume.pdf',
    social: {
        github: 'https://github.com/yourname',
        linkedin: 'https://linkedin.com/in/yourname',
        twitter: 'https://twitter.com/yourname',
        instagram: 'https://instagram.com/yourname'
    },
    bio: [
        'Your bio paragraph 1.',
        'Your bio paragraph 2.'
    ],
    stats: [
        { value: '10+', label: 'Projects', color: '#00ffaa' },
        { value: '5+', label: 'Clients', color: '#00aaff' },
        { value: '2+', label: 'Years', color: '#aa00ff' },
        { value: '3', label: 'Awards', color: '#ff00aa' }
    ],
    // ... continue with other sections
}
```

---

**Need more help?** Check SETUP.md for detailed instructions!

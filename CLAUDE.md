# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Universal Single-Page Landing Page Template** - A flexible Svelte + Vite template adaptable for any business type (SaaS, E-commerce, Services, Portfolio, etc.)

## Quick Commands

```bash
npm install          # Install dependencies
npm run dev          # Start dev server (http://localhost:5173)
npm run build        # Build for production
npm run preview      # Preview production build
```

## Architecture

```
src/
├── App.svelte              # Root orchestrator
├── main.js                 # Entry point
├── app.css                 # Global styles (Tailwind)
├── components/             # Reusable sections
│   ├── Header.svelte      # Navigation
│   ├── Hero.svelte        # Landing section
│   ├── Features.svelte    # Value propositions
│   ├── Showcase.svelte    # Products/Portfolio/Services
│   ├── SocialProof.svelte # Testimonials/Logos
│   ├── Pricing.svelte     # Plans/Packages
│   ├── FAQ.svelte         # Common questions
│   ├── CTA.svelte         # Call-to-action
│   ├── Contact.svelte     # Contact form
│   └── Footer.svelte      # Links/Legal
└── data/
    └── content.json       # All text/images/config
```

## Claude Code Interaction Guide

### 1. Quick Task Templates

**Component Creation**
```markdown
"Create a [section] with:
- Purpose: [what it achieves]
- Layout: [grid/carousel/cards]
- Content: [from content.json]
- Mobile: [responsive behavior]"
```

**Modification Request**
```markdown
"Update [component] to:
Current: [what exists]
Need: [what to change]
Keep: [what must not break]"
```

**Performance Fix**
```markdown
"Optimize [issue]:
Symptom: [what's wrong]
Metric: [LCP/FID/CLS value]
Target: [desired outcome]"
```

### 2. Business Type Adaptations

**SaaS Landing Page**
```markdown
Sections needed: Hero → Features → Integrations → Pricing → FAQ → CTA
Focus: Feature benefits, pricing tiers, free trial
```

**E-commerce Landing Page**
```markdown
Sections needed: Hero → Categories → Bestsellers → Reviews → Offers → Newsletter
Focus: Product showcase, trust badges, urgency
```

**Service Business**
```markdown
Sections needed: Hero → Services → Process → Portfolio → Testimonials → Contact
Focus: Trust building, case studies, consultation CTA
```

**Portfolio/Agency**
```markdown
Sections needed: Hero → Work → Services → About → Clients → Contact
Focus: Visual showcase, client logos, creative process
```

**Non-profit/Cause**
```markdown
Sections needed: Hero → Mission → Impact → Stories → Donate → Volunteer
Focus: Emotional connection, transparency, action items
```

## Git Workflow Best Practices

### Branch Strategy

```bash
main                 # Production-ready code
├── develop         # Integration branch
├── feature/*       # New features
├── fix/*          # Bug fixes
└── hotfix/*       # Urgent production fixes
```

### Commit Message Format

```bash
# Format: type(scope): description

feat(hero): add video background support
fix(form): resolve validation error
style(header): update mobile menu design
perf(images): implement lazy loading
docs(readme): update installation steps
refactor(data): simplify JSON structure
test(contact): add form validation tests
chore(deps): update dependencies
```

### Common Git Commands

```bash
# Start new feature
git checkout -b feature/testimonial-slider

# Stage and commit changes
git add .
git commit -m "feat(testimonials): add auto-play slider"

# Push to remote
git push -u origin feature/testimonial-slider

# Create pull request (using GitHub CLI)
gh pr create --title "Add testimonial slider" --body "..."

# Merge develop to your branch
git checkout feature/your-branch
git merge develop

# Interactive rebase (clean history)
git rebase -i HEAD~3

# Stash work in progress
git stash save "WIP: hero animation"
git stash pop
```

### Pre-commit Checklist

```markdown
Before committing:
□ Code runs without errors (npm run dev)
□ No console.log statements
□ Images optimized (< 200KB each)
□ Mobile responsive tested
□ Accessibility checked
□ Build succeeds (npm run build)
```

## Universal Section Templates

### 1. Hero Section (Any Business)

```svelte
<section id="hero" class="min-h-screen flex items-center">
  <div class="container mx-auto px-4">
    <div class="max-w-3xl">
      <h1 class="text-4xl md:text-6xl font-bold mb-6">
        {content.hero.headline}
      </h1>
      <p class="text-xl mb-8 text-gray-600">
        {content.hero.subheadline}
      </p>
      <div class="flex gap-4">
        <button class="btn-primary">{content.hero.cta.primary}</button>
        <button class="btn-secondary">{content.hero.cta.secondary}</button>
      </div>
    </div>
  </div>
</section>
```

### 2. Features Grid (Adaptable)

```svelte
<section id="features" class="py-20">
  <div class="container mx-auto px-4">
    <h2 class="text-3xl font-bold text-center mb-12">
      {content.features.title}
    </h2>
    <div class="grid md:grid-cols-3 gap-8">
      {#each content.features.items as feature}
        <div class="text-center p-6">
          <div class="text-4xl mb-4">{feature.icon}</div>
          <h3 class="text-xl font-semibold mb-2">{feature.title}</h3>
          <p class="text-gray-600">{feature.description}</p>
        </div>
      {/each}
    </div>
  </div>
</section>
```

### 3. Social Proof (Universal)

```svelte
<section id="social-proof" class="py-20 bg-gray-50">
  <!-- Client Logos -->
  <div class="container mx-auto px-4 mb-12">
    <p class="text-center text-gray-500 mb-8">Trusted by</p>
    <div class="flex justify-center items-center gap-8 flex-wrap">
      {#each content.clients as client}
        <img src={client.logo} alt={client.name} class="h-12 opacity-60">
      {/each}
    </div>
  </div>
  
  <!-- Testimonials -->
  <div class="container mx-auto px-4">
    <div class="max-w-3xl mx-auto">
      {#each content.testimonials as testimonial}
        <blockquote class="text-center">
          <p class="text-xl italic mb-4">"{testimonial.quote}"</p>
          <cite class="text-sm text-gray-600">
            — {testimonial.author}, {testimonial.role}
          </cite>
        </blockquote>
      {/each}
    </div>
  </div>
</section>
```

### 4. CTA Section (Conversion)

```svelte
<section id="cta" class="py-20 bg-primary text-white">
  <div class="container mx-auto px-4 text-center">
    <h2 class="text-3xl font-bold mb-4">{content.cta.headline}</h2>
    <p class="text-xl mb-8 opacity-90">{content.cta.subheadline}</p>
    <button class="btn-white text-primary">
      {content.cta.button}
    </button>
  </div>
</section>
```

## Content Structure (content.json)

```json
{
  "business": {
    "name": "Your Business",
    "type": "saas|ecommerce|service|portfolio|nonprofit",
    "logo": "/logo.svg",
    "tagline": "Your value proposition"
  },
  "hero": {
    "headline": "Main value proposition",
    "subheadline": "Supporting statement",
    "cta": {
      "primary": "Get Started",
      "secondary": "Learn More"
    },
    "image": "/hero-image.jpg",
    "video": null
  },
  "features": {
    "title": "Why Choose Us",
    "items": [
      {
        "icon": "🚀",
        "title": "Fast",
        "description": "Lightning quick"
      }
    ]
  },
  "testimonials": [
    {
      "quote": "Amazing service!",
      "author": "Jane Doe",
      "role": "CEO at Company",
      "avatar": "/avatar.jpg",
      "rating": 5
    }
  ],
  "pricing": {
    "title": "Simple Pricing",
    "plans": [
      {
        "name": "Starter",
        "price": "$9/mo",
        "features": ["Feature 1", "Feature 2"],
        "recommended": false
      }
    ]
  },
  "faq": [
    {
      "question": "Common question?",
      "answer": "Clear answer."
    }
  ],
  "contact": {
    "title": "Get in Touch",
    "email": "hello@example.com",
    "phone": "+1234567890",
    "address": "123 Main St",
    "form": {
      "endpoint": "/api/contact",
      "fields": ["name", "email", "message"]
    }
  }
}
```

## Performance Optimization Checklist

```markdown
Initial Load:
□ Hero image < 100KB (WebP format)
□ Above-fold CSS inlined
□ Fonts preloaded
□ Critical JS only

Images:
□ Lazy load below fold
□ Use srcset for responsive
□ WebP with fallbacks
□ Blur-up placeholders

Code:
□ Tree-shake unused CSS
□ Split vendor chunks
□ Minify everything
□ Gzip/Brotli enabled
```

## Accessibility Requirements

```svelte
<!-- Every interactive element -->
<button aria-label="Open menu" aria-expanded={isOpen}>

<!-- Every form field -->
<label for="email" class="sr-only">Email</label>
<input id="email" type="email" required aria-required="true">

<!-- Every image -->
<img src={image} alt="Descriptive text">

<!-- Skip navigation -->
<a href="#main" class="sr-only focus:not-sr-only">Skip to content</a>
```

## Common Claude Code Requests

### Quick Fixes
```markdown
"Add mobile menu toggle"
"Make hero responsive"
"Add loading states to forms"
"Implement smooth scroll"
"Add fade-in animations"
```

### Feature Additions
```markdown
"Add newsletter signup to footer"
"Create image gallery in showcase"
"Add filter/sort to product grid"
"Implement countdown timer"
"Add progress indicators"
```

### Optimizations
```markdown
"Reduce bundle size"
"Improve LCP score"
"Add error boundaries"
"Implement retry logic"
"Cache API responses"
```

## Testing Workflow

```bash
# Local testing
npm run dev
# Open http://localhost:5173
# Test on multiple devices

# Build testing
npm run build
npm run preview
# Check production build

# Lighthouse testing
# Open Chrome DevTools → Lighthouse
# Run audit for Performance, Accessibility, SEO

# Cross-browser testing
# Test on: Chrome, Firefox, Safari, Edge
# Mobile: iOS Safari, Chrome Android
```

## Deployment Checklist

```markdown
Pre-deployment:
□ Remove all console.logs
□ Update meta tags
□ Set proper favicon
□ Configure domain/hosting
□ Setup SSL certificate
□ Configure CDN
□ Setup analytics
□ Test contact forms
□ Verify all links
□ Check 404 page

Post-deployment:
□ Verify live site
□ Test forms again
□ Check analytics tracking
□ Monitor performance
□ Setup error tracking
□ Configure backups
```

## Quick Component Patterns

### Responsive Container
```svelte
<div class="container mx-auto px-4 sm:px-6 lg:px-8">
  <!-- Content -->
</div>
```

### Grid Layout
```svelte
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
  <!-- Items -->
</div>
```

### Card Component
```svelte
<div class="bg-white rounded-lg shadow-md p-6 hover:shadow-lg transition-shadow">
  <!-- Card content -->
</div>
```

### Modal Pattern
```svelte
{#if showModal}
  <div class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
    <div class="bg-white rounded-lg p-6 max-w-md w-full">
      <!-- Modal content -->
    </div>
  </div>
{/if}
```

## Error Handling

```svelte
<script>
  let error = null;
  let loading = false;
  
  async function handleSubmit() {
    loading = true;
    error = null;
    
    try {
      const response = await fetch('/api/endpoint');
      if (!response.ok) throw new Error('Failed');
      // Success logic
    } catch (e) {
      error = 'Something went wrong. Please try again.';
    } finally {
      loading = false;
    }
  }
</script>

{#if error}
  <div class="text-red-600">{error}</div>
{/if}
```

## State Management

```javascript
// stores.js
import { writable } from 'svelte/store';

// UI State
export const loading = writable(false);
export const modal = writable(null);
export const notification = writable(null);

// Business Data
export const cart = writable([]);
export const user = writable(null);
export const preferences = writable({
  theme: 'light',
  language: 'en'
});
```

## Quick Wins for Conversion

1. **Above the fold**: Clear value prop + CTA within 3 seconds
2. **Social proof**: Testimonials, reviews, client logos
3. **Urgency**: Limited time offers, stock indicators
4. **Trust signals**: Security badges, guarantees, certifications
5. **Reduce friction**: Minimal form fields, guest checkout
6. **Mobile first**: 60%+ traffic is mobile
7. **Page speed**: Every second delay = 7% conversion drop

## Common Issues & Solutions

```markdown
Issue: "Slow page load"
→ Check image sizes, lazy load, check bundle size

Issue: "Form not working"
→ Check network tab, verify endpoint, check CORS

Issue: "Layout broken on mobile"
→ Check responsive classes, test viewport widths

Issue: "Animations janky"
→ Use transform not position, add will-change

Issue: "SEO not working"
→ Check meta tags, add structured data, sitemap
```

## Claude Code Tips

1. **Be specific**: "Add testimonial slider with 3 cards visible on desktop, 1 on mobile"
2. **Provide context**: Share current code when asking for modifications
3. **Batch requests**: Group related changes together
4. **Test incrementally**: Run dev server after each major change
5. **Use examples**: "Make it like Stripe's pricing section"

## File Size Limits

- Components: < 150 lines
- JSON data: < 100KB
- Images: < 200KB (optimize with TinyPNG)
- Total bundle: < 500KB initial load
- Fonts: Max 2 families, 4 weights total

## Environment Setup

### Initial Project Setup
```bash
# Clone or create new project
git clone [repo-url] project-name
cd project-name

# Install dependencies
npm install

# Create environment files
touch .env.development .env.production

# Initialize Tailwind (if needed)
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

### Environment Variables
```bash
# .env.development
VITE_API_URL=http://localhost:3000
VITE_PUBLIC_URL=http://localhost:5173
VITE_ANALYTICS_ID=UA-XXXXXX-X
VITE_FORM_ENDPOINT=/.netlify/functions/contact

# .env.production  
VITE_API_URL=https://api.yourdomain.com
VITE_PUBLIC_URL=https://yourdomain.com
VITE_ANALYTICS_ID=UA-XXXXXX-X
VITE_FORM_ENDPOINT=https://formspree.io/f/YOUR_ID
```

### VS Code Settings
```json
// .vscode/settings.json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "[svelte]": {
    "editor.defaultFormatter": "svelte.svelte-vscode"
  },
  "tailwindCSS.experimental.classRegex": [
    ["class([^]*)", "[\"'`]([^\"'`]*).*?[\"'`]"]
  ]
}
```

### Required VS Code Extensions
```markdown
- Svelte for VS Code
- Tailwind CSS IntelliSense
- Prettier
- ESLint
- GitLens
```

## Security Best Practices

### Input Sanitization
```svelte
<script>
  import DOMPurify from 'dompurify';
  
  function sanitizeInput(input) {
    return DOMPurify.sanitize(input, { 
      ALLOWED_TAGS: [],
      ALLOWED_ATTR: []
    });
  }
  
  function handleUserInput(event) {
    const clean = sanitizeInput(event.target.value);
    // Use sanitized input
  }
</script>
```

### Content Security Policy
```html
<!-- index.html -->
<meta http-equiv="Content-Security-Policy" 
  content="default-src 'self'; 
    script-src 'self' 'unsafe-inline' https://cdn.jsdelivr.net; 
    style-src 'self' 'unsafe-inline'; 
    img-src 'self' data: https:; 
    font-src 'self' data:;">
```

### API Security
```javascript
// Secure API calls
async function secureApiCall(endpoint, data) {
  const headers = {
    'Content-Type': 'application/json',
    'X-Requested-With': 'XMLHttpRequest',
  };
  
  // Add CSRF token if available
  const csrfToken = document.querySelector('meta[name="csrf-token"]')?.content;
  if (csrfToken) headers['X-CSRF-Token'] = csrfToken;
  
  try {
    const response = await fetch(endpoint, {
      method: 'POST',
      headers,
      credentials: 'same-origin',
      body: JSON.stringify(data)
    });
    
    if (!response.ok) throw new Error('API call failed');
    return await response.json();
  } catch (error) {
    console.error('Secure API call failed:', error);
    throw error;
  }
}
```

### Form Security
```svelte
<script>
  // Rate limiting
  let lastSubmit = 0;
  const RATE_LIMIT = 3000; // 3 seconds
  
  async function handleSubmit(event) {
    event.preventDefault();
    
    // Rate limiting
    const now = Date.now();
    if (now - lastSubmit < RATE_LIMIT) {
      error = 'Please wait before submitting again';
      return;
    }
    lastSubmit = now;
    
    // Honeypot field check
    if (event.target.honeypot.value) {
      // Bot detected
      return;
    }
    
    // Process form...
  }
</script>

<form on:submit={handleSubmit}>
  <!-- Honeypot field (hidden from users) -->
  <input type="text" name="honeypot" style="display:none" tabindex="-1" autocomplete="off">
  
  <!-- Real fields -->
  <input type="email" name="email" required>
  <button type="submit">Submit</button>
</form>
```

## Advanced Patterns

### Debounce & Throttle
```javascript
// utils/timing.js
export function debounce(func, wait) {
  let timeout;
  return function executedFunction(...args) {
    const later = () => {
      clearTimeout(timeout);
      func(...args);
    };
    clearTimeout(timeout);
    timeout = setTimeout(later, wait);
  };
}

export function throttle(func, limit) {
  let inThrottle;
  return function(...args) {
    if (!inThrottle) {
      func.apply(this, args);
      inThrottle = true;
      setTimeout(() => inThrottle = false, limit);
    }
  };
}

// Usage in component
import { debounce, throttle } from '$lib/utils/timing';

const handleSearch = debounce((value) => {
  // Search logic
}, 300);

const handleScroll = throttle(() => {
  // Scroll logic
}, 100);
```

### Intersection Observer Hook
```javascript
// hooks/useIntersectionObserver.js
import { onMount } from 'svelte';

export function useIntersectionObserver(callback, options = {}) {
  let element;
  
  onMount(() => {
    const observer = new IntersectionObserver(callback, {
      threshold: 0.1,
      rootMargin: '50px',
      ...options
    });
    
    if (element) observer.observe(element);
    
    return () => {
      if (element) observer.unobserve(element);
    };
  });
  
  return (node) => {
    element = node;
  };
}
```

### Local Storage Store
```javascript
// stores/localStorage.js
import { writable } from 'svelte/store';

export function localStorageStore(key, initialValue) {
  // Get from localStorage or use initial value
  const storedValue = typeof window !== 'undefined' 
    ? localStorage.getItem(key) 
    : null;
  
  const data = storedValue ? JSON.parse(storedValue) : initialValue;
  const store = writable(data);
  
  // Subscribe to changes and update localStorage
  store.subscribe(value => {
    if (typeof window !== 'undefined') {
      localStorage.setItem(key, JSON.stringify(value));
    }
  });
  
  return store;
}

// Usage
import { localStorageStore } from '$lib/stores/localStorage';
const preferences = localStorageStore('user-preferences', {
  theme: 'light',
  language: 'en'
});
```

### Dynamic Component Loading
```svelte
<script>
  let DynamicComponent;
  
  async function loadComponent(componentName) {
    const module = await import(`./components/${componentName}.svelte`);
    DynamicComponent = module.default;
  }
  
  // Load based on condition
  $: if (userType === 'premium') {
    loadComponent('PremiumFeatures');
  } else {
    loadComponent('BasicFeatures');
  }
</script>

{#if DynamicComponent}
  <svelte:component this={DynamicComponent} />
{/if}
```

## Utility Functions

### Format Utilities
```javascript
// utils/format.js
export const formatCurrency = (amount, currency = 'USD') => {
  return new Intl.NumberFormat('en-US', {
    style: 'currency',
    currency
  }).format(amount);
};

export const formatDate = (date, format = 'short') => {
  const options = format === 'short' 
    ? { month: 'short', day: 'numeric', year: 'numeric' }
    : { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
  
  return new Date(date).toLocaleDateString('en-US', options);
};

export const formatPhoneNumber = (phone) => {
  const cleaned = phone.replace(/\D/g, '');
  const match = cleaned.match(/^(\d{3})(\d{3})(\d{4})$/);
  return match ? `(${match[1]}) ${match[2]}-${match[3]}` : phone;
};

export const truncateText = (text, maxLength = 100) => {
  if (text.length <= maxLength) return text;
  return text.slice(0, maxLength).trim() + '...';
};
```

### Validation Utilities
```javascript
// utils/validation.js
export const validators = {
  email: (value) => {
    const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return regex.test(value) || 'Invalid email address';
  },
  
  phone: (value) => {
    const regex = /^[\d\s\-\+\(\)]+$/;
    return regex.test(value) || 'Invalid phone number';
  },
  
  required: (value) => {
    return (value && value.length > 0) || 'This field is required';
  },
  
  minLength: (min) => (value) => {
    return (value && value.length >= min) || `Minimum ${min} characters required`;
  },
  
  maxLength: (max) => (value) => {
    return (!value || value.length <= max) || `Maximum ${max} characters allowed`;
  },
  
  url: (value) => {
    try {
      new URL(value);
      return true;
    } catch {
      return 'Invalid URL';
    }
  }
};

// Usage
function validateForm(formData) {
  const errors = {};
  
  const emailError = validators.email(formData.email);
  if (emailError !== true) errors.email = emailError;
  
  const phoneError = validators.phone(formData.phone);
  if (phoneError !== true) errors.phone = phoneError;
  
  return errors;
}
```

## Animation Utilities

### Scroll Animations
```javascript
// utils/animations.js
import { spring } from 'svelte/motion';

export function parallax(node, { speed = 0.5 } = {}) {
  let scrollY = 0;
  
  function handleScroll() {
    scrollY = window.scrollY;
    const offset = scrollY * speed;
    node.style.transform = `translateY(${offset}px)`;
  }
  
  window.addEventListener('scroll', handleScroll);
  
  return {
    destroy() {
      window.removeEventListener('scroll', handleScroll);
    }
  };
}

export function fadeInOnScroll(node, { 
  threshold = 0.1, 
  rootMargin = '50px' 
} = {}) {
  const observer = new IntersectionObserver(
    entries => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          node.classList.add('fade-in');
          observer.unobserve(node);
        }
      });
    },
    { threshold, rootMargin }
  );
  
  observer.observe(node);
  
  return {
    destroy() {
      observer.disconnect();
    }
  };
}
```

### CSS Animation Classes
```css
/* app.css additions */
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes slideIn {
  from { transform: translateX(-100%); }
  to { transform: translateX(0); }
}

@keyframes pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.05); }
}

.fade-in { animation: fadeIn 0.6s ease-out forwards; }
.slide-in { animation: slideIn 0.4s ease-out forwards; }
.pulse { animation: pulse 2s infinite; }
```

## Browser Compatibility

### Feature Detection
```javascript
// utils/browser.js
export const browserFeatures = {
  webp: () => {
    const canvas = document.createElement('canvas');
    canvas.width = canvas.height = 1;
    return canvas.toDataURL('image/webp').indexOf('image/webp') === 0;
  },
  
  intersectionObserver: () => 'IntersectionObserver' in window,
  
  smoothScroll: () => 'scrollBehavior' in document.documentElement.style,
  
  clipboard: () => navigator.clipboard !== undefined,
  
  webgl: () => {
    try {
      const canvas = document.createElement('canvas');
      return !!(window.WebGLRenderingContext && 
        (canvas.getContext('webgl') || canvas.getContext('experimental-webgl')));
    } catch(e) {
      return false;
    }
  }
};

// Polyfill loading
if (!browserFeatures.smoothScroll()) {
  import('smoothscroll-polyfill').then(module => {
    module.polyfill();
  });
}
```

## Debugging Tools

### Console Helpers
```javascript
// utils/debug.js
export const debug = {
  log: (...args) => {
    if (import.meta.env.DEV) {
      console.log('[DEBUG]', ...args);
    }
  },
  
  table: (data) => {
    if (import.meta.env.DEV) {
      console.table(data);
    }
  },
  
  time: (label) => {
    if (import.meta.env.DEV) {
      console.time(label);
    }
  },
  
  timeEnd: (label) => {
    if (import.meta.env.DEV) {
      console.timeEnd(label);
    }
  },
  
  trace: () => {
    if (import.meta.env.DEV) {
      console.trace();
    }
  }
};

// Performance monitoring
export function measurePerformance(name, fn) {
  if (import.meta.env.DEV) {
    performance.mark(`${name}-start`);
    const result = fn();
    performance.mark(`${name}-end`);
    performance.measure(name, `${name}-start`, `${name}-end`);
    
    const measure = performance.getEntriesByName(name)[0];
    console.log(`${name} took ${measure.duration.toFixed(2)}ms`);
    
    return result;
  }
  return fn();
}
```

## Package.json Scripts

```json
{
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "check": "svelte-check --tsconfig ./jsconfig.json",
    "lint": "eslint --ext .js,.svelte src",
    "format": "prettier --write src/**/*.{js,svelte,css}",
    "test": "vitest",
    "test:ui": "vitest --ui",
    "analyze": "npx vite-bundle-visualizer",
    "clean": "rm -rf dist node_modules package-lock.json && npm install"
  }
}
```

## Tailwind Configuration

```javascript
// tailwind.config.js
module.exports = {
  content: ['./src/**/*.{html,js,svelte,ts}'],
  theme: {
    extend: {
      colors: {
        primary: {
          DEFAULT: '#2563eb',
          dark: '#1d4ed8',
          light: '#3b82f6'
        },
        secondary: {
          DEFAULT: '#10b981',
          dark: '#059669',
          light: '#34d399'
        }
      },
      fontFamily: {
        sans: ['Inter', 'system-ui', 'sans-serif'],
        display: ['Poppins', 'system-ui', 'sans-serif']
      },
      animation: {
        'fade-in': 'fadeIn 0.5s ease-in-out',
        'slide-up': 'slideUp 0.3s ease-out',
        'bounce-slow': 'bounce 2s infinite'
      }
    }
  },
  plugins: [
    require('@tailwindcss/forms'),
    require('@tailwindcss/typography'),
    require('@tailwindcss/aspect-ratio')
  ]
}
```

## Vite Configuration

```javascript
// vite.config.js
import { defineConfig } from 'vite';
import { svelte } from '@sveltejs/vite-plugin-svelte';
import path from 'path';

export default defineConfig({
  plugins: [
    svelte({
      compilerOptions: {
        dev: process.env.NODE_ENV !== 'production'
      }
    })
  ],
  resolve: {
    alias: {
      '$lib': path.resolve('./src/lib'),
      '$components': path.resolve('./src/components'),
      '$utils': path.resolve('./src/utils'),
      '$stores': path.resolve('./src/stores')
    }
  },
  build: {
    rollupOptions: {
      output: {
        manualChunks: {
          'vendor': ['svelte'],
          'utils': ['./src/utils/index.js']
        },
        assetFileNames: (assetInfo) => {
          const extType = assetInfo.name.split('.').at(1);
          if (/png|jpe?g|svg|gif|tiff|bmp|ico/i.test(extType)) {
            return `assets/images/[name]-[hash][extname]`;
          }
          if (/woff|woff2|eot|ttf|otf/i.test(extType)) {
            return `assets/fonts/[name]-[hash][extname]`;
          }
          return `assets/[name]-[hash][extname]`;
        }
      }
    },
    cssCodeSplit: true,
    sourcemap: true,
    minify: 'terser',
    terserOptions: {
      compress: {
        drop_console: true,
        drop_debugger: true
      }
    }
  },
  server: {
    port: 5173,
    strictPort: false,
    open: true,
    cors: true,
    hmr: {
      overlay: true
    }
  },
  preview: {
    port: 4173,
    strictPort: false,
    open: true
  }
});
```

## Hosting Configurations

### Netlify
```toml
# netlify.toml
[build]
  command = "npm run build"
  publish = "dist"

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200

[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "DENY"
    X-Content-Type-Options = "nosniff"
    X-XSS-Protection = "1; mode=block"
    Content-Security-Policy = "default-src 'self'"
```

### Vercel
```json
// vercel.json
{
  "buildCommand": "npm run build",
  "outputDirectory": "dist",
  "framework": "vite",
  "rewrites": [
    { "source": "/(.*)", "destination": "/index.html" }
  ]
}
```

### Docker
```dockerfile
# Dockerfile
FROM node:18-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```
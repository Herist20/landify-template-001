# Property Company Landing Page Template

A professional and modern landing page template for property/real estate companies built with Svelte. This template features a clean design, responsive layout, and fully editable content through JSON configuration.

## Features

- **Fully Editable Content**: All text, images, and data are configurable through a single JSON file
- **Responsive Design**: Mobile-first approach that looks great on all devices
- **Modern UI Components**: Professional design with smooth animations and interactions
- **Complete Sections**:
  - Navigation Header with contact info
  - Hero section with statistics
  - Featured Properties showcase
  - Services overview
  - About Us section
  - Client Testimonials
  - Contact form with map
  - Footer with newsletter signup

## Installation

1. Install dependencies:
```bash
npm install
```

2. Run the development server:
```bash
npm run dev
```

3. Open your browser and navigate to `http://localhost:5173`

## Customization

### Editing Content

All content is stored in `src/data/siteContent.json`. Simply edit this file to customize:

- Company information (name, logo, contact details)
- Navigation menu items
- Hero section content and statistics
- Property listings
- Services offered
- About section content
- Testimonials
- Contact form labels
- Footer content and social links

### Example: Changing Company Name

```json
{
  "company": {
    "name": "Your Company Name",
    "phone": "+1 (555) 987-6543",
    "email": "info@yourcompany.com"
  }
}
```

### Example: Adding a New Property

```json
{
  "featuredProperties": {
    "properties": [
      {
        "id": 7,
        "title": "New Property Title",
        "location": "Property Location",
        "price": "$500,000",
        "beds": 3,
        "baths": 2,
        "area": "1,500 sq ft",
        "image": "https://your-image-url.com",
        "type": "For Sale",
        "featured": true
      }
    ]
  }
}
```

### Styling

The main styles are in `src/app.css`. CSS variables are used for easy theme customization:

```css
:root {
  --primary-color: #2563eb;  /* Main brand color */
  --secondary-color: #10b981; /* Accent color */
  --text-primary: #1f2937;    /* Main text color */
  --text-secondary: #6b7280;  /* Secondary text color */
}
```

## Building for Production

```bash
npm run build
```

The built files will be in the `dist` directory, ready to be deployed to any static hosting service.

## Technologies Used

- **Svelte**: Fast and efficient component framework
- **Vite**: Modern build tool for fast development
- **Lucide Icons**: Beautiful open-source icons

## Project Structure

```
├── src/
│   ├── components/        # Svelte components
│   │   ├── Header.svelte
│   │   ├── Hero.svelte
│   │   ├── FeaturedProperties.svelte
│   │   ├── Services.svelte
│   │   ├── About.svelte
│   │   ├── Testimonials.svelte
│   │   ├── Contact.svelte
│   │   └── Footer.svelte
│   ├── data/
│   │   └── siteContent.json  # All editable content
│   ├── App.svelte            # Main app component
│   ├── main.js               # App entry point
│   └── app.css               # Global styles
├── index.html
├── package.json
└── vite.config.js
```

## License

This template is free to use for both personal and commercial projects.

## Support

For any questions or issues, please create an issue in the repository.
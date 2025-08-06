# Photography Portfolio Website

A modern, responsive photography website to showcase your photos organized by year and location.

## Features

- **Responsive Design**: Works perfectly on desktop, tablet, and mobile devices
- **Photo Gallery**: Beautiful grid layout with hover effects
- **Year-Location Filtering**: Filter photos by year and/or location
- **Individual Photo Pages**: Click any photo to view it on a dedicated page with details
- **Social Media Links**: Connect with visitors through social media platforms
- **Modern UI**: Clean, professional design with smooth animations
- **Mobile Navigation**: Hamburger menu for mobile devices
- **Smooth Scrolling**: Smooth navigation between sections
- **Keyboard Navigation**: Use arrow keys for navigation on photo pages

## Getting Started

1. **Open the website**: Simply open `index.html` in your web browser
2. **View the gallery**: Scroll down to see the photo gallery
3. **Filter photos**: Use the dropdown menus to filter by year or location
4. **View photos**: Click on any photo to open its dedicated page with details
5. **Connect**: Use the social media links in the hero section to connect

## Customizing Your Photos

### Adding Your Own Photos

To add your own photos, edit the `photos` array in `script.js`:

```javascript
const photos = [
    {
        id: 1,
        title: "Your Photo Title",
        location: "Location Name",
        year: 2024,
        image: "path/to/your/photo.jpg",
        description: "Description of your photo"
    },
    // Add more photos here...
];
```

### Photo Object Properties

- `id`: Unique identifier for the photo
- `title`: The title of your photo
- `location`: Where the photo was taken
- `year`: When the photo was taken
- `image`: URL or path to your photo file
- `description`: Optional description of the photo

### Supported Image Formats

- JPEG (.jpg, .jpeg)
- PNG (.png)
- WebP (.webp)
- GIF (.gif)

### Image Optimization Tips

1. **Resize your photos**: For web display, 1200px width is usually sufficient
2. **Compress images**: Use tools like TinyPNG or ImageOptim to reduce file size
3. **Use consistent aspect ratios**: For best results, use similar aspect ratios
4. **Organize by folders**: Create folders like `photos/2024/paris/` for better organization

## File Structure

```
photography-website/
├── index.html          # Main HTML file
├── styles.css          # CSS styles
├── script.js           # JavaScript functionality
├── README.md           # This file
└── photos/             # Your photo folder (create this)
    ├── 2024/
    │   ├── paris/
    │   └── tokyo/
    └── 2023/
        ├── newyork/
        └── london/
```

## Customization Options

### Changing Colors

Edit the CSS variables in `styles.css`:

```css
:root {
    --primary-color: #3498db;
    --secondary-color: #2c3e50;
    --accent-color: #667eea;
}
```

### Changing Fonts

Replace the Google Fonts link in `index.html`:

```html
<link href="https://fonts.googleapis.com/css2?family=Your+Font:wght@300;400;500;600;700&display=swap" rel="stylesheet">
```

### Modifying Layout

- **Grid columns**: Change `grid-template-columns` in `.gallery-grid`
- **Spacing**: Adjust `gap` and `padding` values
- **Card size**: Modify `minmax(300px, 1fr)` in the grid

## Browser Compatibility

- Chrome 60+
- Firefox 55+
- Safari 12+
- Edge 79+

## Performance Tips

1. **Optimize images**: Compress and resize your photos
2. **Use lazy loading**: Images load as you scroll (already implemented)
3. **CDN for fonts**: Google Fonts are loaded from CDN
4. **Minimize HTTP requests**: Combine CSS and JS files for production

## Deployment

### Local Development

Simply open `index.html` in your browser or use a local server:

```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx serve .

# Using PHP
php -S localhost:8000
```

### Web Hosting

Upload all files to your web hosting provider:
- `index.html`
- `styles.css`
- `script.js`
- Your photo files

### GitHub Pages

1. Create a GitHub repository
2. Upload your files
3. Enable GitHub Pages in repository settings
4. Your site will be available at `https://username.github.io/repository-name`

## Troubleshooting

### Photos Not Loading
- Check file paths are correct
- Ensure image files exist
- Verify image URLs are accessible

### Filters Not Working
- Check browser console for JavaScript errors
- Ensure photo data format is correct
- Verify filter elements exist in HTML

### Mobile Issues
- Test on actual mobile devices
- Check viewport meta tag is present
- Verify touch events are working

## License

This project is open source and available under the MIT License.

## Support

If you need help customizing your photography website, feel free to:
1. Check the browser console for errors
2. Verify all file paths are correct
3. Test with a simple photo first
4. Ensure your web server supports the file types you're using

## Future Enhancements

Potential features you could add:
- Photo categories/tags
- Search functionality
- Slideshow mode
- Social media sharing
- Photo download links
- EXIF data display
- Map integration
- Blog section
- Contact form 
# Personal Website

A responsive personal website template featuring a profile section, social links, contact information, and a projects showcase.

## Features

- Clean, modern design
- Fully responsive layout for mobile and desktop
- Profile section with image and social links
- Contact information section with clickable email, phone, and location (copy to clipboard on click) and timezone (with live clock)
- Projects showcase with screenshots, GitHub and demo links
- Easy to customize

## Structure

- `index.html` - Main HTML file with the website structure
- `styles.css` - CSS styling for the website

## How to Use

1. Clone or download this repository
2. Open `index.html` in your web browser to view the website
3. Customize the content by editing the HTML file:
   - Replace the placeholder profile image with your own
   - Update your name, tagline, and contact information
   - Add your own projects with descriptions and links
   - Update the social media links to point to your profiles

## Customization

### Profile Image

Replace the placeholder image URL in `index.html`:

```html
<img src="https://via.placeholder.com/150" alt="Profile Picture">
```

with the path to your own image:

```html
<img src="path/to/your/image.jpg" alt="Profile Picture">
```

### Personal Information

Update the name, tagline, and contact information in the HTML file:

```html
<h1>Your Name</h1>
<p class="tagline">Web Developer & Designer</p>
```

Update your contact information, including email, phone, location, and timezone:

```html
<div class="contact-item" onclick="copyToClipboard('your.email@example.com')">
    <i class="fas fa-envelope"></i>
    <p class="copyable" data-tooltip="Click to copy">your.email@example.com</p>
</div>
<div class="contact-item" onclick="copyToClipboard('Your phone number')">
    <i class="fas fa-phone"></i>
    <p class="copyable" data-tooltip="Click to copy">Your phone number</p>
</div>
<div class="contact-item" onclick="copyToClipboard('Your City, Country')">
    <i class="fas fa-map-marker-alt"></i>
    <p class="copyable" data-tooltip="Click to copy">Your City, Country</p>
</div>
<div class="contact-item">
    <i class="fas fa-clock"></i>
    <p>Your Timezone (UTC+/-) <span id="current-time"></span></p>
</div>
```

The email, phone, and location information are clickable and will copy the text to the clipboard when clicked. A tooltip will appear to indicate that the text can be copied, and will change to "Copied!" when the text is successfully copied.

#### Clickable Contact Information

The contact information (email, phone, and location) is clickable and will copy the text to the clipboard when clicked. This is implemented using the following JavaScript function:

```javascript
function copyToClipboard(text) {
    navigator.clipboard.writeText(text).then(() => {
        // Show feedback
        const elements = document.querySelectorAll('.copyable');
        elements.forEach(el => {
            if (el.textContent === text) {
                el.setAttribute('data-tooltip', 'Copied!');
                el.classList.add('copied');

                // Reset after 2 seconds
                setTimeout(() => {
                    el.setAttribute('data-tooltip', 'Click to copy');
                    el.classList.remove('copied');
                }, 2000);
            }
        });
    }).catch(err => {
        console.error('Failed to copy text: ', err);
    });
}
```

This function:
1. Copies the text to the clipboard using the Clipboard API
2. Provides visual feedback by changing the tooltip text to "Copied!" and adding a "copied" class to the element
3. Resets the tooltip and removes the "copied" class after 2 seconds

#### Live Clock

The website includes a live clock that shows your current local time next to the timezone information. The clock updates automatically every second.

The JavaScript code that powers the live clock is located at the bottom of the `index.html` file:

```javascript
function updateClock() {
    const now = new Date();
    const timeString = now.toLocaleTimeString();
    document.getElementById('current-time').textContent = ' - ' + timeString;
}

// Update the clock immediately
updateClock();

// Update the clock every second
setInterval(updateClock, 1000);
```

You can customize the time format by modifying the `toLocaleTimeString()` method. For example, to use 24-hour format:

```javascript
const timeString = now.toLocaleTimeString('en-US', { hour12: false });
```

### Social Links

Update the social media links with your own profiles:

```html
<div class="social-links">
    <a href="https://yourwebsite.com" target="_blank" title="Personal Website"><i class="fas fa-globe"></i></a>
    <a href="https://linkedin.com/in/yourprofile" target="_blank" title="LinkedIn"><i class="fab fa-linkedin"></i></a>
    <a href="https://github.com/yourusername" target="_blank" title="GitHub"><i class="fab fa-github"></i></a>
</div>
```

### Projects

Add or modify projects in the projects section:

```html
<div class="project-card">
    <h3>Your Project Name</h3>
    <div class="project-screenshot">
        <img src="path/to/your/screenshot.jpg" alt="Project Screenshot">
    </div>
    <p>Description of your project.</p>
    <div class="project-links">
        <a href="https://github.com/yourusername/project" target="_blank" class="btn"><i class="fab fa-github"></i> GitHub</a>
        <a href="https://project-demo.com" target="_blank" class="btn"><i class="fas fa-external-link-alt"></i> Live Demo</a>
    </div>
</div>
```

#### Project Screenshots

Each project should include a screenshot. Replace the placeholder image with your own project screenshot:

```html
<div class="project-screenshot">
    <img src="https://via.placeholder.com/800x450" alt="Project Screenshot">
</div>
```

For best results:
- Use screenshots with a 16:9 aspect ratio (e.g., 800x450 pixels)
- Use high-quality images that clearly show your project's interface
- Optimize images for web to keep file sizes small

## Styling Customization

To change the color scheme or other styling aspects, edit the `styles.css` file. The primary color is defined as `#3498db` and can be changed throughout the file to match your preferred color scheme.

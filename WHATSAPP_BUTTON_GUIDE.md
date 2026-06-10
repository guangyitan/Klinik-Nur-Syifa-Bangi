# WhatsApp Floating Button Implementation Guide

This guide explains how to implement the floating WhatsApp button used in this project.

## Overview

The floating WhatsApp button is a fixed-position button that appears in the bottom-right corner of the screen with a pulsing wave animation to attract attention. It links directly to WhatsApp with a pre-filled message.

## Dependencies

- **FontAwesome** (for the WhatsApp icon)
  - Include in your HTML: `<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">`

## HTML Structure

Place this code at the end of your `<body>` tag, before any closing scripts:

```html
<!-- Floating WhatsApp Button -->
<a href="https://wa.me/YOUR_PHONE_NUMBER?text=YOUR_PRE-FILLED_MESSAGE"
   target="_blank"
   class="whatsapp-button ws-wave-animation"
   aria-label="Chat on WhatsApp">
    <i class="fab fa-whatsapp"></i>
</a>
```

### Customization

Replace the following values:

- `YOUR_PHONE_NUMBER` - Your WhatsApp number in international format (e.g., `60122787387`)
- `YOUR_PRE-FILLED_MESSAGE` - URL-encoded pre-filled message (e.g., `Hi%2C%20I%20am%20interested%20in%20your%20product`)

Example with real values:
```html
<a href="https://wa.me/60122787387?text=Hi%2C%20I%20am%20interested%20in%20your%20product.%20May%20I%20speak%20to%20a%20sales%20consultant%3F"
   target="_blank"
   class="whatsapp-button ws-wave-animation"
   aria-label="Chat on WhatsApp">
    <i class="fab fa-whatsapp"></i>
</a>
```

## CSS Implementation

### Option 1: Scoped Version (with prefix)

Use this if you want to scope the styles to a specific container (e.g., `#ybk-page`):

```css
/** WhatsApp Button **/
#ybk-page .whatsapp-button {
  position: fixed;
  bottom: 20px;
  right: 20px;
  z-index: 9999;
  background-color: #198754;
  color: white;
  border-radius: 50%;
  width: 80px;
  height: 80px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 36px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
  text-decoration: none !important;
}

@media (min-width: 768px) {
  #ybk-page .whatsapp-button {
    width: 120px;
    height: 120px;
    font-size: 48px;
    bottom: 30px;
    right: 30px;
  }
}

#ybk-page .ws-wave-animation {
  animation: wsPulseWave 2s infinite;
}

@keyframes wsPulseWave {
  0% {
    box-shadow: 0 0 0 0 rgba(25, 135, 84, 0.7);
  }
  70% {
    box-shadow: 0 0 0 15px rgba(25, 135, 84, 0);
  }
  100% {
    box-shadow: 0 0 0 0 rgba(25, 135, 84, 0);
  }
}
```

### Option 2: Global Version (without prefix)

Use this if you want to use the button without a container prefix:

```css
/** WhatsApp Button **/
.whatsapp-button {
  position: fixed;
  bottom: 20px;
  right: 20px;
  z-index: 9999;
  background-color: #198754;
  color: white;
  border-radius: 50%;
  width: 80px;
  height: 80px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 36px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
  text-decoration: none !important;
}

@media (min-width: 768px) {
  .whatsapp-button {
    width: 120px;
    height: 120px;
    font-size: 48px;
    bottom: 30px;
    right: 30px;
  }
}

.ws-wave-animation {
  animation: wsPulseWave 2s infinite;
}

@keyframes wsPulseWave {
  0% {
    box-shadow: 0 0 0 0 rgba(25, 135, 84, 0.7);
  }
  70% {
    box-shadow: 0 0 0 15px rgba(25, 135, 84, 0);
  }
  100% {
    box-shadow: 0 0 0 0 rgba(25, 135, 84, 0);
  }
}
```

## Customization Options

### Change Button Color

Modify the `background-color` and the animation color (in `rgba`):

```css
.whatsapp-button {
  background-color: #YOUR_COLOR; /* Main button color */
}

@keyframes wsPulseWave {
  0% {
    box-shadow: 0 0 0 0 rgba(R, G, B, 0.7); /* RGB of your color */
  }
  70% {
    box-shadow: 0 0 0 15px rgba(R, G, B, 0);
  }
  100% {
    box-shadow: 0 0 0 0 rgba(R, G, B, 0);
  }
}
```

### Change Button Size

Modify the `width`, `height`, and `font-size`:

```css
.whatsapp-button {
  width: 60px;  /* Your desired width */
  height: 60px; /* Your desired height */
  font-size: 28px; /* Adjust icon size proportionally */
}
```

### Change Position

Modify `bottom` and `right` values:

```css
.whatsapp-button {
  bottom: 20px; /* Distance from bottom */
  right: 20px;  /* Distance from right */
}
```

To move to bottom-left:
```css
.whatsapp-button {
  bottom: 20px;
  left: 20px;
  right: auto;
}
```

### Remove Animation

Simply remove the `ws-wave-animation` class from the HTML or remove the animation CSS.

### Adjust Animation Speed

Modify the animation duration:

```css
.ws-wave-animation {
  animation: wsPulseWave 3s infinite; /* Change 2s to desired duration */
}
```

## Responsive Behavior

The button has two breakpoints:

- **Mobile (< 768px)**: 80px × 80px, 36px icon, 20px from edges
- **Desktop (≥ 768px)**: 120px × 120px, 48px icon, 30px from edges

You can adjust these breakpoints in the `@media` query.

## Quick Copy-Paste Implementation

### 1. Add FontAwesome to your HTML head
```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
```

### 2. Add the HTML before closing body tag
```html
<a href="https://wa.me/YOUR_NUMBER?text=YOUR_MESSAGE"
   target="_blank"
   class="whatsapp-button ws-wave-animation"
   aria-label="Chat on WhatsApp">
    <i class="fab fa-whatsapp"></i>
</a>
```

### 3. Add the CSS to your stylesheet
```css
.whatsapp-button {
  position: fixed;
  bottom: 20px;
  right: 20px;
  z-index: 9999;
  background-color: #198754;
  color: white;
  border-radius: 50%;
  width: 80px;
  height: 80px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 36px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
  text-decoration: none !important;
}

@media (min-width: 768px) {
  .whatsapp-button {
    width: 120px;
    height: 120px;
    font-size: 48px;
    bottom: 30px;
    right: 30px;
  }
}

.ws-wave-animation {
  animation: wsPulseWave 2s infinite;
}

@keyframes wsPulseWave {
  0% {
    box-shadow: 0 0 0 0 rgba(25, 135, 84, 0.7);
  }
  70% {
    box-shadow: 0 0 0 15px rgba(25, 135, 84, 0);
  }
  100% {
    box-shadow: 0 0 0 0 rgba(25, 135, 84, 0);
  }
}
```

## Tips

1. **URL Encoding**: When creating the pre-filled message, make sure to URL-encode special characters:
   - Space → `%20`
   - Comma → `%2C`
   - Question mark → `%3F`
   - Use an online URL encoder or encodeURIComponent() in JavaScript

2. **Z-Index**: The button uses `z-index: 9999` to ensure it stays above other content. Adjust if you have elements with higher z-index values.

3. **Accessibility**: The `aria-label="Chat on WhatsApp"` provides screen reader support. Keep this for accessibility.

4. **Performance**: The animation uses CSS transforms which are GPU-accelerated and performant.

5. **Mobile Experience**: On mobile, the button is sized appropriately for touch targets (80px minimum recommended for touch).

## Troubleshooting

- **Button not visible**: Check z-index conflicts with other fixed elements
- **Animation not working**: Ensure the `ws-wave-animation` class is applied
- **Icon not showing**: Verify FontAwesome is loaded correctly
- **Link not opening**: Check that the WhatsApp URL format is correct

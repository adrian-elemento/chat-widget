# Enhanced Chat Widget

A modern, customizable chat widget with user information collection and product selection capabilities. Built with vanilla JavaScript and designed to integrate seamlessly with n8n workflows.

## Features

- 🎨 **Customizable Design**: Fully customizable colors, branding, and positioning
- 👤 **User Information Collection**: Collects user details before starting chat
- 🛍️ **Product Selection**: Allows users to select specific products for targeted support
- 📱 **Responsive Design**: Works on desktop and mobile devices
- 🔗 **n8n Integration**: Built to work seamlessly with n8n webhooks
- ⚡ **Lightweight**: Pure JavaScript implementation with no external dependencies
- 🎯 **Modern UI**: Clean, modern interface with smooth animations

## Quick Start

### 1. Include the Script

Add the chat widget script to your HTML page:

```html
<script src="chat-widget.js"></script>
```

### 2. Configure the Widget

Before the script tag, add your configuration:

```html
<script>
window.ChatWidgetConfig = {
    webhook: {
        url: 'https://your-n8n-instance.com/webhook/your-webhook-id',
        route: 'your-route-name'
    },
    branding: {
        logo: 'https://your-domain.com/logo.png',
        name: 'Your Company Name',
        welcomeText: 'Welcome! How can we help you today?',
        responseTimeText: 'We typically respond within 24 hours',
        poweredBy: {
            text: 'Powered by n8n',
            link: 'https://n8n.partnerlinks.io/m8a94i19zhqq?utm_source=nocodecreative.io'
        }
    },
    style: {
        primaryColor: '#854fff',
        secondaryColor: '#6b3fd4',
        position: 'right', // or 'left'
        backgroundColor: '#ffffff',
        fontColor: '#333333'
    }
};
</script>
<script src="chat-widget.js"></script>
```

## Configuration Options

### Webhook Configuration
- `url`: Your n8n webhook URL
- `route`: Route identifier for your webhook

### Branding Configuration
- `logo`: URL to your company logo
- `name`: Your company name
- `welcomeText`: Welcome message displayed to users
- `responseTimeText`: Response time information
- `poweredBy`: Footer link configuration

### Style Configuration
- `primaryColor`: Primary brand color (hex)
- `secondaryColor`: Secondary brand color (hex)
- `position`: Widget position ('left' or 'right')
- `backgroundColor`: Background color (hex)
- `fontColor`: Text color (hex)

## n8n Integration

The widget sends data to your n8n webhook in the following format:

```json
{
    "action": "sendMessage",
    "sessionId": "unique-session-id",
    "route": "your-route-name",
    "chatInput": "user message",
    "metadata": {
        "userId": "user@email.com",
        "firstName": "John",
        "lastName": "Doe",
        "email": "user@email.com",
        "selectedProduct": "lightspeed-filter",
        "productName": "Lightspeed Filter",
        "timestamp": "2024-01-01T12:00:00.000Z"
    }
}
```

### Expected n8n Response

Your n8n workflow should return a JSON response:

```json
{
    "output": "Bot response message"
}
```

Or for multiple responses:

```json
[
    {
        "output": "First response message"
    },
    {
        "output": "Second response message"
    }
]
```

## Product Selection

The widget includes predefined product options:
- Lightspeed Filter
- Lightspeed Insight
- Lightspeed Alert
- Lightspeed Classroom
- Lightspeed Signal
- Lightspeed MDM

Users can select a specific product or skip the selection for general support.

## Customization

### Adding Custom Products

To add custom products, modify the `dropdown-options` section in the HTML template within the script:

```javascript
<div class="dropdown-options">
    <div class="dropdown-option" data-value="your-product-id">Your Product Name</div>
    // ... existing options
</div>
```

### Styling

The widget uses CSS custom properties for easy theming. You can override any style by setting CSS variables:

```css
.n8n-chat-widget {
    --chat--color-primary: #your-color;
    --chat--color-secondary: #your-secondary-color;
    --chat--color-background: #your-background;
    --chat--color-font: #your-font-color;
}
```

## Browser Support

- Chrome 60+
- Firefox 55+
- Safari 12+
- Edge 79+

## License

This project is open source and available under the [MIT License](LICENSE).

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Support

For support and questions, please open an issue on GitHub.

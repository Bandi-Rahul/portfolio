# Portfolio Website with Email Functionality

A modern, responsive portfolio website for Rahul Bandi with integrated email contact form functionality.

![preview img](/preview.png)

## Features

- ✨ Modern, responsive design
- 📧 Working contact form with email notifications
- 🎨 Smooth animations and transitions
- 📱 Mobile-first approach
- ⚡ Fast loading and optimized performance
- 🔗 Social media integration

## Email Setup Instructions

To enable the contact form email functionality, you need to set up EmailJS:

### Step 1: Create EmailJS Account

1. Go to [EmailJS](https://www.emailjs.com/)
2. Sign up for a free account
3. Verify your email address

### Step 2: Create Email Service

1. In your EmailJS dashboard, go to "Email Services"
2. Click "Add New Service"
3. Choose your email provider (Gmail, Outlook, etc.)
4. Follow the setup instructions for your chosen provider
5. Note down your **Service ID**

### Step 3: Create Email Template

1. Go to "Email Templates" in your dashboard
2. Click "Create New Template"
3. Use this template structure:

```
Subject: New Contact Form Submission from {{from_name}}

Hello {{to_name}},

You have received a new message from your portfolio website:

Name: {{from_name}}
Email: {{from_email}}
Subject: {{subject}}

Message:
{{message}}

---
This message was sent from your portfolio contact form.
```

4. Save the template and note down your **Template ID**

### Step 4: Get Public Key

1. Go to "Account" > "General"
2. Find your **Public Key**

### Step 5: Update JavaScript File

Open `assets/js/main.js` and replace the placeholders:

```javascript
// Replace this line:
emailjs.init("YOUR_PUBLIC_KEY");
// With your actual public key:
emailjs.init("your_actual_public_key_here");

// Replace these in the emailjs.send function:
emailjs.send('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', templateParams)
// With your actual IDs:
emailjs.send('your_service_id', 'your_template_id', templateParams)
```

### Step 6: Test the Contact Form

1. Open your website
2. Fill out the contact form
3. Submit the form
4. Check if you receive the email
5. Verify the thank you page redirection works

## File Structure

```
portfolio/
├── index.html              # Main portfolio page
├── thank-you.html          # Thank you page after form submission
├── assets/
│   ├── css/
│   │   └── styles.css      # Main stylesheet
│   ├── js/
│   │   └── main.js         # JavaScript functionality
│   ├── img/               # Images and photos
│   └── scss/              # SCSS source files (optional)
├── README.md              # This file
└── preview.png           # Website preview
```

## Customization

### Update Contact Information

In `index.html`, update the contact details:

```html
<div class="contact__detail">
    <i class='bx bx-envelope contact__icon'></i>
    <span>your.email@example.com</span> <!-- Update this -->
</div>
```

### Update Social Media Links

Update the social media links in both `index.html` and `thank-you.html`:

```html
<a href="https://www.linkedin.com/in/your-profile/" class="footer__icon">
<a href="https://www.instagram.com/your-profile/" class="footer__icon">
<a href="https://github.com/your-username" class="footer__icon">
```

## Technologies Used

- HTML5
- CSS3
- JavaScript (ES6+)
- EmailJS for email functionality
- BoxIcons for icons
- ScrollReveal for animations

## Deployment

This is a static website that can be deployed to:

- **GitHub Pages**: Push to a GitHub repository and enable Pages
- **Netlify**: Drag and drop the folder or connect to Git
- **Vercel**: Import from Git repository
- **Any web hosting service**: Upload files via FTP

**Note**: Remember to replace all placeholder values (YOUR_PUBLIC_KEY, YOUR_SERVICE_ID, YOUR_TEMPLATE_ID) with your actual EmailJS credentials for the contact form to work properly.


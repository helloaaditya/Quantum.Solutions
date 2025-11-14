# EmailJS Setup Instructions

To make the contact form work and send emails to your inbox, you need to set up EmailJS (free service).

## Step 1: Create EmailJS Account
1. Go to https://www.emailjs.com/
2. Sign up for a free account (allows 200 emails/month for free)
3. Verify your email address

## Step 2: Create Email Service
1. Go to "Email Services" in your EmailJS dashboard
2. Click "Add New Service"
3. Choose "Gmail" (or your email provider)
4. Connect your Gmail account (aadityakum123@gmail.com)
5. Copy the **Service ID** (e.g., `service_xxxxx`)

## Step 3: Create Email Template
1. Go to "Email Templates" in your EmailJS dashboard
2. Click "Create New Template"
3. Use this template:

**Template Name:** Contact Form

**Subject:** New Contact Form Submission - {{subject}}

**Content:**
```
From: {{from_name}}
Email: {{from_email}}
Subject: {{subject}}

Message:
{{message}}

---
This email was sent from your Quantum Solution portfolio contact form.
```

4. Copy the **Template ID** (e.g., `template_xxxxx`)

## Step 4: Get Public Key
1. Go to "Account" → "General" in your EmailJS dashboard
2. Copy your **Public Key** (e.g., `xxxxxxxxxxxxx`)

## Step 5: Update script.js
Open `script.js` and replace these placeholders:

1. Replace `YOUR_PUBLIC_KEY` with your EmailJS Public Key (line 174)
2. Replace `YOUR_SERVICE_ID` with your Service ID (line 200)
3. Replace `YOUR_TEMPLATE_ID` with your Template ID (line 200)

**Example:**
```javascript
emailjs.init("abc123xyz456"); // Your Public Key

emailjs.send('service_abc123', 'template_xyz789', formData)
```

## Step 6: Test the Form
1. Open your website
2. Fill out the contact form
3. Submit it
4. Check your email (aadityakum123@gmail.com) for the message

## Alternative: Use Formspree (Easier Option)
If you prefer a simpler setup without EmailJS:

1. Go to https://formspree.io/
2. Sign up for free account
3. Create a new form
4. Copy the form endpoint URL
5. Update the contact form in `index.html`:
   - Change `id="contactForm"` to include `action="YOUR_FORMSPREE_URL"` and `method="POST"`
   - Remove EmailJS script and update JavaScript to use Formspree

## Notes
- EmailJS free plan: 200 emails/month
- Formspree free plan: 50 submissions/month
- Both services are reliable and easy to use
- Your email address (aadityakum123@gmail.com) is already configured in the code


# Google Form Setup for Workshops Page

To enable workshop booking on the workshops.html page, you need to create a Google Form and embed it.

## Step 1: Create Google Form

1. Go to https://forms.google.com/
2. Click "Blank" to create a new form
3. Name it: "Workshop Registration - Quantum Solution"

## Step 2: Add Form Fields

Add these fields to your form:

### Required Fields:
- **Full Name** (Short answer, Required)
- **Email Address** (Short answer, Required, Email validation)
- **Phone Number** (Short answer, Required)
- **Select Workshop** (Dropdown, Required)
  - Complete Web Development Workshop
  - Android App Development Workshop
  - SEO & Digital Marketing Masterclass
  - E-Commerce & Shopify Development
- **Preferred Batch** (Multiple choice)
  - Weekend Batch
  - Weekday Evening Batch
  - Custom Schedule
- **Any Questions?** (Paragraph, Optional)

### Optional Fields:
- **Experience Level** (Multiple choice)
  - Beginner
  - Intermediate
  - Advanced
- **How did you hear about us?** (Multiple choice)

## Step 3: Get Form Embed Code

1. Click the "Send" button (top right)
2. Click the "Embed HTML" icon (</>)
3. Copy the iframe code
4. Extract the form ID from the URL

The URL will look like:
```
https://docs.google.com/forms/d/e/FORM_ID/viewform?embedded=true
```

## Step 4: Get Entry IDs for Pre-filling

To pre-fill the workshop name in the form:

1. In your Google Form, right-click on the "Select Workshop" field
2. Click "Inspect" (or press F12)
3. Look for `entry.XXXXX` in the HTML (where XXXXX is a number)
4. Note this entry ID - you'll need it for pre-filling

Alternatively:
1. Submit a test form
2. Check the form response URL - it will contain entry IDs
3. Example: `entry.123456789` is the entry ID

## Step 5: Update workshops.html

Open `workshops.html` and find these lines (around line 450):

```javascript
const GOOGLE_FORM_BASE = 'https://docs.google.com/forms/d/e/YOUR_GOOGLE_FORM_ID/viewform?embedded=true';
```

Replace:
- `YOUR_GOOGLE_FORM_ID` with your actual Google Form ID
- `YOUR_ENTRY_ID` with the entry ID of your "Select Workshop" field (the number part, e.g., `123456789`)

Example:
```javascript
const GOOGLE_FORM_BASE = 'https://docs.google.com/forms/d/e/1FAIpQLSfXXXXX/viewform?embedded=true';
// And in the openBookingModal function:
const formUrl = GOOGLE_FORM_BASE + '&entry.123456789=' + encodedWorkshopName;
```

## Step 5: Configure Form Settings

1. In Google Forms, click the Settings icon (gear)
2. Enable:
   - ✅ Collect email addresses
   - ✅ Limit to 1 response (optional)
   - ✅ Show progress bar
3. Click "Responses" tab
4. Click the Google Sheets icon to create a spreadsheet for responses
5. Enable email notifications for new responses

## Step 6: Test the Form

1. Open workshops.html in your browser
2. Scroll to the booking form section
3. Fill out and submit a test registration
4. Check your Google Sheets for the response

## Alternative: Custom Contact Form

If you prefer not to use Google Forms, you can:
1. Use the contact form on the main page
2. Add a note in workshops.html directing users to contact you
3. Or integrate with EmailJS (similar to contact form)

## Form Response Management

- All responses will be saved in Google Sheets
- You can set up email notifications
- Export data for analysis
- Send confirmation emails manually or via automation

---

**Note:** Make sure your Google Form is set to "Anyone with the link can respond" for public access.


# EmailJS Setup Guide

Your contact form is now ready to send emails! Follow these steps to activate it:

## Step 1: Create EmailJS Account
1. Go to https://www.emailjs.com
2. Sign up for a free account
3. Verify your email

## Step 2: Set Up Email Service
1. Go to "Email Services" in your EmailJS dashboard
2. Click "Add Service"
3. Choose your email provider (Gmail, Outlook, etc.)
   - For Gmail: Enable "Less secure app access" or use an [App Password](https://support.google.com/accounts/answer/185833)
4. Complete the setup and note your **Service ID**

## Step 3: Create Email Template
1. Go to "Email Templates" in your dashboard
2. Click "Create New Template"
3. Use this template with these variables:
   ```
   Subject: New Portfolio Contact from {{from_name}}
   
   Name: {{from_name}}
   Email: {{from_email}}
   
   Message:
   {{message}}
   
   Reply to: {{from_email}}
   ```
4. Save the template and note your **Template ID**

## Step 4: Get Your Public Key
1. Go to "Account" → "API Keys"
2. Copy your **Public Key**

## Step 5: Update Your Portfolio
Replace the placeholders in `/JavaScript/script.js`:

```javascript
emailjs.init('YOUR_PUBLIC_KEY');     // Line ~45 - Replace with your public key

emailjs.send(
    'YOUR_SERVICE_ID',               // Line ~71 - Replace with your service ID
    'YOUR_TEMPLATE_ID',              // Line ~72 - Replace with your template ID
    formData
);
```

## Step 6: Test It!
1. Open your portfolio's Contact page
2. Fill out the form with test data
3. Submit and check your email inbox
4. Verify the email arrives with your message

## Troubleshooting

**Email not sending?**
- Check browser console for errors (F12 → Console)
- Verify all three IDs are correct
- Check EmailJS dashboard for activity logs
- Make sure your email service is properly connected

**Template variables not working?**
- Review EmailJS template syntax: `{{variable_name}}`
- Ensure variable names match exactly in both template and JavaScript

**Rate limiting?**
- Free EmailJS account allows 200 emails/month
- Upgrade plan if you need more

## Security Note
Your public key is intentionally public (client-side only). The service and template IDs are also safe to expose in your frontend code.

---

Need help? Check [EmailJS Documentation](https://www.emailjs.com/docs/)

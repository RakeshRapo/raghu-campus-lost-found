# Email Notifications & Finder Details Guide

## 📧 Email Notification System

The Campus Find the Lost Portal now includes automatic email notifications for key events. This system helps keep all parties informed about the status of their items.

### 🔧 Email Configuration

Before using email notifications, you need to configure your email settings:

1. **Copy the configuration file:**
   ```bash
   cp email-config.example.js email-config.js
   ```

2. **Edit `email-config.js` with your credentials:**
   ```javascript
   module.exports = {
       email: {
           service: 'gmail', // or 'outlook', 'yahoo', etc.
           auth: {
               user: 'your-email@gmail.com',
               pass: 'your-app-password'
           }
       }
   };
   ```

3. **For Gmail users:**
   - Enable 2-factor authentication
   - Generate an App Password: https://myaccount.google.com/apppasswords
   - Use the App Password instead of your regular password

4. **Update the server configuration:**
   - Edit `server-excel.js` and update the `emailConfig` object with your credentials
   - Or set environment variables: `EMAIL_USER` and `EMAIL_PASS`

### 📬 Email Notifications Sent

#### 1. When an Item is Found (Found Button Clicked)
- **Trigger:** Someone clicks "I Found This!" and submits finder details
- **Recipient:** Original item owner (the person who lost the item)
- **Email Content:**
  - Item details (name, category, description, location)
  - Finder information (name, email, pickup location, preferred time)
  - Next steps for arranging pickup
  - Professional HTML template with styling

#### 2. When an Item is Claimed (Claim Button Clicked)
- **Trigger:** Someone clicks "This Belongs to Me!" and submits claim details
- **Recipients:** 
  - **Claimer:** Confirmation of their claim submission
  - **Finder:** Notification that someone wants to claim their found item
- **Email Content:**
  - Item details and claim information
  - Claimer's contact details and proof of ownership
  - Status updates and next steps

### 🎨 Email Templates

The system uses three professional HTML email templates:

1. **`item_found`** - Sent to original owner when item is found
2. **`item_claimed`** - Sent to claimer confirming their claim
3. **`finder_notified`** - Sent to finder when someone claims their item

All templates include:
- Responsive design
- Professional styling
- Clear information hierarchy
- Actionable next steps
- Branded footer

## 📍 Where to Find Finder Details

### 1. In Item Cards (Main View)
Finder details are displayed directly in the item cards for found items:

- **Location:** Main item listings page
- **When visible:** Only for lost items that have been marked as found
- **Information shown:**
  - Finder's name
  - Contact email
  - Pickup location
  - Preferred pickup time
- **Visual style:** Blue-tinted box with clear labeling

### 2. Contact Finder Button
- **Location:** On found item cards
- **Function:** Opens email client with pre-filled details
- **Information included:**
  - Professional email template
  - Item details
  - Pickup information
  - Contact details

### 3. Owner Notification Modal
- **Trigger:** Automatically appears when item is found
- **Information:** Complete finder details with contact options
- **Actions:** Direct email contact button

### 4. API Endpoint
- **URL:** `GET /api/finder-details/:itemId`
- **Returns:** JSON with finder details and item information
- **Use case:** For programmatic access to finder information

### 5. Excel Database
Finder details are stored in the Excel file:

**Lost Items Sheet:**
- `finderDetails` column (JSON object)
- Contains complete finder information

**Found Items Sheet:**
- `finderName` - Finder's name
- `finderContact` - Finder's email
- `finderLocation` - Pickup location
- `finderNotes` - Additional notes
- `pickupTime` - Preferred pickup time

## 🔄 Email Notification Flow

### Found Item Flow:
1. User finds item → Clicks "I Found This!"
2. User fills finder details form
3. System saves to Excel database
4. **Email sent to original owner** with finder details
5. Owner can contact finder directly

### Claim Item Flow:
1. User sees found item → Clicks "This Belongs to Me!"
2. User fills claim form with ownership proof
3. System saves claim to Excel database
4. **Email sent to claimer** confirming submission
5. **Email sent to finder** with claim details
6. Both parties can communicate to verify ownership

## 🛠️ Technical Implementation

### Server-Side (Node.js)
- **Package:** Nodemailer for email sending
- **Configuration:** SMTP settings in `server-excel.js`
- **Templates:** HTML templates with inline CSS
- **Async sending:** Emails sent asynchronously to avoid blocking

### Frontend Integration
- **Contact buttons:** Direct email client integration
- **Modal notifications:** User-friendly contact information display
- **API calls:** Fetch finder details from server endpoints

### Database Storage
- **Excel integration:** All finder details stored in Excel file
- **JSON fields:** Complex data stored as JSON strings
- **Backup:** Excel file serves as backup and export option

## 🔒 Security & Privacy

### Email Security:
- Uses SMTP with authentication
- Supports 2FA and app passwords
- No sensitive data in email subjects
- Professional templates maintain privacy

### Data Protection:
- Only email addresses are shared (no phone numbers)
- Contact information is public but controlled
- All communications are opt-in
- No automated spam or marketing emails

## 🚀 Getting Started

1. **Configure email settings** (see Email Configuration above)
2. **Test the system** with a sample lost/found item
3. **Monitor email delivery** in server logs
4. **Customize templates** if needed for your organization

## 📊 Monitoring & Logs

The server logs email activities:
- Successful email sends with message IDs
- Failed email attempts with error details
- Email recipient information for debugging

Check server console for email status messages when testing.

## 🆘 Troubleshooting

### Common Issues:
1. **Emails not sending:** Check email configuration and credentials
2. **Finder details not showing:** Verify Excel database structure
3. **Contact buttons not working:** Check browser email client settings

### Debug Steps:
1. Check server logs for email errors
2. Verify Excel file contains finder details
3. Test email configuration separately
4. Check browser console for JavaScript errors

---

**Note:** This email notification system enhances the user experience by keeping all parties informed about item status changes, while maintaining security and privacy standards.

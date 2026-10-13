

CONTACT ENQUIRY EMAIL NOTIFICATIONS
-----------------------------------
The contact form stores each enquiry in the site's database and sends a notification to jvmsmartvers@gmail.com when SMTP is configured. Set these environment variables in the hosting dashboard (do not commit credentials):
  SMTP_HOST=smtp.gmail.com
  SMTP_PORT=587
  SMTP_USERNAME=<the Gmail account used to send notifications>
  SMTP_PASSWORD=<Google App Password for that account>
  SMTP_FROM_EMAIL=<same Gmail address or verified sender>
Use a Google App Password, not your normal Gmail password. Enable 2-Step Verification on the sending Gmail account first, then create an App Password. After adding variables, restart/redeploy the service. If not configured, enquiries still save, but email notifications will not be sent.

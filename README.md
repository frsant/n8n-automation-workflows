#  Client Onboarding & Follow-Up Workflow with n8n

This workflow automates the **client intake and subscription tracking process** for a fitness & nutrition coaching service.  

It allows you to:
1. Collect detailed onboarding information via a **custom form**.  
2. Automatically store client data in a **Google Sheets tracker**.  
3. Send **email reminders** when a client’s subscription renewal is approaching.  

---

## Workflow Overview

### 1. Onboarding Form
- A form titled **“INITIAL QUESTIONNAIRE”** is presented to new clients.  
- Clients provide personal details, goals, training background, daily routine, eating habits, preferences, and more.  
- Key fields include: email, name, age, height, weight, objectives, gym experience, weekly availability, food preferences, lifestyle, and health conditions.  

 **Trigger used:** `Form Trigger`

---

### 2.  Store Data in Google Sheets
- Every time a client submits the form, their information is **appended to a Google Sheet** for tracking.  
- The workflow automatically calculates:  
  - **Service type** selected (monthly, quarterly, semi-annual, competition, nutrition, training).  
  - **Estimated value** of the service.  
  - **Start date** (current date).  
  - **Renewal date** (based on the selected plan).  

 **Node used:** `Google Sheets (Append Row)`

---

### 3.  Daily Renewal Check
- Every day at **08:00 AM**, the workflow checks the Google Sheet for clients whose renewal is **2 days away**.  

 **Trigger used:** `Schedule Trigger`  
 **Node used:** `Google Sheets (Lookup Rows)`

---

### 4.  Email Reminder
- When a renewal is due in 2 days, an **automated reminder email** is sent to the client.  

 **Node used:** `Email Send (SMTP)`

---

##  Requirements

- [n8n](https://n8n.io) installed (self-hosted or cloud).  
- A **Google account** with access to the target Google Sheet.  
- An **SMTP email account** (Gmail, Outlook, or any other mail provider).  

---

##  How to Use

1. **Import the workflow** into your n8n instance (`.json` file).  
2. Set up the following credentials in n8n:  
   - **Google Sheets OAuth2 API**  
   - **SMTP Email account**  
3. Update the Google Sheet ID and sheet name to match your own.  
4. Adjust email content and recipient details as needed.  
5. Activate the workflow. 

---

##  Notes

- No private credentials are stored in the workflow JSON.  
- Before publishing, anonymize any **real client data**.  
- The workflow can be extended with:  
  - CRM integration (HubSpot, Pipedrive).  
  - Slack/Telegram notifications.  
  - Payment tracking (Stripe, PayPal).  

---

## 📄 License
This project is released under the [MIT License](LICENSE). Feel free to use and adapt it.  

# 📂 Power Automate Flow Guide  
## Auto-Create OneDrive Folders from Email Attachments

## 🧾 Overview

This document outlines how to configure a **Microsoft Power Automate** flow that:

- Automatically creates a folder in **OneDrive for Business**
- Uses the **email subject line** as the folder name
- Saves all email attachments into the corresponding folder

The flow is triggered whenever a new email with attachments is received.

---

## ⚙️ Prerequisites

Before proceeding, ensure you have:

- ✅ Access to **Microsoft Power Automate**
- ✅ A valid **OneDrive for Business** account
- ✅ A designated parent folder in OneDrive  
  *(Example: `Email Attachment Folders using Subject`)*

---

## 📁 Step 0 — OneDrive Folder Creation

### 📌 Create the Parent Folder

1. Open **OneDrive**
2. Create a new folder with the following name:

```

Email Attachment Folders using subject

```

> 📎 This folder will act as the root directory where all email-based folders will be created.

---

## 🔄 Flow Configuration

### 🚀 Step 1 — Configure the Trigger

1. Open **Power Automate**
2. Navigate to:
   - **New Flow** → **Automated Cloud Flow**
3. Enter the following details:
   - **Flow Name:** `Email Attachment Folders using subject`
4. Select the trigger:
   - **When a new email arrives (V3) — Office 365 Outlook**
5. Click **Create**

---

### ⚙️ Configure Advanced Trigger Settings

1. Expand **Advanced Parameters**
2. Click **"Show all"** *(or “Showing 0 of 9”)*
3. Enable the following option:
   - ✅ **Only with Attachments**
4. Set:
   - **Only with Attachments → Yes**

> ⚠️ This ensures the flow only runs when incoming emails contain attachments.

---

### 📄 Step 2 — Configure "Create File" Action

#### ➕ Add Action

- Select action: **Create File** *(OneDrive for Business)*

---

#### 📂 Folder Path Configuration

- Choose your parent folder:
```

/Email Attachment Folders using subject

```

- Append `/Subject` using dynamic content:

```

Example:
/Email Attachment Folders using subject/Subject

```

> 📁 The **Subject** value dynamically creates a new folder for each email.

---

#### 📝 File Configuration

- **File Name:**
  - Select **Attachment Name** from Dynamic Content  
```

Example: Attachment Name

```

- **File Content:**
- Select **Attachment Content** from Dynamic Content  
```

Example: Attachment Content

````

---

### 🔁 Automatic Loop Handling

> ⚠️ When **Attachment Name** is selected, Power Automate automatically creates a **"For Each" loop**.

This allows the flow to:
- Process single attachments
- Handle multiple attachments efficiently

---

## 🧠 Process Flow Logic

```plaintext
New Email Arrives
     ↓
Check: Has Attachments? → Yes
     ↓
For Each Attachment:
→ Navigate to /Email Attachment Folders/[Email Subject]/
→ Create folder if it does not exist
→ Save attachment inside the folder
````

---

## 🧪 Testing the Flow

Follow these steps to validate the configuration:

1. 💾 Save the flow
2. ▶️ Click **Test → Manually**
3. 📧 Send a test email to yourself with an attachment
4. 📥 Wait for the email to arrive
5. 🔍 Verify in OneDrive:

   * A folder is created using the email subject
   * The attachment is saved inside the folder

---

## 📝 Key Notes

| 🔑 Feature          | 📌 Description                               |
| ------------------- | -------------------------------------------- |
| Folder Naming       | Automatically derived from the email subject |
| Attachment Handling | Managed via auto-generated For Each loop     |
| Folder Creation     | Automatically created if it does not exist   |
| Trigger Timing      | Typically instant, may take a few seconds    |

---

## ✅ Summary

This automation improves file management by:

* 📂 Dynamically organizing attachments into subject-based folders
* ⚡ Eliminating manual file handling
* 📎 Ensuring consistent and structured storage in OneDrive

---

```
```

# IT Help Desk: User Password Reset & Ticket Resolution Workflow

![Windows Server 2025](https://img.shields.io/badge/OS-Windows%20Server%202025-blue?style=for-the-badge&logo=windows)
![Active Directory](https://img.shields.io/badge/Identity-Active%20Directory%20Users%20%26%20Computers-0078D4?style=for-the-badge&logo=microsoft)
![Zendesk](https://img.shields.io/badge/Ticketing-Zendesk%20Support-03363D?style=for-the-badge&logo=zendesk)
![Status](https://img.shields.io/badge/Ticket%20Status-Solved-success?style=for-the-badge)

## 📌 Project Overview

This documentation details the standard operating procedure (SOP) for handling an inbound **Password Reset Request** via **Zendesk** ticketing system and fulfilling it within **Active Directory Users and Computers (ADUC)** on **Windows Server 2025**.

The project demonstrates key Tier 1 / Tier 2 Help Desk responsibilities:
1. **Ticket Ingestion & Verification:** Analyzing user request details in Zendesk.
2. **Identity & Access Management:** Locating the user object within Active Directory Organizational Units (OUs) and applying a temporary password.
3. **Security Enforcement:** Mandating password change upon initial login.
4. **End-User Communication:** Replying professionally with login instructions.
5. **Internal Documentation:** Logged root cause, troubleshooting steps, and resolution details before closing the ticket.

---

## 🛠️ Tools & Technologies Used

- **Ticketing Platform:** Zendesk Support Desk
- **Directory Service:** Active Directory Domain Services (AD DS) / `domain: DemoAD.Local2`
- **Management Console:** Active Directory Users and Computers (`dsa.msc`)
- **Server Operating System:** Windows Server 2025 Datacenter
- **User Handled:** Arnold Markley (`Human Resources` OU)
- **Assigned Help Desk Technician:** Tim Johnson

---

## 🚀 Step-by-Step Workflow & Execution

### Step 1: Receiving and Reviewing the Zendesk Ticket

1. Log into the **Zendesk Support Dashboard**.
2. Locate the incoming ticket under **Unassigned / New Tickets** (Ticket #4).
3. Review ticket details:
   - **Requester:** Arnold Markley (`arnoldmarkley1@solutions.com`)
   - **Subject:** `Password Reset`
   - **User Message:** *"Good afternoon Sherri, I seem to have forgotten my password and can't sign in. Can you reset it for me, Thanks -Arnold"*

![Zendesk New Ticket Received](./Screenshot%20Ticket%20Received.png)
*Figure 1: Ticket #4 submitted in Zendesk by Arnold Markley requesting a password reset.*

---

### Step 2: Assigning the Ticket and Acknowledging the User

1. Assign Ticket #4 to the handling agent (**Tim Johnson**).
2. Set ticket state to **Open**.
3. Send an initial public response to the user letting them know their ticket is being actively worked on:
   > *"Hi Arnold, no worries we'll have you back in your account in no time!"*
4. Click **Submit as Open**.

![Zendesk Response to User](./Screenshot%20Public%20Reply.png)
*Figure 2: Assigning the ticket and acknowledging the user's issue.*

---

### Step 3: Performing Password Reset in Active Directory (Windows Server 2025)

1. Connect to the **Windows Server 2025 Domain Controller**.
2. Open **Active Directory Users and Computers** (`dsa.msc`).
3. Expand the domain tree (`DemoAD.Local2`) and navigate to the user's Organizational Unit:
   - **Path:** `DemoAD.Local2` ➔ `Human Resources`
4. Locate user object **Arnold Markley**.
5. Right-click **Arnold Markley** and select **Reset Password...**.

![Active Directory User Selection](./Screenshot%20ADUC%20User%20Select.png)
*Figure 3: Locating Arnold Markley under the Human Resources Organizational Unit in ADUC.*

6. In the **Reset Password** dialog window:
   - Enter a secure temporary password (e.g., `TheLamb01%`).
   - Confirm the temporary password.
   - **CRITICAL SECURITY STEP:** Check **"User must change password at next logon"**.
7. Click **OK** to apply the password reset.

![Active Directory Password Reset Dialog](./Screenshot%20ADUC%20Password%20Reset.png)
*Figure 4: Setting a temporary password and enforcing password change on next logon.*

---

### Step 4: Communicating Temporary Credentials & Verification

1. Return to **Zendesk Ticket #4**.
2. Draft a public reply providing clear instructions to the user:
   > *"Hi Arnold, I was able to reset your password for you. Login with the password `TheLamb01%`. Where after you will be required to change it immediately upon log-on to a password of your choosing that fits company parameters. Is there anything else I can help you with or is that it?"*
3. The user confirms resolution: *"That was all Sherri, thank you for solving this so quickly!"*

![User Confirmation in Zendesk](./Screenshot%20User%20Confirmation.png)
*Figure 5: Transmitting temporary password instructions and receiving confirmation from the end-user.*

---

### Step 5: Internal Documentation & Ticket Closure

1. Switch response mode in Zendesk from **Public reply** to **Internal note**.
2. Document the ticket summary following standard Help Desk logging guidelines:
   ```text
   Issue Summary: User needed password reset
   Root cause: Forgot original credentials.
   Steps Taken: Accessed user account through AD and initiated password reset.
   Solution Implemented: Created a simple easy to read temporary password and required it to be changed at next log-on.
   User Communication: Contacted user to notify the issue was resolved and steps needed on their end.
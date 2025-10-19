# Module 02: Onboarding Admins & Invitations

**Module Duration:** 45 minutes | **Difficulty:** Intermediate
**Prerequisites:** Module 01 completed, super_admin role required

---

## 🎯 **PURPOSE**

This module teaches super admins how to safely invite new team members to LetsGoBelize.app. You'll learn:
- How to create secure admin invitations
- 48-hour expiry policy enforcement
- Audit trail review procedures
- Emergency invitation revocation
- Onboarding checklist for new admins

⚠️ **Caution:** Only super_admin role can create invitations. If you're an admin, request invitations from your super admin.

---

## ⏰ **WHEN TO USE**

Use this procedure when:
- Hiring a new admin, blogger, or guide
- Replacing a departing team member
- Promoting an existing user to higher role
- Conducting quarterly access review
- Responding to security audit findings

---

## 📋 **STEP-BY-STEP: Create Admin Invitation**

### **Method 1: Dashboard UI (Recommended)**

#### **Step 1: Navigate to User Management**

1. Log into Admin Dashboard (`/dashboard`)
2. Click **"User Management"** in left sidebar
3. Select **"Admin Invitations"** tab
4. Verify you see "Create New Invitation" button (super_admin only)

💡 **Tip:** If you don't see this button, you lack super_admin role.

---

#### **Step 2: Fill Invitation Form**

Required fields:

| **Field**          | **Example**                      | **Notes**                                      |
|--------------------|----------------------------------|------------------------------------------------|
| Email              | jane.doe@letsgobelize.app        | Must be valid corporate email                  |
| Role               | `admin`                          | Dropdown: super_admin, admin, blogger, guide   |
| Invited By         | (Auto-filled)                    | Your name as inviter                           |
| Expiration         | 48 hours (default)               | System-enforced, cannot extend                 |
| Personal Message   | "Welcome to the team!"           | Optional, sent in invitation email             |

⚠️ **Caution:** Double-check email address. Invitations cannot be edited after sending.

---

#### **Step 3: Review Permissions**

Before clicking "Send Invitation," confirm:

- [ ] Email address is correct (no typos)
- [ ] Role matches job responsibilities (see Module 01 RBAC matrix)
- [ ] Recipient expects this invitation (avoid surprise invites)
- [ ] Expiration time allows recipient to respond (48h standard)

💡 **Best Practice:** Email recipient first to confirm they'll accept invitation.

---

#### **Step 4: Send & Verify**

1. Click **"Send Invitation"** button
2. Wait for success toast: "✅ Invitation sent successfully"
3. Check **Invitation Status** shows "pending"
4. Verify audit log entry created (see Step 5)

✅ **Success:** Recipient receives email with unique invitation link.

---

#### **Step 5: Monitor Acceptance**

Check invitation status regularly:

| **Status**   | **Meaning**                          | **Action Required**                |
|--------------|--------------------------------------|------------------------------------|
| `pending`    | Sent, awaiting acceptance            | None (wait for recipient)          |
| `accepted`   | User created account successfully    | Begin onboarding process           |
| `expired`    | 48 hours passed without acceptance   | Resend new invitation              |
| `revoked`    | Manually cancelled by super admin    | None (intentionally blocked)       |

⚠️ **Caution:** Expired invitations CANNOT be reactivated. You must create a new one.

---

### **Method 2: Emergency Invitation (Supabase Dashboard)**

Use this method ONLY if Admin Dashboard is down.

#### **Prerequisites**
- Access to Supabase Dashboard (`https://supabase.com/dashboard`)
- `admin_invitations` table write permissions

#### **Steps**

1. Navigate to Supabase project → Table Editor → `admin_invitations`
2. Click **"Insert row"**
3. Fill required columns:
   ```sql
   email: jane.doe@letsgobelize.app
   role: admin
   invited_by: (your user_id from auth.users table)
   expires_at: (current_time + 48 hours)
   status: pending
   ```
4. System triggers automated system to send email automatically
5. Return to Admin Dashboard to monitor acceptance

⚠️ **Warning:** This bypasses UI validation. Use only in emergencies.

---

## 🔍 **Audit Trail Review**

### **Purpose**

Every invitation creates two audit records:
1. **admin_invitations table:** Invitation details, status, timestamps
2. **admin_invitation_audit table:** Complete history of status changes

### **How to Review Audit Trail**

#### **Step 1: Access Audit Dashboard**

1. Admin Dashboard → **"Security Alerts"** → **"Admin Actions Audit"**
2. Filter by date range (default: last 30 days)
3. Filter by action type: "invitation_created", "invitation_accepted", "invitation_expired"

---

#### **Step 2: Key Audit Fields**

| **Field**        | **What to Check**                               |
|------------------|-------------------------------------------------|
| `invited_by`     | Was invitation created by authorized super admin? |
| `email`          | Is email a legitimate corporate address?        |
| `role`           | Does role match recipient's job description?    |
| `accepted_at`    | How quickly did user accept? (security metric)  |
| `ip_address`     | Was invitation accepted from expected location? |
| `user_agent`     | Was invitation accepted from legitimate device? |

💡 **Red Flags:**
- Invitation accepted within 1 minute (possible automated attack)
- Multiple failed acceptance attempts (suspicious activity)
- IP address from unexpected country
- Role = super_admin without CTO approval

---

#### **Step 3: Monthly Audit Checklist**

Perform this review on the 1st of each month:

- [ ] List all invitations created last month
- [ ] Verify each invitation had legitimate business purpose
- [ ] Check for expired invitations (resend if needed)
- [ ] Confirm accepted users completed onboarding
- [ ] Review revoked invitations (document reason)
- [ ] Export audit log to CSV for compliance records

📄 **Export Location:** `Admin Dashboard → Security Alerts → Export Audit Log`

---

## 🚨 **Emergency Revoke Procedure**

### **When to Revoke**

Revoke an invitation immediately if:
- Recipient reports invitation email was not requested (phishing attempt)
- Employee terminated before accepting invitation
- Invitation sent to wrong email address
- Security breach detected involving invited email

⚠️ **Critical:** Revocation prevents the invitation link from working, even if already sent.

---

### **Step-by-Step: Revoke Invitation**

#### **Method 1: Dashboard (Fastest)**

1. Admin Dashboard → **"User Management"** → **"Admin Invitations"**
2. Find invitation (filter by email or status)
3. Click **"⋮ More"** menu → **"Revoke Invitation"**
4. Confirm revocation reason in modal:
   - "Sent to wrong email"
   - "Recipient terminated"
   - "Security concern"
   - "Other (specify)"
5. Click **"Confirm Revoke"**
6. System automatically:
   - Updates `status` to "revoked"
   - Logs revocation in audit table
   - Disables invitation link
   - Does NOT send email (silent revocation)

✅ **Success:** Invitation link returns "Invalid or expired" if clicked.

---

#### **Method 2: Supabase Dashboard (Emergency)**

1. Supabase Dashboard → `admin_invitations` table
2. Find row by email
3. Update `status` column: `pending` → `revoked`
4. Add `revoked_at` timestamp: current time
5. Add `revoked_by` user_id: your user ID
6. Save changes

⚠️ **Warning:** This does NOT trigger audit log entry. Manually document revocation.

---

## ⚠️ **DO / DO NOT**

### **DO:**

✅ **Verify recipient identity before sending**
- Confirm via video call or in-person
- Use official company email only

✅ **Use corporate email addresses**
- jane.doe@letsgobelize.app ✅
- jane.personal@gmail.com ❌

✅ **Match role to job description**
- Sales team → `guide` (if creating tours)
- Content team → `blogger`
- Operations manager → `admin`
- Leadership → `super_admin` (CTO approval required)

✅ **Monitor acceptance within 48 hours**
- Send reminder email at 24h mark
- Resend if expired

✅ **Document all super_admin promotions**
- Require written CTO approval
- Store approval in `docs/security/admin-promotions/`

---

### **DO NOT:**

❌ **Never send invitations to personal emails**
- Security policy violation
- Audit trigger

❌ **Never create multiple invitations for same person**
- Confuses recipient
- Creates audit noise
- If first expired, create ONE new invitation

❌ **Never share invitation links**
- Links are single-use, tied to specific email
- Sharing = security breach

❌ **Never bypass 48-hour expiry**
- System-enforced for security (Security Audit, Aug 23, 2025)
- No exceptions

❌ **Never promote to super_admin without CTO sign-off**
- Requires written approval
- Unauthorized promotion = immediate audit investigation

---

## ✅ **VERIFICATION CHECKLIST**

After creating an invitation, confirm:

- [ ] Recipient received invitation email within 5 minutes
- [ ] Invitation link is unique (check `token` field in database)
- [ ] Expiration timestamp is exactly 48 hours from creation
- [ ] Audit log entry created with correct `invited_by` field
- [ ] Status shows "pending" in dashboard
- [ ] Role matches job description (cross-check HR records)
- [ ] Personal message displays correctly in email (if provided)

If ANY checkbox fails, revoke invitation and create new one.

---

## 🚨 **ESCALATION**

| **Issue**                              | **Contact**                      | **Response Time** |
|----------------------------------------|----------------------------------|-------------------|
| Invitation email not received          | support@letsgobelize.app         | 1 hour            |
| Invitation link returns "Invalid"      | security@letsgobelize.app        | 30 minutes        |
| User accepted but cannot log in        | engineering@letsgobelize.app     | 1 hour            |
| Suspected unauthorized invitation      | security@letsgobelize.app        | 15 minutes        |
| Need to extend expiration (exception)  | CTO approval required            | 24-48 hours       |

---

## 📋 **New Admin Onboarding Checklist**

Once invitation is accepted, complete this onboarding:

### **Day 1: Account Setup**

- [ ] User logs in successfully with new credentials
- [ ] User completes profile (name, bio, profile picture)
- [ ] User receives welcome email from admin team
- [ ] User added to team Slack/communication channels
- [ ] User assigned a mentor admin for shadowing

---

### **Week 1: Training**

- [ ] User reads Admin Training Manual (this document)
- [ ] User completes Module 01 (Roles & Permissions)
- [ ] User shadows mentor for daily tasks
- [ ] User granted access to staging environment for practice
- [ ] User completes security awareness training

---

### **Week 2: Supervised Practice**

- [ ] User performs 3 supervised tour creations
- [ ] User processes 2 supervised bookings
- [ ] User sends 1 supervised safety alert (staging only)
- [ ] User completes troubleshooting simulation
- [ ] Mentor signs off on competency checklist

---

### **Week 3: Independent Operations**

- [ ] User operates independently with spot-check reviews
- [ ] User attends first team meeting
- [ ] User added to on-call rotation (if applicable)
- [ ] User completes feedback survey on training

📄 **Template:** See [15-Checklists-and-Templates.md](15-Checklists-and-Templates.md) for full onboarding checklist.

---

## 📚 **Common Scenarios**

### **Scenario 1: Invitation Expired**

**Problem:** User didn't check email for 3 days, invitation expired.

**Solution:**
1. Verify user still needs access (check with HR)
2. Create NEW invitation (do not try to reactivate old one)
3. Send personal email/Slack reminder: "New invitation sent, please accept within 48h"
4. Mark old invitation as "expired_resent" in notes

---

### **Scenario 2: Wrong Role Assigned**

**Problem:** User accepted invitation but needs different role.

**Solution:**
1. Log into Admin Dashboard → **"User Management"**
2. Find user in **"All Users"** table
3. Click **"Edit"** → Change role dropdown
4. Click **"Save Changes"**
5. User's new role takes effect on next login (or force logout)

💡 **Tip:** Role changes do NOT require re-invitation.

---

### **Scenario 3: Duplicate User Created**

**Problem:** User accepted invitation twice (two accounts with same email).

**Root Cause:** Cannot happen—Supabase Auth prevents duplicate emails.

**If reported:**
1. Check if user has two different emails (e.g., typo: jane.doe@ vs jane.do@)
2. Identify correct account (most recent activity)
3. Super admin deletes duplicate account
4. Merge data if necessary (contact engineering@letsgobelize.app)

---

## 🔒 **Security Best Practices**

### **48-Hour Expiry Policy**

**Why:** Prevents invitation links from being used weeks/months later if compromised.

**Enforcement:** System automatically sets `expires_at = created_at + 48 hours`. Cannot be overridden in UI.

**Exception Process:**
1. Document business justification
2. Email CTO with request
3. CTO provides written approval
4. Engineering manually extends expiration in database
5. Incident logged in security audit

💡 **Note:** As of August 23, 2025 Security Audit, zero extensions have been granted.

---

### **Single-Use Tokens**

Invitation tokens use UUID v4 format and are:
- Cryptographically random (impossible to guess)
- Single-use (marked as "used" after acceptance)
- Tied to specific email (cannot be transferred)

⚠️ **If token leaked:** Revoke invitation immediately, create new one.

---

### **Audit Logging**

Every invitation action creates immutable audit records:

```sql
-- Example audit entry
{
  "action": "invitation_accepted",
  "user_id": "abc-123",
  "invited_email": "jane.doe@letsgobelize.app",
  "role": "admin",
  "accepted_at": "2025-10-08T14:30:00Z",
  "ip_address": "192.168.1.100",
  "user_agent": "Mozilla/5.0..."
}
```

📄 **Retention:** Audit logs stored for 7 years (compliance requirement).

---

## 🎓 **Knowledge Check**

1. Who can create admin invitations? **Only super_admin role**
2. How long are invitations valid? **48 hours (system-enforced)**
3. Can expired invitations be reactivated? **NO—must create new invitation**
4. What email addresses are allowed? **Corporate emails only (e.g., @letsgobelize.app)**
5. How do you revoke an invitation? **Dashboard → User Management → Admin Invitations → Revoke**

✅ **If you answered 4/5 correctly, proceed to Module 03.**

---

**Next Module:** [03: Tours Management](03-Tours-Management.md) →

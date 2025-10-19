# Module 01: Roles & Permissions

**Module Duration:** 30 minutes | **Difficulty:** Beginner
**Prerequisites:** Admin Dashboard access

---

## 🎯 **PURPOSE**

Understanding roles and permissions is critical to safely operating LetsGoBelize.app. This module teaches you:
- What each role can and cannot do
- How platform security protects data
- When to escalate permission requests
- How to recognize unauthorized actions

---

## ⏰ **WHEN TO USE**

Use this module when:
- Starting your first day as admin
- Before creating invitations for new team members
- Troubleshooting "Permission Denied" errors
- Reviewing security audit findings
- Training new staff on the platform

---

## 📋 **RBAC Matrix (Who Can Do What)**

### **super_admin (Full Platform Access)**

✅ **Can Do:**
- Manage all users (create, edit, delete, change roles)
- Access all tours and bookings (including other guides' content)
- Process all payments and refunds
- Send safety alerts to all travelers
- View and export all analytics
- Manage AI Concierge system settings
- Configure platform security settings
- Create admin invitations
- Access financial reports and payouts
- Publish/unpublish any content

❌ **Cannot Do:**
- Nothing (full access granted)

⚠️ **Caution:** Super admin powers are permanent. Only assign this role to trusted leadership.

---

### **admin (Operations Manager Access)**

✅ **Can Do:**
- View all tours and bookings
- Edit any tour or booking
- Process refunds within established limits
- Send safety alerts (location-specific)
- Publish blog posts
- Access analytics dashboards
- Upload images to platform storage
- Manage calendar and messages
- View financial transaction reports

❌ **Cannot Do:**
- Change user roles (must request from super admin)
- Modify platform security settings
- Process large refunds (requires super admin approval)
- Delete users or permanently remove data
- Access AI training data or expert validation queue

💡 **Tip:** If you need to change someone's role, email the super admin with justification.

---

### **blogger (Content Creator Access)**

✅ **Can Do:**
- Create, edit, and publish blog posts
- Upload blog images to designated storage
- View blog analytics (views, engagement)
- Manage own author profile
- Access content calendar

❌ **Cannot Do:**
- View or edit tours
- Access bookings or payments
- Send safety alerts
- View user analytics
- Edit other bloggers' posts (unless super admin)
- Upload images to restricted storage areas

💡 **Tip:** Bloggers should never have access to traveler personal information.

---

### **guide (Tour Operator Access)**

✅ **Can Do:**
- Create and edit **own** tours
- View **own** bookings and customer details
- Upload images to tour storage
- Manage own calendar availability
- View own earnings and payout history
- Respond to customer messages
- Update tour availability/pricing

❌ **Cannot Do:**
- View other guides' tours or bookings
- Access platform-wide analytics
- Send safety alerts
- Process refunds (must request from admin)
- Edit blog posts
- Change tour approval status (auto-published after review)

⚠️ **Important:** Guides see ONLY their own data due to platform security.

---

### **traveler (Customer Access)**

✅ **Can Do:**
- Browse and book tours
- View own bookings
- Manage profile and preferences
- Upload profile picture
- Contact guides via messages
- Request refunds (admin approves)

❌ **Cannot Do:**
- Access Admin Dashboard
- View other travelers' data
- Create tours or blog posts
- Access analytics
- Send safety alerts

💡 **This role is for customers only—no backend access.**

---

## 🔒 **Platform Security Overview**

### **How Data Protection Works**

The platform automatically enforces data access rules based on your role:
- Guides see only **their** tours and bookings
- Admins can view all operational data
- Travelers can only access their own bookings and profile
- Security rules are managed by the engineering team

### **What This Means for You**

When you log in, the system automatically:
- Shows you only the data you're authorized to see
- Prevents accidental access to restricted information
- Blocks unauthorized modifications
- Enforces role-based rules consistently

**Example**: A guide viewing bookings will only see bookings for their own tours, even if they try to access other data.

💡 **Key Takeaway:** Security policies are configured by the engineering team and cannot be changed from the dashboard.

---

## 🛡️ **Safe vs Unsafe Actions**

### **Safe Actions (Always Allowed)**

✅ **Viewing data within your role**
- Guide viewing own bookings
- Admin viewing all analytics
- Blogger viewing own posts

✅ **Editing your own profile**
- Update name, bio, profile picture
- Change dietary restrictions (travelers)

✅ **Creating content you're authorized for**
- Guide creating new tour
- Blogger publishing blog post
- Admin sending safety alert

---

### **Unsafe Actions (Require Approval)**

⚠️ **Editing data outside your scope**
- Guide editing another guide's tour → **Escalate to admin**
- Admin changing user roles → **Escalate to super admin**
- Blogger accessing booking data → **Permission denied (by design)**

⚠️ **Financial operations above limits**
- Admin issuing refund > established limit → **Requires super admin approval**
- Guide requesting early payout → **Contact payments@letsgobelize.app**

⚠️ **Database or security changes**
- Requesting security policy changes → **Email engineering@letsgobelize.app with business justification**
- Adding new admin users → **Use Module 02 invitation process**

---

## ⚠️ **DO / DO NOT**

### **DO:**

✅ **Stay within your role boundaries**
- Only perform actions your role allows
- Request permission escalation via proper channels

✅ **Verify permissions before bulk actions**
- Test with 1 record before updating 100
- Check you're logged in with correct role

✅ **Report permission errors immediately**
- Screenshot "Access Denied" messages
- Email security@letsgobelize.app

✅ **Ask when uncertain**
- Better to ask than break production

---

### **DO NOT:**

❌ **Never share login credentials**
- Each admin gets their own account
- No "shared admin" accounts

❌ **Never try to bypass security**
- Do not attempt SQL queries directly
- Do not use browser dev tools to modify requests

❌ **Never change roles without authorization**
- Only super admin can promote users
- Unauthorized role changes trigger security alerts

❌ **Never access data outside your role**
- Guides: Don't try to view other guides' bookings
- Bloggers: Don't attempt to access payment data

---

## ✅ **VERIFICATION CHECKLIST**

Before proceeding to other modules, confirm:

- [ ] I understand my assigned role and its limits
- [ ] I know which actions require escalation
- [ ] I can explain security in simple terms
- [ ] I know who to contact for permission changes
- [ ] I've tested my dashboard access successfully
- [ ] I can identify safe vs unsafe actions
- [ ] I have bookmarked the escalation contacts

---

## 🚨 **ESCALATION GUIDE**

### **When to Escalate**

| **Scenario**                                  | **Contact**                      | **Response Time** |
|-----------------------------------------------|----------------------------------|-------------------|
| "Access Denied" error for authorized action   | hello@letsgobelize.app           | 2 hours           |
| Need to change a user's role                  | Super admin via email            | 24 hours          |
| Suspected security breach (unauthorized access)| security@letsgobelize.app        | 15 minutes        |
| security policy blocking legitimate work           | engineering@letsgobelize.app     | 48 hours          |
| Need temporary elevated permissions           | Super admin + justification      | 24 hours          |

### **Escalation Email Template**

```
Subject: Permission Request - [Your Name] - [Date]

Role: [Your current role]
Request: [Specific permission needed]
Reason: [Business justification]
Urgency: [Low/Medium/High]
Affected Users: [If applicable]

Example Action:
- Current: I get "Access Denied" when trying to [specific action]
- Needed: Temporary admin access to [specific table/feature]
- Duration: [How long you need elevated access]

Thank you,
[Your Name]
```

---

## 📚 **Examples & Scenarios**

### **Scenario 1: Guide Can't See Booking**

**Problem:** Guide reports they can't see a booking for their tour.

**Troubleshooting:**
1. Verify the booking exists (admin checks `bookings` table)
2. Confirm booking's `guide_id` matches the guide's `user_id`
3. Check security policy `guides_read_own_bookings` is active
4. If data mismatch: Update booking's `guide_id` (admin action)

**Root Cause:** Usually a data entry error where booking was created without proper `guide_id` reference.

---

### **Scenario 2: Admin Can't Edit User Role**

**Problem:** Admin tries to promote a guide to admin but gets "Permission Denied."

**Expected Behavior:** Only super admins can change roles (security audit requirement from August 23, 2025).

**Solution:**
1. Admin emails super admin with request
2. Super admin verifies request is legitimate
3. Super admin updates role via User Management page
4. System sends audit log entry

**Why:** Role changes are high-risk. Centralized control prevents privilege escalation attacks.

---

### **Scenario 3: Blogger Sees "Insufficient Permissions"**

**Problem:** Blogger tries to edit another blogger's post.

**Expected Behavior:** security policy `bloggers_update_own_posts` restricts updates to posts where `author_id = user.id`.

**Solution:**
1. Verify blogger is trying to edit someone else's post
2. If legitimate need: Contact admin to edit post
3. If unauthorized: Remind blogger of role boundaries

**Why:** Content ownership prevents accidental overwrites.

---

## 🔍 **Quick Reference: Permission Flowchart**

```
Need to perform an action?
    |
    ├─ Is it within your role? (Check RBAC matrix)
    |   ├─ YES → Proceed with action
    |   └─ NO → Escalate to higher role
    |
    ├─ Do you get "Access Denied"?
    |   ├─ YES → Check security policies (contact engineering)
    |   └─ NO → Action successful
    |
    └─ Unsure if authorized?
        └─ Ask supervisor BEFORE attempting
```

---

## 📖 **Additional Resources**

- **Security Audit (August 23, 2025):** Original source of security requirements
- **Platform Security Documentation:** Contact engineering team for technical details
- **User Role Change Log:** Contact super admin for access

---

## 🎓 **Knowledge Check**

Test your understanding:

1. Can a guide view another guide's bookings? **NO - security prevents this**
2. Who can change user roles? **Only super_admin**
3. What should you do if you get "Access Denied" for a legitimate action? **Email hello@letsgobelize.app with details**
4. Can admin users edit security policies? **NO - Only engineering can modify security**
5. What's the refund limit for regular admins? **established limit USD**

✅ **If you answered 4/5 correctly, proceed to Module 02. Otherwise, re-read the RBAC Matrix.**

---

**Next Module:** [02: Onboarding Admins & Invitations](02-Onboarding-Admins-Invitations.md) →

# LetsGoBelize.app Admin Training Manual

**Version 1.0** | **Last Updated:** October 8, 2025
**Target Audience:** Non-developer administrators, power users, and operations staff

---

## 📚 **Welcome to Your Admin Training Manual**

This manual is your complete guide to safely managing LetsGoBelize.app's backend operations. You don't need to be a developer—just follow the step-by-step procedures, checklists, and safety guardrails provided.

### **What This Manual Covers**

This training system teaches you how to:
- Manage tours, bookings, and payments securely
- Send safety alerts to travelers
- Handle WhatsApp communications professionally
- Monitor the AI Concierge system
- Perform monthly financial close procedures
- Respond to incidents and escalate when needed

---

## 🎯 **Prerequisites**

Before using this manual, ensure you have:

- [ ] Admin account credentials for LetsGoBelize.app
- [ ] Access to the Admin Dashboard at `/dashboard`
- [ ] Your assigned role: `super_admin`, `admin`, `blogger`, or `guide`
- [ ] Basic computer skills (web browsing, form filling)
- [ ] Read this ReadMe completely

**⚠️ Important:** Never share your login credentials with anyone.

---

## 🧭 **How to Use This Manual**

### **Module Structure**

Each training module follows this format:

1. **PURPOSE** - Why this task matters for operations
2. **WHEN TO USE** - Trigger scenarios requiring this procedure
3. **STEP-BY-STEP** - Numbered instructions (no technical jargon)
4. **DO / DO NOT** - Safety guardrails to prevent mistakes
5. **CHECKLIST** - Verification steps before completion
6. **ESCALATION** - When to contact engineering support

### **Quick Reference System**

- **Module 01-15:** Detailed training for each admin function
- **Appendix A-B:** Reference tables and glossary
- **Quick Cards:** One-page cheat sheets for common tasks
- **Checklists:** Daily/weekly/monthly verification lists
- **Templates:** Standardized forms for incidents and reports

### **Color-Coded Callouts**

Throughout this manual, you'll see:

- ⚠️ **Caution:** Action requires extra care or approval
- 💡 **Tip:** Helpful shortcut or best practice
- ✅ **Success:** Expected outcome after completing step
- 🚨 **Emergency:** Critical security or safety issue

---

## 👥 **Role Matrix**

Your permissions depend on your assigned role:

| **Role**        | **Can Do**                                                                                       | **Cannot Do**                                     |
|-----------------|--------------------------------------------------------------------------------------------------|---------------------------------------------------|
| **super_admin** | Everything (user management, tours, bookings, payments, alerts, database, AI governance)         | N/A (full access)                                 |
| **admin**       | Tours, bookings, payments, alerts, blog posts, analytics                                         | User role changes, database schema, RLS policies  |
| **blogger**     | Create/edit/publish blog posts, view analytics                                                   | Tours, bookings, payments, user management        |
| **guide**       | Create/edit own tours, view own bookings, upload images                                          | Other guides' content, payments, alerts           |
| **traveler**    | Book tours, view own bookings, manage profile                                                    | Backend dashboard access                          |

💡 **Tip:** If you need permissions beyond your role, contact your super admin via email.

---

## 🗺️ **Environment Map**

LetsGoBelize.app operates in three environments:

| **Environment** | **Purpose**                      | **URL**                        | **Data**           |
|-----------------|----------------------------------|--------------------------------|--------------------|
| **Production**  | Live customer-facing platform    | `https://letsgobelize.app`     | Real customer data |
| **Staging**     | Testing before production deploy | `https://staging.letsgobelize.app` | Test data only     |
| **Development** | Local testing (engineering only) | `http://localhost:5173`        | Mock data          |

⚠️ **Caution:** All procedures in this manual apply to **PRODUCTION** unless explicitly stated otherwise.

---

## 📖 **Glossary Quick Reference**

Common terms you'll encounter:

- **RLS (Row Level Security):** Database security that controls who can view/edit data
- **Supabase:** The database and backend system powering LetsGoBelize.app
- **Stripe Connect:** Payment processing system for tour guide payouts
- **Edge Functions:** Server-side code that runs automated tasks
- **WhatsApp Business API:** System for sending booking confirmations and alerts
- **AI Concierge:** GPT-4 powered assistant helping travelers plan trips

📚 **Full Glossary:** See [Appendix B: Glossary](#appendix-b-glossary.md) for complete definitions.

---

## 🚨 **Emergency Contacts**

**Before starting any admin task, save these contacts:**

| **Issue Type**              | **Contact**                              | **Response Time** |
|-----------------------------|------------------------------------------|-------------------|
| Security Incident           | security@letsgobelize.app                | 15 minutes        |
| Payment/Stripe Issues       | payments@letsgobelize.app                | 1 hour            |
| Database Errors             | engineering@letsgobelize.app             | 30 minutes        |
| WhatsApp API Down           | support@letsgobelize.app                 | 2 hours           |
| AI Concierge Malfunction    | ai-support@letsgobelize.app              | 1 hour            |
| General Admin Questions     | hello@letsgobelize.app                   | 24 hours          |

⚠️ **For life-threatening emergencies (traveler safety), call local emergency services FIRST (911 in Belize), then notify security@letsgobelize.app.**

---

## 📋 **Training Module Index**

### **Core Operations**
- [Module 01: Roles, Permissions & RLS](01-Roles-Permissions-RLS.md)
- [Module 02: Onboarding Admins & Invitations](02-Onboarding-Admins-Invitations.md)
- [Module 03: Tours Management](03-Tours-Management.md)
- [Module 04: Bookings Flow & Operations](04-Bookings-Flow-Operations.md)
- [Module 05: Payments & Stripe Connect](05-Payments-Stripe-Connect.md)

### **Safety & Communications**
- [Module 06: Safety Alerts Runbook](06-Safety-Alerts-Runbook.md)
- [Module 07: WhatsApp Operations](07-WhatsApp-Operations.md)

### **AI & Content Management**
- [Module 08: AI Assistant Governance](08-AI-Assistant-Governance.md)
- [Module 09: Storage, Images & Files](09-Storage-Images-Files.md)

### **Analytics & Reporting**
- [Module 10: Analytics & Insights Dashboard](10-Analytics-Insights-Dashboard.md)

### **Technical Safeguards**
- [Module 11: Security & Compliance](11-Security-Compliance.md)
- [Module 12: Backups & Disaster Recovery](12-Backups-Disaster-Recovery.md)
- [Module 13: Release & Change Control](13-Release-Change-Control.md)

### **Problem Solving**
- [Module 14: Troubleshooting Playbook](14-Troubleshooting-Playbook.md)
- [Module 15: Checklists & Templates](15-Checklists-and-Templates.md)

### **Reference Materials**
- [Appendix A: APIs & Objects](appendix-A-APIs-and-Objects.md)
- [Appendix B: Glossary](appendix-B-Glossary.md)
- [Mermaid Backend Flows](mermaid-backend-flows.md)

### **Quick Access Tools**
- [Quick Cards: Operations Laminates](quick-cards/ops-laminates.md)
- [Checklist: Month-End Close](checklists/month-end-close.md)
- [Checklist: Incident Response](checklists/incident-response.md)
- [Template: Post-Incident Report](templates/post-incident-report.md)

---

## 🎓 **Learning Path Recommendations**

### **New Admins (Week 1)**
1. Read this ReadMe completely
2. Complete Module 01 (Roles & Permissions)
3. Complete Module 03 (Tours Management)
4. Complete Module 04 (Bookings Flow)
5. Shadow an experienced admin for 1 day

### **Week 2**
1. Complete Module 05 (Payments)
2. Complete Module 06 (Safety Alerts)
3. Complete Module 07 (WhatsApp Operations)
4. Practice with test data in staging environment

### **Week 3**
1. Complete Module 08 (AI Governance)
2. Complete Module 10 (Analytics)
3. Complete Module 14 (Troubleshooting)
4. Handle real tasks with supervisor oversight

### **Ongoing**
- Review Module 11 (Security) monthly
- Practice incident response (Module 15) quarterly
- Attend admin team meetings for updates

---

## ✅ **Certification Checklist**

Before operating independently, verify you can:

- [ ] Log into Admin Dashboard securely
- [ ] Create and publish a tour correctly
- [ ] Process a booking from start to completion
- [ ] Issue a refund through Stripe Dashboard
- [ ] Send a safety alert to specific travelers
- [ ] Explain when to escalate to engineering
- [ ] Follow month-end close procedure
- [ ] Respond to a simulated incident properly

💡 **Tip:** Ask your supervisor to sign off on each skill before going solo.

---

## 📞 **Getting Help**

**Stuck on a procedure?**

1. Re-read the relevant module's ESCALATION section
2. Check the Troubleshooting Playbook (Module 14)
3. Ask a fellow admin in your team chat
4. Email hello@letsgobelize.app with:
   - Your name and role
   - Which module you're working on
   - Specific step where you're stuck
   - Screenshot (if applicable)

**Response times:**
- **Urgent (production down):** 15-30 minutes
- **Important (user impact):** 1-2 hours
- **General questions:** 24 hours

---

## 🔄 **Manual Updates**

This manual is updated quarterly. Current version: **1.0 (October 2025)**

**Change log:**
- **v1.0 (Oct 2025):** Initial release covering all backend operations

💡 **Tip:** Bookmark this page and check the version number monthly to ensure you're using the latest procedures.

---

## 📜 **Safety Pledge**

By using this manual, you agree to:

1. **Never guess** - Always follow documented procedures
2. **Ask first** - Escalate when uncertain rather than experiment
3. **Test in staging** - Never try new procedures in production first
4. **Protect data** - Treat all customer information as confidential
5. **Report incidents** - Notify security@letsgobelize.app immediately for breaches
6. **Stay current** - Complete refresher training when manual updates release

---

**Ready to begin?** Start with [Module 01: Roles, Permissions & RLS](01-Roles-Permissions-RLS.md) →

---

**Questions?** Email: hello@letsgobelize.app
**Training Coordinator:** admin-training@letsgobelize.app

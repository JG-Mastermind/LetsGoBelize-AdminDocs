# Incident Response Checklist

**Emergency Procedures for Security and Operations Incidents**

Use this checklist when a security breach, data loss, or critical operations failure occurs.

---

## 🚨 **When to Use This Checklist**

Activate incident response for:

### **Security Incidents:**
- Unauthorized account access
- Data breach or exposure
- Ransomware or malware attack
- Compromised API keys
- Suspicious admin actions
- Customer reports identity theft

### **Operations Incidents:**
- Database downtime > 15 minutes
- Payment processing failures
- WhatsApp API complete outage
- Mass booking cancellations
- Safety alert system failure
- Website completely unreachable

### **Data Incidents:**
- Accidental data deletion
- Incorrect bulk updates
- Data corruption
- Backup restoration needed

⚠️ **If life-threatening:** Call 911 FIRST, then proceed with checklist.

---

## ⏱️ **Phase 1: IMMEDIATE RESPONSE (0-15 minutes)**

### **Step 1: Stop the Bleeding**

**Time Limit:** 5 minutes

- [ ] **Contain incident:** Take immediate action to prevent further damage:
  - Security breach → Disable compromised accounts
  - Data corruption → Stop all write operations
  - API failure → Switch to manual backup processes
  - Mass error → Pause automated systems

- [ ] **Document start time:** Record exact time incident detected: [HH:MM AM/PM]

- [ ] **Screenshot evidence:** Capture error messages, logs, dashboards (before they disappear)

⚠️ **DO NOT:**
- ❌ Try to "fix" without understanding root cause (may worsen issue)
- ❌ Delete error logs or evidence
- ❌ Communicate with users yet (coordinate messaging first)

---

### **Step 2: Activate Incident Commander**

**Time Limit:** 2 minutes

- [ ] Determine incident severity:

| **Severity** | **Definition**                       | **Commander**          | **Response Time** |
|--------------|--------------------------------------|------------------------|-------------------|
| **P0**       | Critical - platform down, data loss | CTO                    | Immediate (call)  |
| **P1**       | Major - core features broken         | Super admin            | 15 minutes        |
| **P2**       | Moderate - degraded service          | Operations manager     | 1 hour            |
| **P3**       | Minor - isolated issue               | Senior admin           | 4 hours           |

- [ ] Contact Incident Commander via:
  - P0/P1: Phone call (do not wait for email)
  - P2/P3: Slack #emergency-response channel + email

- [ ] Report initial assessment:
  ```
  INCIDENT: [Brief headline]
  SEVERITY: [P0/P1/P2/P3]
  START TIME: [Timestamp]
  AFFECTED: [Users/systems/features]
  CONTAINMENT: [Actions taken]
  REPORTER: [Your name]
  ```

---

### **Step 3: Notify Stakeholders**

**Time Limit:** 5 minutes

- [ ] Alert core response team via Slack #emergency-response:
  - Operations team
  - Engineering on-call
  - Customer support lead
  - Finance (if payment-related)

- [ ] **DO NOT notify customers yet** (wait for coordinated messaging)

- [ ] Create incident war room:
  - Zoom/Slack huddle for P0/P1
  - Slack thread for P2/P3

---

### **Step 4: Preserve Evidence**

**Time Limit:** 3 minutes

- [ ] Screenshot all error messages
- [ ] Export relevant logs (before they rotate):
  - Database logs
  - Application logs
  - API request logs
  - WhatsApp delivery logs
- [ ] Note which users/accounts affected
- [ ] Save system state snapshots

---

## 🔍 **Phase 2: ASSESSMENT (15-45 minutes)**

### **Step 1: Root Cause Analysis**

- [ ] Gather facts (do not speculate):
  - What exactly happened?
  - When did it start?
  - What triggered it? (code deploy, manual action, external API)
  - How many users affected?
  - What data exposed/corrupted?

- [ ] Check recent changes:
  - [ ] Code deployments in last 24 hours
  - [ ] Database migrations in last 7 days
  - [ ] Admin actions in last hour (check audit log)
  - [ ] External API status pages (Stripe, WhatsApp, Supabase)

- [ ] Reproduce issue (in staging if possible):
  - Can you trigger the issue intentionally?
  - Does it happen consistently or intermittently?

---

### **Step 2: Impact Assessment**

Calculate blast radius:

- [ ] **Users affected:**
  - Total count: [X]
  - Roles: [travelers/guides/admins]
  - Geographic distribution: [areas]

- [ ] **Systems affected:**
  - [ ] Website/frontend
  - [ ] Admin dashboard
  - [ ] Mobile apps
  - [ ] Database
  - [ ] Payment processing
  - [ ] Email/SMS/WhatsApp
  - [ ] AI Concierge

- [ ] **Data affected:**
  - [ ] Customer PII exposed? (CRITICAL)
  - [ ] Payment data exposed? (CRITICAL)
  - [ ] Bookings lost/corrupted?
  - [ ] Tours data corrupted?

- [ ] **Revenue impact:**
  - Estimated lost bookings: $[X]
  - Refunds required: $[X]
  - Downtime cost: $[X/hour]

---

### **Step 3: Determine Recovery Path**

- [ ] Identify fix options:

| **Option**           | **Time to Fix** | **Risk** | **Impact** |
|----------------------|-----------------|----------|------------|
| Rollback deployment  | 15 min          | Low      | [Impact]   |
| Database restore     | 1-2 hours       | Medium   | [Impact]   |
| Hotfix patch         | 2-4 hours       | Medium   | [Impact]   |
| Full rebuild         | 8+ hours        | High     | [Impact]   |

- [ ] Choose fastest, lowest-risk option
- [ ] Get Incident Commander approval
- [ ] Assign owner: [Name]
- [ ] Set target resolution time: [HH:MM]

---

## 🔧 **Phase 3: RESOLUTION (45 minutes - 4 hours)**

### **Step 1: Execute Fix**

- [ ] Implement approved solution
- [ ] Test in staging first (if P2/P3)
- [ ] Document every step taken (for post-mortem)
- [ ] Monitor systems during fix application

---

### **Step 2: Verify Resolution**

- [ ] **Smoke tests** (quick checks):
  - [ ] Website loads correctly
  - [ ] Users can log in
  - [ ] Bookings process successfully
  - [ ] Payments work end-to-end
  - [ ] WhatsApp sending
  - [ ] Dashboard functional

- [ ] **Data integrity checks:**
  - [ ] Run database consistency checks
  - [ ] Verify backups are current
  - [ ] Confirm no data loss

- [ ] **User acceptance:**
  - [ ] Ask 2-3 affected users to test
  - [ ] Verify they can complete critical workflows

---

### **Step 3: Communicate All-Clear**

- [ ] **Internal announcement** (Slack #emergency-response):
  ```
  INCIDENT RESOLVED: [Headline]
  
  FIX APPLIED: [Brief description]
  RESOLUTION TIME: [Duration]
  IMPACT: [Summary]
  NEXT STEPS: [Post-mortem scheduled]
  
  Systems are now stable. Resume normal operations.
  ```

- [ ] **Customer communication** (if customers were affected):

**For website downtime:**
  ```
  Subject: Service Restored - LetsGoBelize.app

  Hi [Customer Name],

  Our platform experienced a brief service disruption between [Start Time] and [End Time] on [Date]. 

  IMPACT: [What customers experienced]
  RESOLUTION: All systems are now fully operational.
  
  If you experienced issues with bookings during this time, please contact us at hello@letsgobelize.app for assistance.

  We apologize for the inconvenience.

  LetsGoBelize.app Team
  ```

**For data breach (CRITICAL):**
  ```
  Subject: URGENT - Security Incident Notification

  Hi [Customer Name],

  We are writing to inform you of a security incident that may have affected your account.

  WHAT HAPPENED: [Specific details]
  DATA AFFECTED: [What data was exposed]
  ACTIONS WE TOOK: [Immediate response]
  ACTIONS YOU SHOULD TAKE: 
  - Change your password immediately
  - Monitor your accounts for suspicious activity
  - [Additional steps]

  We take your privacy seriously and have implemented additional safeguards to prevent future incidents.

  For questions: security@letsgobelize.app

  LetsGoBelize.app Security Team
  ```

---

## 📋 **Phase 4: POST-INCIDENT (24-48 hours after resolution)**

### **Step 1: Schedule Post-Mortem**

- [ ] Set meeting within 48 hours
- [ ] Invite participants:
  - [ ] Incident Commander
  - [ ] All responders
  - [ ] Engineering lead
  - [ ] Operations manager
  - [ ] Customer support lead

---

### **Step 2: Complete Post-Incident Report**

Use template: [templates/post-incident-report.md](../templates/post-incident-report.md)

Required sections:
- [ ] Executive summary (3-5 sentences)
- [ ] Timeline of events (minute-by-minute)
- [ ] Root cause analysis
- [ ] Impact assessment (users, revenue, data)
- [ ] Response evaluation (what went well/poorly)
- [ ] Action items (prevent recurrence)
- [ ] Recommendations

**Submit to:** security@letsgobelize.app + CTO

---

### **Step 3: Implement Preventative Measures**

From post-mortem action items:

- [ ] Update monitoring/alerting
- [ ] Improve documentation
- [ ] Add automated tests
- [ ] Update runbooks
- [ ] Schedule training
- [ ] Revise incident response checklist (this document)

**Track in:** Project management system with owners and deadlines

---

## ⚠️ **Special Incident Types**

### **Data Breach (CRITICAL)**

Additional steps REQUIRED:

- [ ] Notify CTO immediately (within 15 minutes)
- [ ] Preserve forensic evidence (do NOT modify logs)
- [ ] Contact legal counsel
- [ ] Prepare regulatory notifications (GDPR, local laws)
- [ ] Customer notification within 72 hours
- [ ] Offer credit monitoring (if payment data exposed)
- [ ] File incident reports with authorities

---

### **Payment Processing Failure**

- [ ] Switch to manual payment collection (if possible)
- [ ] Notify finance team
- [ ] Contact Stripe support
- [ ] Document all failed transactions
- [ ] Manually process payments when system restored
- [ ] Reconcile all transactions before month-end close

---

### **Database Corruption**

- [ ] Stop ALL write operations immediately
- [ ] Assess corruption extent (use DB integrity checks)
- [ ] Restore from most recent clean backup
- [ ] Replay transactions from write-ahead log (engineering only)
- [ ] Verify data integrity post-restoration
- [ ] Investigate root cause (disk failure, bad migration, etc.)

---

## 📞 **Emergency Contacts**

| **Role**              | **Contact**                     | **Phone**          |
|-----------------------|---------------------------------|--------------------|
| **Incident Commander (P0/P1)** | CTO                   | [Provided to admins] |
| **Engineering On-Call** | engineering@letsgobelize.app  | [Slack alert]      |
| **Operations Manager**  | ops@letsgobelize.app          | [Slack alert]      |
| **Security Team**       | security@letsgobelize.app     | [Emergency line]   |
| **Customer Support Lead** | support@letsgobelize.app    | [Slack alert]      |
| **Finance Team**        | finance@letsgobelize.app      | [Business hours]   |

**After-Hours:** Check Slack #emergency-response for on-call rotation

---

## ✅ **Incident Resolution Sign-Off**

Complete this before closing incident:

- [ ] Root cause identified and documented
- [ ] Fix implemented and verified
- [ ] All affected users notified
- [ ] Post-incident report scheduled
- [ ] Action items created and assigned
- [ ] Incident closed in tracking system

**Incident Commander Sign-Off:**

Name: __________________________
Date/Time: ______________________
Signature: _______________________

---

**Checklist Version:** 1.0
**Last Updated:** October 8, 2025
**Next Review:** Quarterly

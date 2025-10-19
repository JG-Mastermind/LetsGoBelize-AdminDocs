# Post-Incident Report Template

**Complete within 48 hours of incident resolution**

---

## 📋 **Incident Metadata**

| **Field**                | **Value** |
|--------------------------|-----------|
| Incident ID              | INC-[YYYY-MM-DD]-[###] |
| Incident Title           | [Brief descriptive headline] |
| Severity                 | P0 / P1 / P2 / P3 |
| Start Time               | [YYYY-MM-DD HH:MM TZ] |
| Detection Time           | [YYYY-MM-DD HH:MM TZ] |
| Resolution Time          | [YYYY-MM-DD HH:MM TZ] |
| Total Duration           | [X hours Y minutes] |
| Incident Commander       | [Name, Role] |
| Report Author            | [Name, Role] |
| Report Date              | [YYYY-MM-DD] |

---

## 📝 **Executive Summary**

**[Write 3-5 sentences for non-technical stakeholders]**

Example:
> On October 8, 2025, between 2:15 PM and 4:30 PM BZT, the LetsGoBelize.app booking system experienced a complete outage affecting all customers attempting to book tours. The incident was caused by a database migration that introduced a schema conflict with the booking API. The engineering team rolled back the migration and restored full service within 2 hours and 15 minutes. Approximately 47 customers were impacted, resulting in an estimated $3,200 in lost bookings. All affected customers were notified and offered 10% discount codes for future bookings.

---

## 🕐 **Timeline of Events**

**Format:** [HH:MM TZ] - [Event description] - [Person/Team]

```
14:00 - Database migration deployed to production - Engineering Team
14:10 - Migration completed successfully (no errors logged) - Engineering Team
14:15 - First customer booking failure reported via support email - Customer Support
14:17 - Second and third booking failures reported - Customer Support
14:18 - Operations admin attempted manual booking (failed) - Operations Team
14:20 - Incident declared (P1 severity) - Operations Manager
14:22 - Engineering on-call notified via Slack - Operations Manager
14:25 - Database logs reviewed, schema conflict identified - Engineering Team
14:30 - Incident escalated to P0 (entire booking system down) - Incident Commander
14:32 - Rollback decision approved - CTO
14:35 - Migration rollback initiated - Engineering Team
14:42 - Rollback completed, database schema restored - Engineering Team
14:45 - Smoke tests: Booking API operational - Engineering Team
14:50 - First successful customer booking confirmed - Customer Support
15:00 - Monitoring: All systems green, no errors - Operations Team
15:15 - Customer notification email drafted - Customer Support
15:30 - Customer notification email sent to 47 affected users - Customer Support
16:30 - Incident status: Resolved (monitoring continues) - Incident Commander
```

---

## 🔍 **Root Cause Analysis**

### **What Happened:**
[Detailed technical explanation of the incident]

Example:
> A database migration (migration #20251008_141000) added a new NOT NULL column `tour_availability` to the `bookings` table without providing a default value. The booking API immediately began failing when attempting INSERT operations because it did not include this new required column in its queries. The migration script passed all pre-deployment tests in staging because staging data already had values for this column (manually populated during testing), masking the production issue.

---

### **Why It Happened:**
[Root cause - not just proximate cause]

Example:
> **Immediate Cause:** Missing default value in schema migration.
>
> **Contributing Factors:**
> 1. Staging environment data was manually modified, creating a mismatch with production
> 2. Migration lacked a two-phase deployment (add column with default → populate data → make NOT NULL)
> 3. Booking API integration tests did not cover newly added columns
> 4. No pre-deployment validation against production schema snapshot
>
> **Root Cause:** Inadequate testing procedures for database schema changes affecting critical APIs.

---

### **Why It Wasn't Detected Earlier:**
[Gaps in monitoring, testing, or processes]

Example:
> - Staging environment diverged from production (manual data changes)
> - Integration tests used mocked database responses (did not hit real schema)
> - No automated schema diff comparison between staging and production
> - Monitoring alerts configured for 500 errors only (booking failures returned 400 Bad Request)

---

## 📊 **Impact Assessment**

### **Users Affected:**
- **Total Users:** 47 customers
- **User Types:** Travelers attempting to book tours
- **Geographic Distribution:** 35 USA, 8 Canada, 4 UK
- **Critical Users:** 2 VIP corporate partners (contacted directly)

---

### **Systems Affected:**
- **Primary:** Booking API (complete outage)
- **Secondary:** Admin Dashboard booking module (manual bookings failed)
- **Unaffected:** Website browsing, tour pages, user logins, AI Concierge

---

### **Data Affected:**
- **Data Loss:** None (no bookings were corrupted or deleted)
- **Data Exposure:** None (no security breach)
- **Orphaned Transactions:** 12 incomplete Stripe payment intents (refunded automatically)

---

### **Revenue Impact:**
- **Lost Bookings:** 47 customers × avg $68/booking = ~$3,200 lost revenue (estimated)
- **Refunds Issued:** $0 (no completed bookings during outage)
- **Discount Codes Issued:** 47 × 10% = potential $320 revenue reduction on future bookings
- **Total Estimated Loss:** $3,520

---

### **Reputational Impact:**
- **Customer Complaints:** 8 emails, 3 social media mentions
- **Media Coverage:** None
- **Review Impact:** 1 negative Google review citing "website broken"
- **Trust Score:** Monitoring for drop in conversion rates (review in 7 days)

---

## 🏆 **What Went Well**

1. **Fast Detection:** Incident detected within 5 minutes of first failure
2. **Clear Communication:** Incident Commander kept team informed via Slack war room
3. **Quick Rollback:** Engineering team executed rollback in 7 minutes (within target)
4. **Customer Outreach:** All affected customers notified within 1 hour of resolution
5. **Coordination:** Operations, engineering, and support teams collaborated effectively

---

## 🚨 **What Went Poorly**

1. **Inadequate Testing:** Migration tested in non-representative staging environment
2. **Delayed Escalation:** Initial P1 classification delayed P0 response by 10 minutes
3. **Manual Monitoring:** Relied on customer reports instead of automated error alerts
4. **Documentation Gap:** No runbook for database migration rollback procedures
5. **Recovery Time:** 2h 15m exceeded our 1-hour RTO target for critical systems

---

## ✅ **Action Items**

| **Action** | **Owner** | **Deadline** | **Status** | **Priority** |
|------------|-----------|--------------|------------|--------------|
| Update migration checklist to require schema diff review | Engineering Lead | Oct 15 | Open | P0 |
| Implement automated schema validation in CI/CD pipeline | DevOps | Oct 22 | Open | P0 |
| Add booking API error monitoring (400/500 status codes) | Engineering | Oct 12 | Open | P1 |
| Create database migration rollback runbook | Engineering | Oct 18 | Open | P1 |
| Refresh staging database from production snapshot weekly | DevOps | Oct 10 | Open | P1 |
| Review and update RTO/RPO targets for critical systems | CTO | Oct 25 | Open | P2 |
| Conduct incident response training for ops team | Operations Manager | Nov 1 | Open | P2 |
| Send apology email + survey to affected customers | Customer Support | Oct 9 | Open | P3 |

---

## 💡 **Lessons Learned**

### **Process Improvements:**
1. **Two-Phase Schema Changes:** All NOT NULL column additions must follow add-with-default → populate → enforce pattern
2. **Staging Parity:** Automated weekly refresh of staging data from production
3. **Pre-Deployment Validation:** Schema diff review mandatory for all database changes

---

### **Technical Improvements:**
1. **Monitoring Gaps:** Expand error alerting beyond 500 errors to include 400 Bad Request
2. **Integration Testing:** Use real database (not mocks) in critical API tests
3. **Automated Rollback:** Implement one-click rollback for database migrations

---

### **Communication Improvements:**
1. **Severity Escalation:** Update severity classification guide to escalate faster
2. **Customer Notifications:** Pre-draft incident notification templates for common scenarios
3. **Status Page:** Implement public status page (status.letsgobelize.app) for transparency

---

## 🔒 **Security Considerations**

### **Was this a security incident?**
☐ Yes  ☑ No

**Explanation:**
> No customer data was exposed, corrupted, or accessed improperly. The incident was purely operational (booking system downtime) with no security implications.

---

### **Customer Data Handling:**
- **PII Accessed:** None
- **Payment Data Accessed:** None
- **Regulatory Notifications Required:** No (GDPR, CCPA, etc.)

---

## 📄 **Attachments**

1. Database migration script: `20251008_141000_add_tour_availability.sql`
2. Error logs: `booking_api_errors_2025-10-08.log`
3. Rollback script: `20251008_141000_rollback.sql`
4. Customer notification email: `incident_notification_2025-10-08.txt`
5. Slack war room transcript: `incident_war_room_2025-10-08.txt`

---

## ✍️ **Sign-Off**

### **Report Reviewed By:**

| **Role**              | **Name**          | **Date**       | **Signature** |
|-----------------------|-------------------|----------------|---------------|
| Incident Commander    | [Name]            | [YYYY-MM-DD]   | ____________  |
| Engineering Lead      | [Name]            | [YYYY-MM-DD]   | ____________  |
| Operations Manager    | [Name]            | [YYYY-MM-DD]   | ____________  |
| CTO (Final Approval)  | [Name]            | [YYYY-MM-DD]   | ____________  |

---

### **Post-Mortem Meeting:**
- **Date/Time:** [YYYY-MM-DD HH:MM]
- **Attendees:** [Names]
- **Meeting Notes:** [Link to notes or attach separately]

---

**Report Distribution:**
- [ ] Incident response team
- [ ] Engineering team
- [ ] Operations team
- [ ] Customer support team
- [ ] Finance team (if revenue impact)
- [ ] Executive leadership
- [ ] Filed in: `/docs/incident-reports/[YYYY]/`

---

**Report Version:** 1.0
**Template Last Updated:** October 8, 2025

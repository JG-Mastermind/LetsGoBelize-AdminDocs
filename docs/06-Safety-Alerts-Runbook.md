# Module 06: Safety Alerts Runbook

**Module Duration:** 90 minutes | **Difficulty:** Advanced
**Prerequisites:** Module 01 completed, admin or super_admin role REQUIRED

---

## 🎯 **PURPOSE**

Safety alerts can save lives. This module teaches you how to:
- Quickly broadcast emergency alerts to travelers
- Target alerts by location, tour type, or specific groups
- Handle weather emergencies, security threats, and medical situations
- Roll back or expire alerts when danger passes
- Document incidents for post-mortem analysis

⚠️ **CRITICAL:** Safety alerts are high-stakes. Read this module completely before sending your first alert.

---

## ⏰ **WHEN TO USE**

Send safety alerts for:
- **Weather:** Hurricane warnings, tropical storms, flash flood alerts
- **Security:** Civil unrest, crime spikes, travel advisories
- **Health:** Disease outbreaks, water quality issues, food safety warnings
- **Infrastructure:** Road closures, power outages, communication disruptions
- **Missing Person:** Traveler overdue from tour, lost hiker
- **Wildlife:** Dangerous animal sightings, beach closures due to jellyfish

⚠️ **DO NOT use for:** Marketing messages, general announcements, tour promotions (use email campaigns instead).

---

## 📊 **SEVERITY LEVELS**

| **Level**    | **Color** | **Icon** | **Use Case**                              | **Notification Method**        |
|--------------|-----------|----------|-------------------------------------------|--------------------------------|
| `info`       | Blue      | ℹ️       | General advisories, minor disruptions     | Email only                     |
| `warning`    | Yellow    | ⚠️       | Developing situation, heightened caution  | Email + SMS                    |
| `critical`   | Red       | 🚨       | Immediate danger, life-threatening        | WhatsApp + SMS + Email + Push  |
| `emergency`  | Purple    | ⚡       | Active crisis, evacuation orders          | All channels + Phone calls     |

💡 **Tip:** When uncertain about severity, choose higher level. Over-alerting is better than under-alerting.

---

## 🛠️ **STEP-BY-STEP: Send Safety Alert**

### **Phase 1: Assess Situation (5 minutes)**

#### **Step 1: Verify Threat**

Before sending alert, confirm threat is real:

**Reliable Sources:**
- [ ] National Emergency Management Organization (NEMO) Belize
- [ ] U.S. Embassy Belize alerts
- [ ] Belize Meteorological Service
- [ ] Local police/fire departments
- [ ] Verified news outlets (Channel 5 Belize, Breaking Belize News)

⚠️ **DO NOT use:** Social media rumors, unverified WhatsApp forwards, tourist panic.

**Verification Checklist:**
- [ ] Threat confirmed by 2+ official sources
- [ ] Geographic scope identified (which areas affected)
- [ ] Timeline established (when threat begins/ends)
- [ ] Severity assessed (info/warning/critical/emergency)

---

#### **Step 2: Identify Affected Travelers**

Determine who needs alert:

**By Location:**
- All travelers in Ambergris Caye
- All travelers in San Ignacio area
- All travelers currently on tours
- All travelers arriving in next 48 hours

**By Tour Type:**
- All water-based tours (for marine warnings)
- All jungle tours (for wildlife alerts)
- All cave tours (for weather-related closures)

**By Severity:**
- Critical/Emergency: Alert everyone in affected area
- Warning: Alert travelers with tours in next 72 hours
- Info: Alert travelers with tours in next week

---

### **Phase 2: Draft Alert Message (10 minutes)**

#### **Message Template Structure**

```
[SEVERITY EMOJI] [ALERT TYPE]: [BRIEF HEADLINE]

SITUATION:
[What is happening, 1-2 sentences]

AFFECTED AREAS:
[Specific locations]

ACTIONS TO TAKE:
- [Action 1]
- [Action 2]
- [Action 3]

TIMELINE:
[When alert is effective, when it expires]

CONTACT:
For questions: [emergency contact number]

---
LetsGoBelize.app Safety Team
Sent: [timestamp]
```

---

#### **Example 1: Hurricane Warning (Critical)**

```
🚨 CRITICAL ALERT: Hurricane Lisa Approaching Belize Coast

SITUATION:
Hurricane Lisa (Category 2) expected to make landfall near Belize City on November 2 at 6 AM. Wind speeds 110 mph, storm surge 8-12 feet. All coastal areas under hurricane warning.

AFFECTED AREAS:
- Belize City
- Ambergris Caye
- Caye Caulker
- Placencia Peninsula
- All offshore cayes

ACTIONS TO TAKE:
- Seek shelter in concrete buildings IMMEDIATELY
- Stock 3 days of water, food, medications
- Secure loose items, board windows
- Stay indoors until all-clear issued
- DO NOT attempt water travel

TIMELINE:
Effective: November 1, 2025 at 2:00 PM
Expected to pass: November 3, 2025

CONTACT:
Emergency assistance: +501-EMERGENCY (24/7)

---
LetsGoBelize.app Safety Team
Sent: Nov 1, 2025 2:03 PM BZT
```

---

#### **Example 2: Road Closure (Warning)**

```
⚠️ WARNING: George Price Highway Closed Due to Accident

SITUATION:
Serious accident near Mile 47 has closed George Price Highway (Western Highway) in both directions. Traffic diverted to Hummingbird Highway.

AFFECTED AREAS:
- Travel between Belize City and San Ignacio
- Tours departing from Belize City to western Belize

ACTIONS TO TAKE:
- Add 90 minutes to travel time if using alternate route
- Contact your guide about pickup time adjustments
- If traveling today, confirm route with guide before departing

TIMELINE:
Effective: October 8, 2025 at 10:00 AM
Estimated reopening: 4:00 PM same day

CONTACT:
Route questions: hello@letsgobelize.app

---
LetsGoBelize.app Safety Team
Sent: Oct 8, 2025 10:15 AM BZT
```

---

#### **Example 3: Missing Traveler (Emergency)**

```
⚡ EMERGENCY: Missing Hiker - Maya Mountains

SITUATION:
Solo hiker (John Smith, 34, USA) overdue from Mountain Pine Ridge trail. Last contact: yesterday 3 PM. Search and rescue activated.

AFFECTED AREAS:
- Mountain Pine Ridge Forest Reserve
- All San Ignacio area tours

ACTIONS TO TAKE:
- If you saw a solo male hiker yesterday afternoon in Mountain Pine Ridge, call immediately
- All guides: Check your groups - report anyone separated from tour
- Do NOT conduct independent search - let professionals handle

DESCRIPTION:
Male, 34, white, 5'10", brown hair, wearing blue backpack, khaki pants, green Columbia jacket.

TIMELINE:
Effective: October 8, 2025 at 8:00 AM
UPDATE: Will send hourly updates

CONTACT:
Sightings/information: +501-XXX-XXXX (Search Coordinator)
Emergency: 911

---
LetsGoBelize.app Safety Team
Sent: Oct 8, 2025 8:05 AM BZT
```

---

### **Phase 3: Send Alert (5 minutes)**

#### **Dashboard UI Method**

1. Admin Dashboard → **"Safety Alerts"** → **"Create New Alert"** button

2. Fill alert form:

| **Field**              | **Instructions**                          |
|------------------------|-------------------------------------------|
| Alert Type             | Dropdown: Weather, Security, Health, Infrastructure, Missing Person, Wildlife |
| Severity               | Radio buttons: Info, Warning, Critical, Emergency |
| Headline               | 5-10 words, urgent and specific           |
| Message Body           | Use template from Phase 2                 |
| Affected Areas         | Multi-select: Ambergris Caye, San Ignacio, etc. |
| Target Audience        | Checkboxes: Current travelers, Upcoming bookings, All users |
| Expiration             | Date/time picker (when to auto-expire)    |
| Notification Channels  | Auto-selected based on severity           |

3. Click **"Preview Alert"** → Review on mobile device simulator

4. Verify:
   - [ ] No typos in message
   - [ ] Emergency contact numbers correct
   - [ ] Affected areas match situation
   - [ ] Expiration time appropriate
   - [ ] Notification channels correct for severity

5. Click **"Send Alert"** → Confirm in modal: "This will notify [X] travelers immediately"

6. System processes:
   - Inserts record in `safety_alerts` table
   - Queues notifications (WhatsApp, SMS, Email, Push)
   - Sends to affected users within 1-2 minutes
   - Creates audit log entry

✅ **Success:** Alert displays on traveler dashboards, notifications sent, status shows "active"

---

### **Phase 4: Monitor & Update (Ongoing)**

#### **Track Delivery**

1. Dashboard → **"Safety Alerts"** → Click alert ID → **"Delivery Status"** tab

Monitor metrics:
- **WhatsApp:** Delivered (✓✓), Read (✓✓ blue)
- **SMS:** Delivered, Failed (investigate)
- **Email:** Opened rate, click rate
- **Push:** Delivery rate

💡 **Red Flags:**
- < 80% delivery rate after 5 minutes → Check notification service
- High bounce rate (email/SMS) → Contact data issues
- No opens after 15 minutes → Follow up with phone calls (emergency only)

---

#### **Send Updates**

For ongoing situations (hurricanes, missing persons), send updates every 2-4 hours:

1. Click original alert → **"Send Update"** button
2. Message format:
   ```
   UPDATE [#2]: [Original Headline]

   [New developments, 2-3 sentences]

   CURRENT STATUS: [Description]

   NEXT UPDATE: [When you'll send next update]
   ```

3. Updates are grouped under original alert (threaded conversation)

---

### **Phase 5: Resolve Alert**

#### **When Danger Passes**

1. Dashboard → **"Safety Alerts"** → Find alert → **"Mark as Resolved"**

2. Send final "All Clear" message:
   ```
   ✅ RESOLVED: [Original Headline]

   The [threat type] affecting [area] has passed. It is now safe to [action].

   CURRENT STATUS: Normal operations resumed

   GUIDANCE:
   - [Any post-incident instructions]
   - [Damage assessment updates]

   Thank you for your patience and cooperation.

   ---
   LetsGoBelize.app Safety Team
   Sent: [timestamp]
   ```

3. System updates:
   - Alert status → "resolved"
   - Removes alert from active dashboard displays
   - Archives in alert history
   - Logs resolution time in audit

---

## 📋 **WhatsApp Broadcast Checklist**

For critical/emergency alerts, send via WhatsApp:

- [ ] Verify WhatsApp Business API credentials active
- [ ] Message template pre-approved by WhatsApp (24-hour requirement)
- [ ] Recipient list accurate (no test accounts in production list)
- [ ] Message < 1024 characters (WhatsApp limit)
- [ ] No prohibited content (violence, graphic images)
- [ ] Include opt-out instructions (legal requirement)
- [ ] Set appropriate send rate (max 100 messages/second to avoid throttling)

⚠️ **WhatsApp Policy:** Emergency alerts allowed without template pre-approval for life-threatening situations only.

---

## 🔄 **Rollback/Expire Alert**

### **When to Rollback**

Retract alert if:
- Alert sent in error (wrong area, wrong severity)
- Situation resolved faster than expected
- Better information reveals threat was overstated
- Technical error duplicated alert

### **Rollback Procedure**

1. Dashboard → **"Safety Alerts"** → Alert → **"⋮ More"** → **"Rollback Alert"**

2. Confirm reason:
   - "Sent in error"
   - "Situation resolved"
   - "Information corrected"
   - "Duplicate alert"

3. System immediately:
   - Sends retraction message: "ALERT RETRACTED: [Headline] - Reason: [...]"
   - Removes alert from active displays
   - Marks status as "retracted"
   - Logs rollback in audit (with admin name)

⚠️ **Caution:** Rollbacks are logged and reviewed quarterly. Frequent rollbacks indicate poor verification process.

---

## ⚠️ **DO / DO NOT**

### **DO:**

✅ **Verify threat with official sources**
- NEMO, U.S. Embassy, Belize Met Service
- Never rely on social media alone

✅ **Send alerts early**
- Better to over-alert than under-alert
- "When in doubt, send it out"

✅ **Use clear, actionable language**
- Tell travelers exactly what to do
- Avoid jargon or technical terms

✅ **Include emergency contacts**
- Local emergency numbers
- LetsGoBelize.app emergency hotline

✅ **Follow up with "all clear" messages**
- Don't leave travelers wondering if danger passed

---

### **DO NOT:**

❌ **Never send alerts based on rumors**
- Verify with 2+ official sources first
- Unverified alerts cause panic and lose trust

❌ **Never use alerts for marketing**
- "Flash sale" is not a safety alert
- Violates trust and legal regulations

❌ **Never delay critical alerts**
- Send within 5 minutes of verification
- Lives depend on timely information

❌ **Never send alerts without expiration**
- All alerts must have resolution plan
- Expired alerts clutter dashboards

❌ **Never share traveler contact info externally**
- Emergency responders get anonymized data only
- GDPR/privacy compliance requirement

---

## ✅ **VERIFICATION CHECKLIST**

Before sending alert:

- [ ] Threat verified by 2+ official sources
- [ ] Severity level appropriate
- [ ] Message follows template structure
- [ ] No typos or formatting errors
- [ ] Affected areas correct
- [ ] Emergency contacts verified
- [ ] Expiration time set
- [ ] Supervisor notified (critical/emergency only)

After sending:

- [ ] Delivery rate > 80% within 5 minutes
- [ ] No bounces or failed deliveries
- [ ] Alert displays on traveler dashboards
- [ ] Audit log entry created
- [ ] Follow-up plan documented

---

## 🚨 **ESCALATION**

| **Issue**                              | **Contact**                      | **Response Time** |
|----------------------------------------|----------------------------------|-------------------|
| WhatsApp broadcast failing             | support@letsgobelize.app         | 5 minutes (critical) |
| Unsure if situation warrants alert     | Super admin + CTO                | 10 minutes        |
| Alert sent to wrong recipients         | engineering@letsgobelize.app     | Immediate (rollback) |
| Missing traveler (life-threatening)    | 911 + security@letsgobelize.app  | Immediate         |
| Media inquiries about alert            | CTO only (do not respond directly)| Forward immediately |

---

## 📋 **Post-Incident Report Template**

After resolving critical/emergency alerts, complete this report within 24 hours:

📄 **See:** [templates/post-incident-report.md](templates/post-incident-report.md)

**Required Sections:**
1. Incident summary (what happened, when, where)
2. Timeline of events and responses
3. Alert messages sent (copies)
4. Traveler impact assessment
5. Response effectiveness evaluation
6. Lessons learned
7. Recommendations for future incidents

**Submit to:** security@letsgobelize.app

---

## 🎓 **Knowledge Check**

1. What severity level requires WhatsApp + SMS + Email + Push? **Critical**
2. How many official sources should verify a threat? **At least 2**
3. When should you send an "all clear" message? **When danger has passed**
4. Who can send safety alerts? **Admin and super_admin only**
5. What is the max WhatsApp message length? **1024 characters**

✅ **If you answered 4/5 correctly, proceed to Module 07.**

---

**Next Module:** [07: WhatsApp Operations](07-WhatsApp-Operations.md) →

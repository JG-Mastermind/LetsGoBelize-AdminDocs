# Module 04: Bookings Flow & Operations

**Module Duration:** 75 minutes | **Difficulty:** Intermediate
**Prerequisites:** Module 03 completed, admin or guide role required

---

## 🎯 **PURPOSE**

This module teaches you the complete booking lifecycle from inquiry to completion. You'll learn:
- How bookings move through statuses (pending → confirmed → completed/cancelled)
- Real-time availability checking and manual overrides
- Refund and partial refund procedures
- Edge cases and troubleshooting
- Monthly reconciliation checklist

⚠️ **Critical:** Bookings directly affect revenue and customer experience. Follow procedures exactly.

---

## ⏰ **WHEN TO USE**

Use this module when:
- Processing daily booking confirmations
- Handling customer booking modifications
- Issuing refunds or cancellations
- Investigating booking discrepancies
- Performing month-end booking reconciliation
- Training new operations staff

---

## 📊 **BOOKING LIFECYCLE DIAGRAM**

```
Customer Books Tour → PENDING (payment processing)
           ↓
    Payment Success → CONFIRMED (send WhatsApp confirmation)
           ↓
  Tour Date Arrives → IN_PROGRESS (day of tour)
           ↓
Tour Completes → COMPLETED (trigger payout to guide, request review)
           
Alternative Paths:
PENDING → Payment Failed → CANCELLED (auto, no refund)
CONFIRMED → Customer Cancels → CANCELLED (refund based on policy)
CONFIRMED → Guide Cancels → CANCELLED (full refund + credit)
```

**Status Definitions:**

| **Status**      | **Meaning**                               | **Actions Available**                |
|-----------------|-------------------------------------------|--------------------------------------|
| `pending`       | Payment processing (< 5 min usually)      | Monitor, do not modify               |
| `confirmed`     | Paid, awaiting tour date                  | Modify, cancel (refund policy)       |
| `in_progress`   | Tour happening today                      | Check-in travelers, mark complete    |
| `completed`     | Tour finished, payment settled            | Request review, handle complaints    |
| `cancelled`     | Booking voided (various reasons)          | View only (cannot resurrect)         |
| `refunded`      | Money returned to customer                | View refund details                  |

---

## 🛠️ **STEP-BY-STEP: Process Daily Bookings**

### **Morning Routine (Every Day at 8:00 AM)**

#### **Step 1: Review Pending Bookings**

1. Admin Dashboard → **"Bookings"** → Filter: **"Pending"**
2. Check for bookings older than 10 minutes:
   - Stripe payment may have failed
   - Customer abandoned checkout
   - Payment authorization issue

**Action for Stuck Pending:**
- If < 30 minutes old: Wait (payment processors can be slow)
- If > 30 minutes old: Contact customer via email (template: "Payment Incomplete")
- If > 24 hours old: Auto-cancel (system does this automatically)

---

#### **Step 2: Confirm Today's Tours**

1. Dashboard → **"Bookings"** → Filter: **"In Progress"** + **"Tour Date = Today"**
2. For each booking:
   - [ ] Verify guide has been notified (auto WhatsApp sent at 6 AM)
   - [ ] Check weather conditions (if outdoor activity)
   - [ ] Confirm meeting point logistics
   - [ ] Note any special requests (dietary, mobility)

**Red Flags:**
- No guide confirmation by 2 hours before tour → Call guide directly
- Severe weather warning → Contact guide about cancellation
- Customer no-show → Wait 30 min past meeting time, then mark as "customer_no_show"

---

#### **Step 3: Send Confirmation Reminders**

For tours happening **tomorrow**:

1. Dashboard → **"Bookings"** → Filter: **"Tour Date = Tomorrow"** + **"Confirmed"**
2. System auto-sends WhatsApp reminder at 4 PM (verify in Logs)
3. Manually check:
   - [ ] WhatsApp delivery status = "delivered" (green checkmark)
   - [ ] If failed: Retry via email (backup method)

💡 **Tip:** 80% of no-shows are prevented by 24-hour reminders.

---

## 💰 **Refund Procedures**

### **Refund Policy Matrix**

| **Cancellation Timing**    | **Refund Amount** | **Who Authorizes**       |
|----------------------------|-------------------|--------------------------|
| > 14 days before tour      | 100% refund       | Auto-approved            |
| 7-14 days before tour      | 50% refund        | Admin approval           |
| 2-6 days before tour       | 25% refund        | Admin approval           |
| < 2 days before tour       | No refund         | Super admin exception    |
| Guide cancels (any time)   | 100% + $50 credit | Auto-approved            |
| Weather cancellation       | 100% or reschedule| Auto-approved            |
| Customer no-show           | No refund         | N/A                      |

⚠️ **Caution:** Deviations from this policy require written CTO approval.

---

### **Step-by-Step: Issue Refund**

#### **Prerequisites**
- Admin or super_admin role
- Access to Stripe Dashboard (credentials from finance team)
- Booking ID and original payment amount verified

#### **Process**

1. **Verify Eligibility**
   - Check refund policy matrix above
   - Confirm no previous refund issued (prevent double refunds)
   - Screenshot booking details for audit trail

2. **Calculate Refund Amount**
   - Full refund: Original payment amount
   - Partial refund: Calculate based on policy (e.g., 50% = $250 → $125)
   - Processing fees: Stripe fees ($3 + 2.9%) are NON-REFUNDABLE (explain to customer)

3. **Process in Stripe Dashboard**
   - Log into Stripe Dashboard → **"Payments"**
   - Search by booking reference (e.g., "BOOK-2025-12345")
   - Click payment → **"Refund"** button
   - Enter refund amount (USD, no commas)
   - Reason dropdown: Select appropriate category
   - Click **"Refund $XXX.XX"**

4. **Update Booking Status**
   - Return to Admin Dashboard
   - Find booking → Click **"⋮ More"** → **"Mark as Refunded"**
   - Enter refund details:
     - Refund amount
     - Refund reason (customer dropdown)
     - Internal notes (why exception granted, if applicable)
   - Click **"Save Refund"**

5. **Notify Customer**
   - System auto-sends email: "Your refund of $XXX.XX has been processed"
   - Funds appear in customer's account within 5-10 business days
   - Add note: "If refund not received after 10 days, contact bank"

✅ **Success:** Booking status shows "refunded", audit log entry created, customer notification sent.

---

### **Partial Refund Example**

**Scenario:** Customer cancels 10 days before $300 tour.

**Calculation:**
- Original payment: $300.00
- Refund policy: 50% (7-14 days window)
- Refund amount: $150.00
- Customer keeps: $150.00 (covers guide's time, admin costs)

**Important:** Explain to customer via email:
```
Hi [Customer Name],

Your cancellation falls within our 7-14 day window, which qualifies for a 50% refund per our policy.

Refund amount: $150.00 (will appear in 5-10 business days)
Non-refundable amount: $150.00 (covers guide preparation and admin costs)

Thank you for understanding. We'd love to welcome you on a future adventure!

Best,
LetsGoBelize.app Team
```

---

## 🔄 **Manual Overrides (Use with Caution)**

### **When Manual Intervention Required**

1. **Availability Override**
   - **Scenario:** Customer wants to book tour that shows "sold out"
   - **Reason:** Guide confirmed they can take 1 more person
   - **Action:** Admin increases `max_participants` by 1 for that date
   - **Risk:** Tour quality may suffer if too crowded

2. **Price Override**
   - **Scenario:** VIP customer negotiated discounted rate
   - **Reason:** Corporate partnership, repeat customer loyalty
   - **Action:** Admin creates booking with custom price
   - **Risk:** Revenue loss, other customers may request same discount

3. **Date Change Without Penalty**
   - **Scenario:** Customer needs to reschedule due to emergency
   - **Reason:** Compassionate exception (e.g., family medical emergency)
   - **Action:** Admin transfers booking to new date, waives change fee
   - **Risk:** Sets precedent, others may request same

⚠️ **Approval Required:** All manual overrides require super admin written approval via email.

---

### **Override Procedure**

1. Customer requests exception → Document in writing (email/ticket)
2. Admin evaluates request → Check refund policy, guide availability
3. Request super admin approval → Forward customer email + recommendation
4. If approved:
   - Admin processes override in dashboard
   - Add detailed note to booking: "Exception granted by [Super Admin Name] on [Date] - Reason: [Justification]"
   - Log in monthly audit report
5. If denied:
   - Politely explain policy to customer
   - Offer alternative (e.g., credit toward future booking)

💡 **Audit Trail:** All overrides are logged and reviewed quarterly.

---

## ⚠️ **DO / DO NOT**

### **DO:**

✅ **Verify payment success before confirming tours**
- Check Stripe Dashboard for "succeeded" status
- Never manually confirm bookings with "pending" payments

✅ **Communicate proactively**
- Send 24-hour reminders
- Notify customers of weather changes
- Update guides on special requests

✅ **Document everything**
- Screenshot refund confirmations
- Save customer emails requesting changes
- Log all manual overrides

✅ **Follow refund policy strictly**
- Exceptions require super admin approval
- Explain policy clearly to customers
- Be empathetic but firm

---

### **DO NOT:**

❌ **Never issue refunds > $500 without super admin approval**
- Security policy (August 23, 2025 audit)
- High-value refunds trigger fraud alerts

❌ **Never change booking details without customer confirmation**
- Always email customer before modifying dates, times, or tours
- Get written "yes" before processing

❌ **Never delete bookings**
- Use "cancel" status instead (preserves audit trail)
- Deletions trigger security investigation

❌ **Never bypass Stripe for direct bank transfers**
- All refunds MUST go through Stripe
- Direct transfers violate payment processor terms

---

## ✅ **VERIFICATION CHECKLIST**

After processing a booking action:

- [ ] Booking status updated correctly in database
- [ ] Customer notified via email/WhatsApp
- [ ] Guide notified (if tour-related change)
- [ ] Stripe payment status matches booking status
- [ ] Audit log entry created
- [ ] Manual override (if any) documented with approval
- [ ] Refund (if any) confirmed in Stripe Dashboard
- [ ] No duplicate bookings created
- [ ] Calendar availability updated (if date changed)

---

## 🚨 **ESCALATION**

| **Issue**                              | **Contact**                      | **Response Time** |
|----------------------------------------|----------------------------------|-------------------|
| Payment stuck "pending" > 1 hour       | payments@letsgobelize.app        | 30 minutes        |
| Refund not appearing in Stripe         | payments@letsgobelize.app        | 1 hour            |
| Customer disputes refund amount        | hello@letsgobelize.app           | 4 hours           |
| Guide no-show for confirmed booking    | Security + guide manager         | Immediate (call)  |
| Double booking on same tour date       | engineering@letsgobelize.app     | 1 hour            |
| Booking data mismatch (DB vs Stripe)   | engineering@letsgobelize.app     | 2 hours           |

---

## 📋 **Monthly Reconciliation Checklist**

Perform on the 1st of each month:

- [ ] Export all bookings from previous month (CSV)
- [ ] Export all Stripe payments from previous month
- [ ] Cross-reference: Every booking has matching payment
- [ ] Identify discrepancies:
  - [ ] Bookings without payments (investigate immediately)
  - [ ] Payments without bookings (possible fraud)
  - [ ] Refunds without "refunded" status
- [ ] Calculate total revenue: Sum of all "completed" bookings
- [ ] Calculate total refunds: Sum of all "refunded" bookings
- [ ] Net revenue: Revenue - Refunds
- [ ] Compare to Stripe Dashboard balance (should match within $10)
- [ ] Document any discrepancies > $50
- [ ] Email finance team: "Monthly Booking Reconciliation - [Month]"

📄 **Template:** See [checklists/month-end-close.md](checklists/month-end-close.md)

---

## 🎓 **Knowledge Check**

1. What status indicates a tour is happening today? **in_progress**
2. How long after booking does payment usually confirm? **< 5 minutes**
3. Who can issue refunds > $500? **Super admin only**
4. What happens if guide cancels tour? **100% refund + $50 credit**
5. When should you escalate a stuck payment? **After 1 hour**

✅ **If you answered 4/5 correctly, proceed to Module 05.**

---

**Next Module:** [05: Payments & Stripe Connect](05-Payments-Stripe-Connect.md) →

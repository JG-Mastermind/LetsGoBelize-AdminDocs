# Month-End Close Checklist

**Finance & Operations Reconciliation**

Perform this checklist on the 1st business day of each month to reconcile previous month's data.

---

## 📅 **Schedule**

- **When:** 1st business day of month (by 5:00 PM)
- **Owner:** Operations Manager or designated admin
- **Duration:** 2-3 hours
- **Approval:** Finance team sign-off required

---

## 📊 **Section 1: Bookings Reconciliation**

### **Step 1: Export Booking Data**

- [ ] Log into Admin Dashboard
- [ ] Navigate to **Bookings** page
- [ ] Set date range: [First day of last month] to [Last day of last month]
- [ ] Click **"Export CSV"**
- [ ] Save as: `bookings_[YYYY-MM].csv`
- [ ] Verify row count matches dashboard summary

---

### **Step 2: Calculate Booking Metrics**

- [ ] **Total Bookings:** Count all bookings
- [ ] **Confirmed Bookings:** Filter `status = 'confirmed'`
- [ ] **Completed Bookings:** Filter `status = 'completed'`
- [ ] **Cancelled Bookings:** Filter `status = 'cancelled'`
- [ ] **Refunded Bookings:** Filter `status = 'refunded'`
- [ ] **No-Show Bookings:** Check `notes` column for "customer_no_show"

**Record in spreadsheet:**
```
Month: [Month YYYY]
Total Bookings: [X]
Confirmed: [X]
Completed: [X]
Cancelled: [X]
Refunded: [X]
No-Shows: [X]
```

---

### **Step 3: Verify Revenue**

- [ ] Sum `total_amount` for all `completed` bookings
- [ ] **Gross Revenue:** Total before platform fees
- [ ] **Platform Fees:** Multiply gross revenue by 15%
- [ ] **Net Revenue to Guides:** Gross - Platform Fees
- [ ] **Refunds Issued:** Sum `total_amount` for `refunded` bookings
- [ ] **Net Revenue (Final):** Gross Revenue - Refunds

**Expected Formula:**
```
Gross Revenue = SUM(bookings WHERE status='completed' → total_amount)
Platform Fees (15%) = Gross Revenue × 0.15
Refunds = SUM(bookings WHERE status='refunded' → total_amount)
Net Revenue = Gross Revenue - Refunds
```

---

## 💳 **Section 2: Stripe Payment Reconciliation**

### **Step 1: Export Stripe Transactions**

- [ ] Log into Stripe Dashboard
- [ ] Navigate to **Payments** → **All payments**
- [ ] Set date range: [Same as bookings]
- [ ] Click **"Export"** → **"CSV"**
- [ ] Save as: `stripe_payments_[YYYY-MM].csv`

---

### **Step 2: Cross-Reference Bookings with Payments**

- [ ] Open both CSVs side-by-side
- [ ] For each booking, verify matching Stripe payment:
  - Booking ID matches payment metadata
  - Amounts match exactly
  - Payment status = "succeeded"

**Identify Discrepancies:**
- [ ] **Bookings without payments:** Investigate (possible free tours, comped bookings)
- [ ] **Payments without bookings:** Investigate (possible fraud, duplicate payments)
- [ ] **Amount mismatches:** Investigate (pricing errors, manual adjustments)

**Document Discrepancies:**
```
Booking ID: [ID]
Issue: [Payment missing / Amount mismatch / etc.]
Explanation: [Reason]
Action Taken: [Resolved / Escalated / etc.]
```

---

### **Step 3: Verify Stripe Balance**

- [ ] Check Stripe **Balance** page
- [ ] Available balance should equal: Net Revenue - Pending Payouts
- [ ] If discrepancy > $10: Investigate immediately
- [ ] Common causes:
  - Pending refunds not yet processed
  - Failed payouts to guides
  - Stripe processing fees

---

## 🏦 **Section 3: Guide Payouts**

### **Step 1: Export Payout Data**

- [ ] Dashboard → **Payouts** page
- [ ] Filter: [Last month date range]
- [ ] Export CSV: `payouts_[YYYY-MM].csv`

---

### **Step 2: Calculate Total Payouts**

- [ ] Sum all `paid` payouts
- [ ] Sum all `pending` payouts
- [ ] Sum all `failed` payouts

**Expected:**
```
Total Payouts Due = Net Revenue to Guides (from Section 1, Step 3)
Paid Payouts = [Sum from export]
Pending Payouts = [Sum from export]
Failed Payouts = [Sum from export]

Total Paid + Pending + Failed should equal Total Payouts Due
```

---

### **Step 3: Resolve Failed Payouts**

For each failed payout:
- [ ] Identify guide (check `guide_id`)
- [ ] Contact guide: "Your payout failed. Please update bank info in Stripe."
- [ ] Retry payout after guide updates info
- [ ] Log resolution in admin notes

---

## 🔁 **Section 4: Refunds Reconciliation**

### **Step 1: Export Refund Data**

- [ ] Dashboard → **Bookings** → Filter: `status = 'refunded'`
- [ ] Date range: [Last month]
- [ ] Export CSV: `refunds_[YYYY-MM].csv`

---

### **Step 2: Verify Refund Compliance**

For each refund:
- [ ] Check refund amount matches policy (see Module 04 refund matrix)
- [ ] Verify refund processed in Stripe
- [ ] Confirm customer received refund (check Stripe refund status)
- [ ] Review notes for proper authorization:
  - Admin refunds < $500: Approved by admin
  - Super admin refunds > $500: Approved by super admin

**Red Flags:**
- Refund > $500 without super admin approval
- Refund amount doesn't match policy
- Multiple refunds to same customer (possible abuse)

---

### **Step 3: Calculate Refund Impact**

- [ ] Total refunds issued: [Amount]
- [ ] Refund rate: (Total Refunds / Gross Revenue) × 100%
- [ ] **Target:** < 5% refund rate
- [ ] **Investigate if:** > 10% refund rate

---

## 🚨 **Section 5: Safety Alerts Review**

### **Step 1: Export Safety Alerts**

- [ ] Dashboard → **Safety Alerts**
- [ ] Date range: [Last month]
- [ ] Export list of all alerts sent

---

### **Step 2: Review Alert Effectiveness**

For each alert:
- [ ] Delivery rate: > 95% target
- [ ] Average delivery time: < 2 minutes target
- [ ] Resolution time: How long until "all clear" sent?
- [ ] Customer feedback: Any complaints or thank-yous?

**Document:**
```
Month: [Month YYYY]
Total Alerts Sent: [X]
Average Delivery Rate: [X]%
Average Delivery Time: [X] minutes
Critical/Emergency Alerts: [X]
```

---

## 📈 **Section 6: Analytics Summary**

### **Key Metrics to Report:**

| **Metric**                | **Value** | **vs Last Month** | **Target** |
|---------------------------|-----------|-------------------|------------|
| Total Bookings            | [X]       | +/-[%]            | N/A        |
| Gross Revenue             | $[X]      | +/-[%]            | $[Target]  |
| Net Revenue               | $[X]      | +/-[%]            | $[Target]  |
| Average Booking Value     | $[X]      | +/-[%]            | $250       |
| Refund Rate               | [X]%      | +/-[%]            | < 5%       |
| No-Show Rate              | [X]%      | +/-[%]            | < 2%       |
| New Guides Onboarded      | [X]       | +/-[X]            | [Target]   |
| New Travelers Registered  | [X]       | +/-[X]            | [Target]   |
| Safety Alerts Sent        | [X]       | +/-[X]            | 0 (ideal)  |

---

## ✅ **Section 7: Final Approval**

### **Checklist Before Submission:**

- [ ] All exports saved in: `/finance/reports/[YYYY-MM]/`
- [ ] Discrepancies documented with explanations
- [ ] Failed payouts resolved or escalated
- [ ] Refund compliance verified
- [ ] Analytics summary completed
- [ ] Finance team notified: finance@letsgobelize.app

### **Email Template to Finance:**

```
Subject: Month-End Close - [Month YYYY]

Hi Finance Team,

Month-end reconciliation for [Month YYYY] is complete.

SUMMARY:
- Total Bookings: [X]
- Gross Revenue: $[X]
- Net Revenue: $[X]
- Refunds Issued: $[X]
- Discrepancies: [X] (see attachment)

All supporting CSVs attached. Please review and sign off by [Date].

Files:
- bookings_[YYYY-MM].csv
- stripe_payments_[YYYY-MM].csv
- payouts_[YYYY-MM].csv
- refunds_[YYYY-MM].csv
- discrepancies_log.xlsx

Thank you,
[Your Name]
[Your Role]
```

---

## 🚨 **Escalation**

If you discover:
- **Discrepancy > $500:** Escalate to finance + CTO immediately
- **Suspected fraud:** Escalate to security@letsgobelize.app immediately
- **Data export errors:** Contact engineering@letsgobelize.app

---

**Checklist Version:** 1.0
**Last Updated:** October 8, 2025
**Next Review:** January 2026

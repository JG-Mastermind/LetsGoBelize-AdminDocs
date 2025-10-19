# Operations Quick Reference Cards

**One-Page Laminated Cheat Sheets for Common Tasks**

Print these cards, laminate them, and keep at your operations desk for quick reference during live situations.

---

## 📋 **Card 1: Create Admin Invitation**

### **Prerequisites:**
- [ ] Super admin role
- [ ] Recipient's corporate email verified
- [ ] Role determined (admin, blogger, guide)

### **Steps:**
1. Dashboard → **User Management** → **Admin Invitations**
2. Click **"Create New Invitation"**
3. Fill form:
   - Email: [recipient]@letsgobelize.app
   - Role: [dropdown selection]
   - Message: Optional welcome note
4. Click **"Send Invitation"**
5. Verify status: "pending"

### **48-Hour Rule:**
- Invitation expires automatically after 48 hours
- Cannot extend—must create new invitation

### **Escalation:**
- Email not received: support@letsgobelize.app (1 hour)
- Link invalid: security@letsgobelize.app (30 min)

---

## 🎫 **Card 2: Publish a Tour**

### **Prerequisites:**
- [ ] Guide or admin role
- [ ] Hero image ready (1920x1080px, <5MB, JPG/PNG)
- [ ] Description written (300+ words)

### **Steps:**
1. Dashboard → **My Tours** (guide) or **Tours Management** (admin)
2. Click **"+ Create New Tour"**
3. Fill required fields:
   - Title (unique, 10-100 chars)
   - Description (300-2000 chars)
   - Price (USD, positive number)
   - Duration (1-24 hours)
   - Difficulty (easy/moderate/challenging/extreme)
   - Max participants (1-50)
4. Upload hero image
5. Add highlights (4-6 bullet points)
6. Set availability (days, blackout dates)
7. Click **"Preview"** → Test mobile view
8. Click **"Publish Tour"**
9. Verify appears on /adventures within 1 minute

### **French Translation (Optional):**
- Toggle **"Add French Translation"**
- Fill `title_fr`, `description_fr`, etc.
- Or click **"Auto-Translate"** (AI-assisted)

### **Escalation:**
- Tour not visible: engineering@letsgobelize.app (30 min)
- Image upload fails: support@letsgobelize.app (1 hour)

---

## ✅ **Card 3: Confirm a Booking**

### **Typical Flow (Automated):**
1. Customer completes payment via Stripe
2. System auto-sets status: `pending` → `confirmed`
3. WhatsApp confirmation sent to customer + guide
4. Admin monitors (no manual action needed)

### **Manual Confirmation (Emergency):**
Use ONLY if payment succeeded but booking stuck "pending"

1. Verify payment in Stripe Dashboard:
   - Search booking ID (e.g., BOOK-2025-12345)
   - Confirm status: "succeeded"
2. Dashboard → **Bookings** → Find booking
3. Click **"⋮ More"** → **"Mark as Confirmed"**
4. Manually trigger WhatsApp:
   - Click **"Send Confirmation"** button
5. Log incident: "Manual confirmation required due to [reason]"

### **Escalation:**
- Payment stuck > 30 min: payments@letsgobelize.app (30 min)
- WhatsApp not sending: support@letsgobelize.app (1 hour)

---

## 💰 **Card 4: Issue Refund**

### **Refund Policy (Quick Reference):**
| **Cancellation Timing** | **Refund Amount** | **Approver**    |
|-------------------------|-------------------|-----------------|
| > 14 days before tour   | 100%              | Auto-approved   |
| 7-14 days before        | 50%               | Admin           |
| 2-6 days before         | 25%               | Admin           |
| < 2 days before         | 0%                | Super admin     |
| Guide cancels           | 100% + $50 credit | Auto-approved   |

### **Steps:**
1. Calculate refund amount (use policy above)
2. Stripe Dashboard → **Payments** → Search booking ID
3. Click payment → **"Refund"** button
4. Enter refund amount (USD, no commas)
5. Select reason from dropdown
6. Click **"Refund $XXX.XX"**
7. Return to Admin Dashboard
8. Find booking → **"⋮ More"** → **"Mark as Refunded"**
9. Enter refund details + notes
10. Click **"Save Refund"**
11. Customer receives auto-email notification

### **Limits:**
- Admin: Up to $500 per refund
- Super admin: Unlimited

### **Escalation:**
- Refund > $500: Super admin approval required
- Stripe error: payments@letsgobelize.app (1 hour)

---

## 🚨 **Card 5: Send Safety Alert**

### **Severity Levels:**
| **Level**  | **Use Case**              | **Channels**              |
|------------|---------------------------|---------------------------|
| Info       | Minor disruptions         | Email only                |
| Warning    | Developing situation      | Email + SMS               |
| Critical   | Immediate danger          | WhatsApp + SMS + Email + Push |
| Emergency  | Active crisis, evacuation | All channels + Phone calls |

### **Steps:**
1. **VERIFY THREAT** (2+ official sources):
   - [ ] NEMO Belize
   - [ ] U.S. Embassy alerts
   - [ ] Belize Met Service
2. Dashboard → **Safety Alerts** → **"Create New Alert"**
3. Fill form:
   - Alert Type: Weather/Security/Health/etc.
   - Severity: [select from above]
   - Headline: 5-10 words, urgent
   - Message: Use template (see Module 06)
   - Affected Areas: Multi-select locations
   - Expiration: Date/time when danger passes
4. Click **"Preview Alert"** → Check mobile view
5. Click **"Send Alert"** → Confirm
6. Monitor delivery: Target 95% within 2 minutes

### **Message Template:**
```
🚨 [ALERT TYPE]: [HEADLINE]

SITUATION: [What's happening, 1-2 sentences]

AFFECTED AREAS: [Locations]

ACTIONS TO TAKE:
- [Action 1]
- [Action 2]

TIMELINE: [When effective, when expires]

CONTACT: [Emergency number]
```

### **Resolution:**
When danger passes:
- Alert → **"Mark as Resolved"**
- Send "All Clear" message

### **Escalation:**
- Delivery < 80%: support@letsgobelize.app (5 min)
- Uncertain severity: Super admin + CTO (10 min)
- Media inquiries: Forward to CTO immediately

---

## 📊 **Card 6: Daily Operations Checklist**

### **Morning (8:00 AM):**
- [ ] Review pending bookings (< 10 min old = wait; > 30 min = investigate)
- [ ] Check today's tours: Verify guides notified
- [ ] Send 24-hour reminders for tomorrow's tours
- [ ] Review safety alerts: Any new threats?

### **Midday (12:00 PM):**
- [ ] Monitor WhatsApp delivery rates (target: 95%+)
- [ ] Check Stripe Dashboard for payment issues
- [ ] Respond to customer inquiries (target: < 2 hours)

### **Evening (5:00 PM):**
- [ ] Mark completed tours as "completed" in dashboard
- [ ] Request reviews from today's customers
- [ ] Log any incidents in notes
- [ ] Prepare tomorrow's operations brief

### **Weekly (Fridays 3:00 PM):**
- [ ] Export bookings for week (CSV)
- [ ] Review refund requests
- [ ] Check tour availability for next 2 weeks
- [ ] Audit admin actions log

### **Monthly (1st of Month):**
- [ ] Run month-end reconciliation (see checklist)
- [ ] Review admin invitation audit
- [ ] Export financial reports for accounting
- [ ] Update contact lists (emergency, guides, admins)

---

## 🔒 **Card 7: Security Incident Response**

### **Recognize Security Incident:**
- [ ] Unauthorized login attempts
- [ ] Role changed without approval
- [ ] Data access by wrong user
- [ ] Payment discrepancy
- [ ] Customer reports fraud
- [ ] Admin invitation sent to wrong person

### **Immediate Actions (5 minutes):**
1. **DO NOT close browser or logout** (preserves audit trail)
2. Screenshot evidence (include timestamps)
3. Email security@letsgobelize.app with:
   - Subject: "SECURITY INCIDENT - [Type]"
   - Your name, role, timestamp
   - What happened (3-5 sentences)
   - Screenshots attached
4. If user account compromised:
   - Super admin → Disable account immediately
   - Notify affected users

### **DO NOT:**
- ❌ Try to fix yourself (preserve evidence)
- ❌ Discuss publicly (confidentiality)
- ❌ Delete or modify logs
- ❌ Contact user directly (security team handles)

### **Response Times:**
- **Critical:** 15 minutes (security team investigates)
- **High:** 1 hour
- **Medium:** 4 hours
- **Low:** 24 hours

### **Follow-Up:**
- Participate in incident debrief
- Complete post-incident report (see template)
- Update procedures if needed

---

## 📞 **Card 8: Emergency Contacts**

**Print this card and keep at operations desk**

| **Issue**              | **Contact**                     | **Response** |
|------------------------|---------------------------------|--------------|
| **LIFE-THREATENING**   | 911 (Belize) + security@letsgobelize.app | Immediate |
| Security incident      | security@letsgobelize.app       | 15 min       |
| Payment/Stripe         | payments@letsgobelize.app       | 1 hour       |
| Database errors        | engineering@letsgobelize.app    | 30 min       |
| WhatsApp API down      | support@letsgobelize.app        | 2 hours      |
| AI Concierge issues    | ai-support@letsgobelize.app     | 1 hour       |
| General admin help     | hello@letsgobelize.app          | 24 hours     |
| CTO (escalations only) | [provided to super admins]      | 1-2 hours    |

**After-Hours Emergency:**
- Super admin on-call rotation
- Check Slack #emergency-response channel

---

## 💡 **Card 9: Common Troubleshooting**

### **Problem: Booking stuck "pending"**
**Fix:**
1. Check Stripe payment status (succeeded/failed)
2. If succeeded > 10 min: Manually confirm (see Card 3)
3. If failed: Booking auto-cancels after 24 hours

---

### **Problem: Tour not visible on /adventures**
**Fix:**
1. Verify `is_published = true`
2. Check at least 1 future availability date exists
3. Clear browser cache (Ctrl+Shift+R)
4. Wait 2 minutes for search index rebuild

---

### **Problem: WhatsApp not sending**
**Fix:**
1. Check WhatsApp Business API status page
2. Verify message < 1024 characters
3. Retry after 5 minutes
4. If persistent: support@letsgobelize.app

---

### **Problem: Image upload timeout**
**Fix:**
1. Compress image (< 5MB using TinyPNG.com)
2. Convert to JPG (faster than PNG)
3. Try different internet connection
4. If persistent: support@letsgobelize.app

---

### **Problem: "Permission Denied" error**
**Fix:**
1. Verify your role allows this action (see RBAC matrix)
2. Log out + log back in (refresh JWT token)
3. If legitimate action blocked: hello@letsgobelize.app

---

## 🎓 **Card 10: Quick Role Reference**

| **Role**        | **Can Do**                                          |
|-----------------|-----------------------------------------------------|
| **super_admin** | Everything (user management, database, all content) |
| **admin**       | Tours, bookings, payments (< $500), safety alerts  |
| **blogger**     | Blog posts, content analytics                       |
| **guide**       | Own tours, own bookings, own calendar               |
| **traveler**    | Book tours, view own bookings                       |

**Permission Hierarchy:** super_admin > admin > blogger / guide > traveler

---

**Print Date:** October 8, 2025
**Version:** 1.0
**Next Update:** January 2026

---

**Need more help?** See full training manual: [00-Admin-ReadMe.md](../00-Admin-ReadMe.md)

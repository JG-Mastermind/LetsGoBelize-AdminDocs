# Module 03: Tours Management

**Module Duration:** 60 minutes | **Difficulty:** Intermediate
**Prerequisites:** Module 01 completed, admin or guide role required

---

## 🎯 **PURPOSE**

This module teaches you how to safely manage tours (adventures) in LetsGoBelize.app. You'll learn:
- Create and edit tours using the Dashboard UI
- Upload and manage tour images
- Set pricing, availability, and maximum participants
- Publish/unpublish tours
- Handle bilingual content (English + French-Canadian)
- Perform post-publish quality assurance

⚠️ **Critical:** Always use "tours" table (NOT "adventures"—deprecated). The UI correctly maps to tours automatically.

---

## ⏰ **WHEN TO USE**

Use this module when:
- Onboarding a new tour guide to the platform
- Creating seasonal tour offerings
- Updating pricing or availability
- Fixing tour content errors
- Translating tours to French-Canadian
- Responding to customer feedback about tour descriptions

---

## 📋 **CANONICAL TOURS TABLE**

### **Understanding the Data Model**

| **Field**              | **Type**   | **Required** | **Purpose**                                    |
|------------------------|------------|--------------|------------------------------------------------|
| `title`                | Text       | Yes          | English tour name (e.g., "Blue Hole Diving")   |
| `title_fr`             | Text       | No           | French tour name (e.g., "Plongée au Grand Trou Bleu") |
| `description`          | Text       | Yes          | Full English description (300-500 words)       |
| `description_fr`       | Text       | No           | Full French description                        |
| `price`                | Decimal    | Yes          | Price in USD (e.g., 250.00)                    |
| `duration`             | Integer    | Yes          | Duration in hours (e.g., 8)                    |
| `difficulty_level`     | Enum       | Yes          | easy, moderate, challenging, extreme           |
| `max_participants`     | Integer    | Yes          | Maximum travelers per tour (e.g., 12)          |
| `featured_image_url`   | Text       | Yes          | Hero image URL from platform storage           |
| `highlights_fr`        | JSON Array | No           | Bullet points in French                        |
| `includes_fr`          | JSON Array | No           | What's included (French)                       |
| `what_to_bring_fr`     | JSON Array | No           | Packing list (French)                          |
| `requirements_fr`      | Text       | No           | Prerequisites (French)                         |
| `not_suitable_for_fr`  | JSON Array | No           | Restrictions (French)                          |
| `meeting_point_fr`     | Text       | No           | Pickup location (French)                       |
| `itinerary_fr`         | JSON Array | No           | Step-by-step schedule (French)                 |
| `faqs_fr`              | JSON Array | No           | Common questions (French)                      |
| `slug`                 | Text       | Yes (auto)   | URL-friendly identifier (e.g., blue-hole-diving) |
| `slug_fr`              | Text       | No (auto)    | French URL slug (e.g., plongee-grand-trou-bleu) |
| `is_published`         | Boolean    | Yes          | true = visible to customers, false = draft     |
| `created_by`           | UUID       | Yes (auto)   | Guide's user ID                                |

💡 **Key Insight:** French fields (`*_fr`) are optional but strongly recommended for French-Canadian market.

---

## 🛠️ **STEP-BY-STEP: Create New Tour**

### **Method: Dashboard UI (Recommended)**

#### **Step 1: Access Tour Creation Form**

**For Guides:**
1. Log into Dashboard (`/dashboard`)
2. Click **"My Tours"** in sidebar
3. Click **"+ Create New Tour"** button

**For Admins:**
1. Log into Dashboard (`/dashboard`)
2. Click **"Tours Management"** → **"All Tours"**
3. Click **"+ Add New Tour"** button

---

#### **Step 2: Fill Basic Information**

**Required Fields (English):**

| **Field**          | **Example**                          | **Validation Rules**                     |
|--------------------|--------------------------------------|------------------------------------------|
| Title              | "Blue Hole Diving Adventure"         | 10-100 characters, unique                |
| Description        | "Experience world-class diving..."   | 300-2000 characters, detailed            |
| Price (USD)        | 250.00                               | Positive number, max 2 decimals          |
| Duration (hours)   | 8                                    | Integer, 1-24 hours                      |
| Difficulty Level   | Moderate                             | Dropdown: Easy, Moderate, Challenging, Extreme |
| Max Participants   | 12                                   | Integer, 1-50 participants               |

💡 **Best Practice:** Write descriptions in present tense, customer-focused language.

**Example Good Description:**
```
Dive into the world-famous Blue Hole, a stunning underwater sinkhole
surrounded by vibrant coral reefs. You'll descend to 130 feet, exploring
ancient stalactites and encountering nurse sharks, Caribbean reef sharks,
and colorful tropical fish. Your PADI-certified guide ensures safety while
maximizing your underwater experience.
```

**Example Poor Description:**
```
Diving. Blue hole. See fish.
```

---

#### **Step 3: Add Detailed Sections**

**Highlights (Bullet Points):**
- "PADI-certified dive master included"
- "Explore stalactites at 130 feet depth"
- "Spot nurse sharks and Caribbean reef sharks"
- "Professional underwater photography available"

💡 **Tip:** Use 4-6 highlights, each 5-10 words.

---

**What's Included:**
- "Round-trip boat transportation"
- "All diving equipment and tanks"
- "Lunch and refreshments"
- "Dive insurance"
- "Professional photos (digital download)"

---

**What to Bring:**
- "Valid PADI certification (Advanced Open Water or higher)"
- "Swimsuit and towel"
- "Sunscreen (reef-safe only)"
- "Waterproof camera (optional)"

---

**Requirements:**
```
Minimum age: 16 years
Required certification: PADI Advanced Open Water or equivalent
Minimum logged dives: 24
Medical clearance required for participants with heart conditions
```

---

**Not Suitable For:**
- "Pregnant women"
- "Non-certified divers"
- "Individuals with respiratory issues"
- "Those afraid of deep water"

---

**Meeting Point:**
```
San Pedro Water Taxi Dock
Barrier Reef Drive, San Pedro Town, Ambergris Caye
GPS: 17.9166° N, 87.9658° W

Pickup time: 6:00 AM sharp
Please arrive 15 minutes early for gear fitting.
```

---

**Itinerary (Step-by-Step Schedule):**

```json
[
  {
    "time": "6:00 AM",
    "activity": "Meet at San Pedro dock, gear check",
    "duration": "30 min"
  },
  {
    "time": "6:30 AM",
    "activity": "Boat departure to Blue Hole",
    "duration": "2.5 hours"
  },
  {
    "time": "9:00 AM",
    "activity": "Dive briefing and safety check",
    "duration": "30 min"
  },
  {
    "time": "9:30 AM",
    "activity": "First dive (Blue Hole main chamber)",
    "duration": "45 min"
  },
  {
    "time": "11:00 AM",
    "activity": "Surface interval, lunch on boat",
    "duration": "1 hour"
  },
  {
    "time": "12:00 PM",
    "activity": "Second dive (Half Moon Caye reef)",
    "duration": "45 min"
  },
  {
    "time": "2:00 PM",
    "activity": "Return to San Pedro",
    "duration": "2.5 hours"
  },
  {
    "time": "4:30 PM",
    "activity": "Arrive at dock, photo sharing",
    "duration": "30 min"
  }
]
```

---

**FAQs (Common Questions):**

```json
[
  {
    "question": "Is the Blue Hole suitable for beginner divers?",
    "answer": "No. The Blue Hole requires Advanced Open Water certification and at least 24 logged dives due to the 130-foot depth."
  },
  {
    "question": "What if weather conditions are poor?",
    "answer": "We monitor weather closely. If conditions are unsafe, we'll reschedule at no charge or offer a full refund."
  },
  {
    "question": "Can I bring my own equipment?",
    "answer": "Yes! If you have your own gear, we'll inspect it before departure. Mention this during booking."
  }
]
```

---

#### **Step 4: Upload Hero Image**

**Image Requirements:**
- **Format:** JPG or PNG
- **Size:** Max 5MB
- **Dimensions:** 1920x1080px (recommended), min 1200x675px
- **Orientation:** Landscape (horizontal)
- **Content:** High-quality photo showing tour activity
- **Restrictions:** NO stock watermarks, NO text overlays

**Upload Process:**

1. Click **"Upload Featured Image"** button
2. Select image from computer
3. System automatically:
   - Resizes to optimal dimensions
   - Compresses for fast loading
   - Uploads to platform storage (image storage)
   - Generates CDN URL
4. Preview displays immediately
5. If incorrect, click **"Replace Image"**

⚠️ **Caution:** Uploading new image replaces old one (cannot undo). Download old image first if needed.

---

#### **Step 5: Add French Translation (Optional but Recommended)**

**Why French Matters:**
- Quebec tourists = 18% of Belize tourism market
- French tours rank higher in search results
- Bilingual tours show professionalism

**Translation Fields:**

Click **"Add French Translation"** toggle to reveal:

- `title_fr`: French tour name
- `description_fr`: Full French description
- `highlights_fr`: Bullet points (French)
- `includes_fr`, `what_to_bring_fr`, `requirements_fr`, etc.

💡 **Translation Options:**

1. **Manual Translation:** Write French yourself (if fluent)
2. **AI-Assisted:** Click **"Auto-Translate"** button (GPT-4 powered)
3. **Professional Service:** Use certified translator, paste result

⚠️ **Important:** AI translations should be reviewed by native French speaker before publishing.

---

#### **Step 6: Set Pricing & Availability**

**Pricing Fields:**

| **Field**              | **Example**   | **Notes**                                |
|------------------------|---------------|------------------------------------------|
| Base Price (USD)       | $250.00       | Per person, standard booking             |
| Discount Percentage    | 15%           | Optional, for last-minute deals          |
| Seasonal Pricing       | +$50 (Dec-Mar)| Peak season upcharge                     |
| Group Discount         | 10% (8+ people)| Automatic, system calculates            |

**Availability Settings:**

| **Setting**            | **Example**   | **Notes**                                |
|------------------------|---------------|------------------------------------------|
| Available Days         | Mon, Wed, Fri | Checkboxes                               |
| Blackout Dates         | Dec 25, Jan 1 | Date picker (holidays)                   |
| Advance Booking        | 7 days        | Minimum notice required                  |
| Max Participants       | 12            | Hard limit per tour instance             |
| Min Participants       | 4             | Tour cancels if below this               |

💡 **Best Practice:** Set `min_participants` to 50% of `max_participants` for financial viability.

---

#### **Step 7: Preview & Publish**

**Before Publishing:**

- [ ] Click **"Preview"** button to see customer view
- [ ] Test tour detail page on mobile device
- [ ] Verify all images load correctly
- [ ] Check for typos in description
- [ ] Confirm pricing displays correctly
- [ ] Test "Book Now" button (leads to booking flow)
- [ ] Verify French translation (if provided)
- [ ] Check SEO slug (e.g., `/tours/blue-hole-diving`)

✅ **Success Indicators:**
- Hero image loads in < 2 seconds
- Description is well-formatted (no weird line breaks)
- Itinerary displays as timeline
- FAQs expand/collapse correctly

---

**Publishing:**

1. Click **"Publish Tour"** button
2. Confirm in modal: "This tour will be visible to all customers"
3. System automatically:
   - Sets `is_published = true`
   - Generates SEO sitemap entry
   - Adds tour to search index
   - Sends notification to admin team (if new guide)
4. Success toast: "✅ Tour published successfully!"
5. Tour appears on `/adventures` page within 1 minute

💡 **Post-Publish:** Tour is live immediately. Monitor first few bookings closely.

---

## ⚠️ **DO / DO NOT**

### **DO:**

✅ **Use high-quality, authentic photos**
- Real photos from actual tours
- Show happy customers (with permission)
- Highlight unique tour features

✅ **Write detailed, accurate descriptions**
- 300-500 words minimum
- Include safety information
- Set realistic expectations

✅ **Set appropriate max_participants**
- Consider safety ratios (e.g., 1 guide per 6 divers)
- Account for equipment availability
- Leave buffer for special needs guests

✅ **Test booking flow before going live**
- Book tour yourself (admin can cancel)
- Verify pricing calculations
- Check availability calendar

✅ **Update tours regularly**
- Seasonal pricing changes
- New itinerary stops
- Updated FAQ based on customer questions

---

### **DO NOT:**

❌ **Never use stock photos with watermarks**
- Copyright violation
- Unprofessional appearance
- Audit violation

❌ **Never promise what you cannot deliver**
- "Guaranteed whale shark sightings" ❌
- "Best tour in Belize" ❌ (subjective)
- Weather-dependent activities without disclaimers

❌ **Never edit another guide's tour without permission**
- Admins: Contact guide first
- System logs all edits (audit trail)

❌ **Never publish tours with missing required fields**
- System prevents this, but don't try to bypass

❌ **Never copy descriptions from competitors**
- Plagiarism violation
- SEO penalty
- Legal liability

---

## ✅ **VERIFICATION CHECKLIST**

After creating/editing a tour, verify:

- [ ] **Content Quality**
  - [ ] Title is descriptive and SEO-friendly
  - [ ] Description has 300+ words
  - [ ] At least 4 highlights listed
  - [ ] Itinerary has 5+ steps
  - [ ] FAQs address common concerns (3+ questions)

- [ ] **Images**
  - [ ] Featured image is high-resolution
  - [ ] Image loads in < 2 seconds
  - [ ] No watermarks or text overlays
  - [ ] Image shows actual tour activity

- [ ] **Pricing**
  - [ ] Price is competitive with similar tours
  - [ ] Discounts (if any) are configured correctly
  - [ ] Group pricing rules set (if applicable)

- [ ] **Availability**
  - [ ] Tour days selected correctly
  - [ ] Blackout dates added for holidays
  - [ ] Max participants set appropriately
  - [ ] Advance booking window reasonable

- [ ] **Translation (if French provided)**
  - [ ] `title_fr` is grammatically correct
  - [ ] `description_fr` is culturally appropriate
  - [ ] French slug is SEO-friendly
  - [ ] All French fields populated (not just title)

- [ ] **SEO**
  - [ ] Slug is unique (no duplicates)
  - [ ] Meta description is compelling
  - [ ] Keywords are relevant (e.g., "diving", "Belize", "Blue Hole")

- [ ] **Post-Publish**
  - [ ] Tour appears on `/adventures` page
  - [ ] Search function finds tour
  - [ ] Booking button works
  - [ ] Mobile view renders correctly

---

## 🚨 **ESCALATION**

| **Issue**                              | **Contact**                      | **Response Time** |
|----------------------------------------|----------------------------------|-------------------|
| Image upload fails repeatedly          | support@letsgobelize.app         | 1 hour            |
| Tour published but not visible         | engineering@letsgobelize.app     | 30 minutes        |
| Pricing calculation error              | engineering@letsgobelize.app     | 1 hour            |
| French translation concerns            | content@letsgobelize.app         | 24 hours          |
| SEO slug conflict (duplicate)          | engineering@letsgobelize.app     | 2 hours           |
| Tour deleted by mistake                | engineering@letsgobelize.app     | 1 hour (recovery) |

---

## 📚 **Common Scenarios**

### **Scenario 1: Guide's Tour Not Appearing**

**Problem:** Guide created tour, clicked "Publish," but tour not visible on `/adventures` page.

**Troubleshooting:**
1. Verify `is_published = true` in dashboard
2. Check if tour meets visibility criteria:
   - At least 1 available date in future
   - Not blacklisted by admin
   - Featured image uploaded
3. Clear browser cache (Ctrl+Shift+R)
4. Wait 2 minutes for search index rebuild

**Root Cause (90% of cases):** No future availability dates set.

---

### **Scenario 2: Image Upload Timeout**

**Problem:** Image uploads fail with "Request timeout" error.

**Causes:**
- Image file > 5MB (too large)
- Slow internet connection
- platform storage bucket misconfigured

**Solutions:**
1. Compress image using TinyPNG.com or similar
2. Switch to faster internet (mobile hotspot if needed)
3. If persistent: Contact support@letsgobelize.app

---

### **Scenario 3: Duplicate Tour Created**

**Problem:** Guide accidentally created same tour twice.

**Solution:**
1. Admin identifies duplicate (check title, description similarity)
2. Compare bookings: Keep tour with more bookings
3. Contact customers on duplicate tour: Transfer to correct tour
4. Admin unpublishes duplicate (do not delete—preserves audit trail)
5. Document incident in admin notes

---

## 🎓 **Knowledge Check**

1. What is the canonical table name for tours? **tours (NOT adventures)**
2. What is the minimum word count for descriptions? **300 words**
3. What image formats are allowed? **JPG and PNG (max 5MB)**
4. How long after publishing does a tour appear? **1 minute (search index rebuild)**
5. Who can edit any tour? **Admins and super_admins (guides edit own only)**

✅ **If you answered 4/5 correctly, proceed to Module 04.**

---

**Next Module:** [04: Bookings Flow & Operations](04-Bookings-Flow-Operations.md) →

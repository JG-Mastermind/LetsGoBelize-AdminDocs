# Appendix B: Glossary

**Non-Technical Definitions for Platform Terms**

---

## 🔤 **A-Z Platform Terminology**

### **A**

**Admin Dashboard**
The backend control panel where admins manage tours, bookings, users, and content. Accessible at `/dashboard`.

**Adventures** (deprecated)
Old name for tours. Now use "tours" table and terminology. Legacy references may still exist in code.

**AI Concierge**
GPT-4-powered chatbot helping travelers plan trips. Uses Belizean personality and cultural authenticity system.

**Anon Key**
Public API key for Supabase. Safe to use in frontend code. Does NOT grant admin access (RLS protects data).

**API (Application Programming Interface)**
How our frontend (website) talks to backend (database, payment systems). Like a waiter taking orders to the kitchen.

**Audit Log**
Automatic record of who did what, when. Cannot be edited or deleted. Used for security investigations and compliance.

---

### **B**

**Booking Flow**
The journey from customer clicking "Book Now" to payment confirmation to tour completion. See [Module 04](04-Bookings-Flow-Operations.md).

**Bucket** (Storage)
Container for files in Supabase Storage. Like folders: `tour_images`, `blog_images`, `profile_images`.

**Blogger Role**
User who can create/edit blog posts. Cannot access tours, bookings, or payments.

---

### **C**

**Canonical**
The "official" or "correct" version of something. Example: "tours" is the canonical table (not "adventures").

**CORS (Cross-Origin Resource Sharing)**
Security feature allowing browser to trust our API calls. Not something admins configure manually.

**CSV (Comma-Separated Values)**
Spreadsheet-like file format for exporting data. Opens in Excel or Google Sheets.

**CTO (Chief Technology Officer)**
Final decision-maker for technical architecture and security policies.

---

### **D**

**Dashboard**
See "Admin Dashboard"

**DDL (Data Definition Language)**
Database commands that change structure (add tables, columns). ONLY engineering can run these.

**Deployment**
Publishing new code/features to production. Requires testing and approval.

---

### **E**

**Edge Function**
Server-side code running in Supabase Cloud. Handles AI conversations, image generation, WhatsApp sending.

**Enum (Enumeration)**
Predefined list of allowed values. Example: booking status can only be `pending`, `confirmed`, `completed`, `cancelled`, `refunded`.

**Escalation**
Process of contacting higher authority when you can't solve a problem. See escalation contacts in each module.

---

### **F**

**Featured Image**
Main hero image for tours or blog posts. Shows at top of page.

**FK (Foreign Key)**
Database link between tables. Example: `booking.tour_id` links to `tours.id`.

**French-Canadian (fr-CA)**
Language variant for Quebec tourists. Uses `fr-CA` in code, `/fr-ca/` in URLs.

---

### **G**

**Guide Role**
Tour operator who can create own tours, view own bookings, manage calendar.

**GPT-4**
OpenAI's AI language model powering our AI Concierge conversations.

---

### **H**

**Hreflang**
HTML tag telling search engines about language versions. Must be lowercase: `hreflang` (not `hrefLang`).

---

### **I**

**i18n (Internationalization)**
System supporting multiple languages. LetsGoBelize supports English and French-Canadian.

**Invitation Token**
Unique link for new admins to create accounts. Valid 48 hours, single-use only.

---

### **J**

**JWT (JSON Web Token)**
Authentication token proving user's identity and role. Auto-managed by Supabase.

---

### **L**

**LetsGoBelize.app**
Platform name (rebranded from BelizeVibes in September 2025 due to trademark issues).

---

### **M**

**Max Participants**
Maximum number of travelers per tour instance. Safety-related limit set by guide.

**Migration**
Database schema change script. Creates/modifies tables, columns, policies. ONLY engineering runs these.

**Mock Data**
Fake sample data for testing. Should NOT exist in production.

---

### **N**

**NEMO (National Emergency Management Organization)**
Official Belize government emergency authority. Primary source for safety alert verification.

---

### **O**

**OAuth**
Login system using Google, Apple, or other providers. More secure than password-only.

**OpenAI**
Company providing GPT-4 AI model for our concierge system.

---

### **P**

**Payout**
Transfer of funds from platform to guide's bank account after tour completion.

**Pending**
Status meaning "waiting for something." Examples: payment processing, invitation not yet accepted.

**Platform Fee**
Percentage LetsGoBelize keeps from tour bookings (15%). Covers hosting, marketing, support costs.

**PostgreSQL (Postgres)**
Database system used by Supabase. You interact via Dashboard UI, not directly.

**Production**
Live customer-facing environment. Changes here affect real users and revenue.

**PWA (Progressive Web App)**
Web app that works like native mobile app. Can be "installed" on phone home screen.

---

### **R**

**RBAC (Role-Based Access Control)**
Permission system based on user roles. See [Module 01](01-Roles-Permissions-RLS.md).

**Refund Policy**
Rules determining refund eligibility and amount based on cancellation timing. See [Module 04](04-Bookings-Flow-Operations.md).

**RLS (Row Level Security)**
Database security automatically filtering data by user role. Prevents guides from seeing other guides' bookings.

**Role**
User's access level: super_admin, admin, blogger, guide, traveler.

---

### **S**

**Severity Level**
Safety alert priority: info, warning, critical, emergency. Determines notification channels used.

**Slug**
URL-friendly identifier. Example: "Blue Hole Diving" → `blue-hole-diving` slug.

**SMS (Short Message Service)**
Text messages sent to customer phones for urgent alerts.

**Staging**
Test environment identical to production but using fake data. Safe place to practice.

**Stripe Connect**
Payment system enabling platform payouts to guides' bank accounts.

**Super Admin**
Highest permission level. Can manage all users, change roles, access all data.

**Supabase**
Backend platform providing database, authentication, storage, and serverless functions.

---

### **T**

**Tour** (canonical)
Adventure or experience bookable on platform. Stored in `tours` table (NOT `adventures`).

**Traveler Role**
Customer who books tours. No dashboard access (customer-facing app only).

---

### **U**

**UUID (Universally Unique Identifier)**
Random 36-character ID like `a1b2c3d4-5678-90ab-cdef-1234567890ab`. Guarantees uniqueness across system.

---

### **V**

**Verification Checklist**
Step-by-step confirmation list ensuring procedure completed correctly. Found at end of each module.

---

### **W**

**WhatsApp Business API**
Official WhatsApp system for sending booking confirmations and safety alerts.

---

### **Need More Definitions?**

If you encounter an unclear term:
1. Search this glossary (Ctrl+F)
2. Check the relevant module for context
3. Email hello@letsgobelize.app with question

---

**Related Documents:**
- [Appendix A: APIs & Objects](appendix-A-APIs-and-Objects.md)
- [Module 01: Roles & Permissions](01-Roles-Permissions-RLS.md)
- [All Training Modules](00-Admin-ReadMe.md)

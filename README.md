![Crashify Key Features](cf5dbe4ccf.png)

🚗 Crashify - AI-Powered Vehicle Assessment 
Revolutionizing vehicle insurance assessments with AI automation and remote photo analysis

📊 Executive Summary
Crashify is an automated vehicle assessment that eliminates the need for costly and time-consuming onsite visits by leveraging AI-powered photo analysis and intelligent workflow automation.
## 🔄 Dual-Flow Architecture

- **Requestor-facing:** Always framed as an onsite assessment.
- **Custodian-facing:** May involve remote photo upload via secure portal.
- **Admin-facing:** Full visibility of upload status, expiry, and metadata.

## 🧠 Workflow Automation

- **Webflow Form:** Collects all assessment data.
- **n8n Automation:** Triggers webhook, calculates pricing, sends notifications.
- **Photo Upload Portal:** Mobile-first, GPS/timestamped, AI-analyzed.
- **IQ Controls API:** Final report generation and delivery.

## 📦 Key Components

- Webflow multi-step form with conditional logic
- n8n webhook and reminder flows
- AI photo analysis (Claude AI)
- IQ Controls API integration
- Professional email templates
- Invoice generation post-assessment

🎯 Understanding Our Two Client Types
Client Type 1: Assessment Requestor (Primary Client)
The entity requesting and paying for the assessment:
Insurance Companies (claims departments)
Fleet Managers (corporate fleet assessments)
Assessing Companies (independent assessment firms)
Brokers (on behalf of insurers)
Client Type 2: Vehicle Custodian (Secondary Client)
The party providing photos/access to the vehicle:
Vehicle Owner (policyholder)
Repairer/Workshop (body shop, mechanic)
Tow Yard (storage facility)
Fleet Driver (company vehicle user)

🏗️ Updated Technical Architecture
Dual-Flow System Overview
┌─────────────────────────────────────────────────────────────┐
│                    WEBFLOW BOOKING FORM                      │
│                                                              │
│  Collects:                                                   │
│  • Assessment Requestor Details (Insurance/Fleet)            │
│  • Vehicle Custodian Details (Owner/Repairer)               │
│  • Vehicle Information (Make, Model, VIN, Rego)             │
│  • Claim Details (Claim #, Excess, Quote)                   │
│  • Assessment Type (Onsite/Photo Collection)                │
│  • Documents Upload (Optional)                              │
│  • Special Notes/Instructions                               │
└────────────────────┬────────────────────────────────────────┘
                     │
                     ▼
         ┌───────────────────────┐
         │    n8n WEBHOOK        │
         │  (Trigger Automation) │
         └───────────┬───────────┘
                     │
                     ▼
┌────────────────────────────────────────────────────────────┐
│              PROCESSING PIPELINE                            │
├────────────────────────────────────────────────────────────┤
│ 1. Calculate Pricing (based on assessment type)            │
│ 2. Generate Unique Upload Token (48h expiry)              │
│ 3. Create Assessment Record                                │
│ 4. Prepare Notifications (Dual-path)                       │
└────────────┬───────────────────────────────────────────────┘
             │
             ├─────────────────┬─────────────────┐
             ▼                 ▼                 ▼
    ┌────────────────┐ ┌──────────────┐ ┌─────────────┐
    │  REQUESTOR     │ │  CUSTODIAN   │ │   ADMIN     │
    │  Notification  │ │  Notification│ │ Notification│
    └────────────────┘ └──────────────┘ └─────────────┘

📋 Webflow Form Data Collection
Required Fields
Assessment Requestor Information
• Company Name (Insurance/Fleet/Assessing Firm)
• Contact Person Name
• Email Address
• Phone Number
• Reference/Job Number (optional)
Vehicle Custodian Information
• Custodian Type: [Owner/Repairer/Tow Yard/Other]
• Business/Person Name
• Contact Person (if business)
• Email Address
• Phone Number
• Physical Address (for onsite assessments)
Vehicle Details
• Vehicle Make
• Vehicle Model
• Vehicle Year
• Registration Number (Rego)
• VIN Number
• Odometer Reading
• Colour
Claim/Assessment Details
• Claim Number
• Policy Excess Amount
• Pre-existing Quote (if available)
• Incident Date
• Incident Description
Assessment Configuration
• Assessment Type:
  - [ ] Onsite Assessment (Assessor visits location)
  - [ ] Digital Assessment (Remote photo upload)
  - [ ] Post-Repair Inspection
  
• Vehicle Category:
  - [ ] Light Vehicle ( base)
  - [ ] Heavy Vehicle ( base)
  - [ ] Machinery (base)

• Urgency:
  - [ ] Standard (48-72 hours)
  - [ ] Urgent Same-Day (+$80)

• Special Circumstances:
  - [ ] Total Loss Assessment (+$80)
  - [ ] Distance >50km (+$1.70/km)
Document Uploads (Optional)
• Supporting Documents:
  - Photos (if pre-existing)
  - Previous quotes/estimates
  - Police reports
  - Other relevant documents
Additional Information
• Special Instructions/Notes (text area)
• Preferred Assessment Date/Time (for onsite)
• Access Instructions (gates, keys, contacts)

Dual-Flow System (Unified as Onsite to Requestor)
🔁 Unified Flow: “Onsite” Assessment (with Optional Remote Photo Collection)
REQUESTOR submits → System calculates cost → Notifications sent:

├─ TO REQUESTOR (Insurance/Fleet)
✉️ Subject: "Assessment Booking Confirmed – [Claim #]"
📄 Content:
Booking confirmation
Cost breakdown (with GST)
Assessment details summary
Expected completion timeframe
"Invoice to follow with final report"
🔒 No mention of photo upload or remote assessment. Always framed as an onsite assessment.

├─ TO CUSTODIAN (Owner/Repairer)
✉️ Subject: "Vehicle Assessment Scheduled – [Vehicle Details]"
📄 Content:
Assessor will visit location
Scheduled date/time (if provided)
What to prepare
Contact details for queries
Access instructions reminder
✅ Action Required (if photo collection is enabled):
Upload photos before the visit (optional but recommended)
• Secure link: [Upload Photos Here]
• Link expires in 48 hours
• Takes 3–5 minutes
• Mobile-friendly
• Visual guide included

└─ TO ADMIN/ASSESSOR
✉️ Subject: "New Onsite Assessment – [Claim #]"
📄 Content:
All booking details
Upload link (if generated)
Expiry timestamp
Requestor & custodian info
Vehicle details
Special instructions
Documents attached

📸 Photo Upload Portal Enhancements (To Achieve 90%+ Compliance)
✅ Portal Features:
Mobile-first, no login required
9-photo checklist with visual examples
Countdown timer (e.g., “Link expires in 47h 23m”)
Progress bar and completion tracker
“Need Help?” button (chat or call)
Confirmation screen after upload

🔁 Reminder Automation (via n8n or similar)

🛠️ Next Steps for Implementation
Update Webflow Form
Keep “Assessment Type” field for internal use only (not shown to requestor)
Always show “Onsite” in requestor-facing content
Modify n8n Workflow
Trigger upload link generation only if “Photo Collection” is selected
Route all requestor notifications through the “Onsite” template
Add automated SMS/email reminders to custodian
Update Email Templates
Requestor: Onsite-only language
Custodian: Include upload link and instructions
Admin: Include upload status and expiry
Enhance Upload Portal
Add countdown timer, progress bar, and visual guide
Ensure mobile optimization and GPS/timestamp capture

📸 Photo Upload Portal Flow (For Custodians)
Step 1: Access Portal
Custodian receives email → Clicks secure link → Token validated
Step 2: Welcome Screen
┌────────────────────────────────────────┐
│  Welcome to Crashify Photo Upload      │
│  Assessment for: [Vehicle Details]     │
│  Claim #: [Claim Number]              │
│                                        │
│  ⏰ Time Remaining: 47h 23m            │
│                                        │
│  📸 Please upload photos in the        │
│     following 9 categories...          │
└────────────────────────────────────────┘
Step 3: Photo Categories
Required Photos (9 Categories):

1. 📸 Exterior Views (4 photos)
   - Front view
   - Rear view
   - Left side
   - Right side

2. 🚗 Interior (2-4 photos)
   - Dashboard/controls
   - Seats/interior condition
   - Roof/headliner (if damaged)

3. 📄 Documentation (3 photos)
   - Odometer reading
   - VIN plate
   - Number plate (registration)

4. 💥 Damage Areas (Multiple photos)
   - Each damaged area
   - Close-up of damage
   - Surrounding context

5. 🔧 Additional Areas (as needed)
   - Engine bay (if mechanical)
   - Undercarriage (if accessible)
   - Any specific areas noted

GPS & Timestamp: Automatically captured
Progress Tracker: Shows completion percentage
Step 4: Upload & Processing
Photos uploaded → Organized by category → GPS/Timestamp added
                                        ↓
                            Sent to Claude AI for analysis
                                        ↓
                            Generated organized ZIP file
                                        ↓
                            Email sent to assessor with:
                            • Organized photo folders
                            • AI damage analysis report
                            • Metadata summary
                                        ↓
                            Notification to requestor:
                            "Photos received, assessment in progress"

🤖 AI Analysis & Reporting
What Claude AI Analyzes
For each vehicle assessment:

1. Damage Identification
   • Component affected (bumper, panel, door, etc.)
   • Damage type (dent, scratch, crack, etc.)
   • Severity rating (Minor/Moderate/Severe)

2. Repair Complexity
   • Estimated labour hours
   • Parts replacement vs. repair
   • Paint/refinish requirements

3. Safety Concerns
   • Structural damage indicators
   • Safety system impacts
   • Roadworthiness assessment

4. Professional Report Generation
   • Detailed damage description
   • Component-by-component analysis
   • Recommended repair approach
   • Priority/sequence of repairs
Output Delivered to Assessor
📦 Organized ZIP File Structure:

crashify_[ClaimNumber]_[Date]/
├── 01_Exterior/
│   ├── front.jpg (GPS: -37.8136, 144.9631 | Time: 2025-10-16 14:23)
│   ├── rear.jpg
│   ├── left_side.jpg
│   └── right_side.jpg
├── 02_Interior/
│   ├── dashboard.jpg
│   └── seats.jpg
├── 03_Documentation/
│   ├── odometer.jpg
│   ├── vin_plate.jpg
│   └── number_plate.jpg
├── 04_Damage_Front_Bumper/
│   ├── bumper_overview.jpg
│   └── bumper_closeup.jpg
├── 05_Damage_Left_Door/
│   └── door_dent.jpg
└── 06_AI_Analysis/
    └── damage_report.txt (Claude AI analysis)

💰 Pricing & Cost Breakdown Notifications
To Requestor (Insurance/Fleet/Assessing Company)
✉️ Email: "Assessment Booking Confirmed"

Dear [Requestor Name],

Your vehicle assessment has been booked successfully.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ASSESSMENT DETAILS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Claim Number:        [Claim #]
Vehicle:             [Year Make Model]
Registration:        [Rego]
Assessment Type:     [Onsite/Digital]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
COST BREAKDOWN
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Base Fee:           $[Amount]
├─ [Vehicle Type]   $[Base]
├─ Urgency Fee      $[Amount] (if applicable)
├─ Distance Fee     $[Amount] (if applicable)
└─ Total Loss Fee   $[Amount] (if applicable)

Subtotal:           $[Amount]
GST (10%):          $[Amount]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TOTAL:              $[Total Amount]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📄 Invoice will be provided with the final assessment report.

Expected Completion: [Timeframe]

If you have any questions, please contact us at info@crashify.com.au

Best regards,
Crashify Team

⚙️ System Configuration Notes
Key Technical Requirements
Webflow Form Setup
Multi-step form for better UX
Conditional logic (show/hide fields based on assessment type)
File upload capability for documents
Form validation for required fields
n8n Webhook Processing
Parse Webflow submission
Distinguish between onsite vs. photo collection
Generate appropriate notifications
Store booking data
Photo Upload Portal
Token-based authentication (48hr expiry)
Mobile-responsive design
Real-time upload progress
GPS/timestamp capture
Category-based organization
Invoice System (Separate)
Generated after assessment completion
Attached to final report
Sent to requestor (not custodian)
Includes all pricing breakdown

📊 Updated Business Model
Revenue Streams
Per Assessment (Charged to Requestor) AS ONSITE:
Light Vehicle Assessment: $250 base
Heavy Vehicle Assessment: $350 base
Machinery Assessment: $450 base
Post-Repair Inspection: $250 base
Additional Fees:
Urgent Same-Day: +$80
Total Loss Assessment: +$80
Distance (>50km): +$1.70/km
GST: 10%
Invoice Delivery:
Sent with final assessment report
Includes detailed cost breakdown
Payment terms as per agreement
Digital invoice (PDF)

🎯 Key Improvements in This Model
Clear Role Separation
✅ Requestor (Insurance/Fleet) clearly identified as payer ✅ Custodian (Owner/Repairer) clearly identified as photo provider ✅ No confusion about who receives what communication
Improved Workflow Clarity
✅ Two distinct assessment paths (onsite vs. photo) ✅ Appropriate notifications to each party ✅ Clear expectations set from the start
Better Data Collection
✅ Comprehensive Webflow form captures all details ✅ Documents can be uploaded upfront ✅ Notes field for special instructions
Professional Communication
✅ Cost breakdown provided immediately to requestor ✅ "Invoice to follow with final report" sets clear expectations ✅ Custodian receives only relevant information
crashify/
├── README.md 
│
├── docs/
│   ├── technical-architecture.md
│   ├── api-documentation.md
│   ├── user-guide.md
│   ├── investor-deck.pdf (Pitch deck)
│   ├── financial-model.xlsx (3-year projections)
│   └── security-whitepaper.md
│
├── workflows/
│   ├── booking-workflow.json (n8n export)
│   ├── photo-processing.json (n8n export)
│   ├── expiry-checker.json (n8n export)
│   └── notification-system.json (n8n export)
│
├── frontend/
│   ├── photo-upload-portal/
│   │   ├── src/
│   │   ├── public/
│   │   ├── package.json
│   │   └── README.md
│   └── booking-form/
│       └── webflow-embed-code.html
│
├── templates/
│   ├── email-templates/
│   │   ├── requestor-confirmation.html
│   │   ├── custodian-upload-instructions.html
│   │   ├── admin-new-assessment.html
│   │   ├── reminder-24hr.html
│   │   └── expiry-notification.html
│   ├── sms-templates/
│   │   └── urgent-notification.txt
│   └── invoice-templates/
│       └── assessment-invoice.html
│
├── analytics/
│   ├── metrics-dashboard/ (Planned - Phase 2)
│   └── kpi-tracker.xlsx
│
├── legal/
│   ├── terms-of-service.md
│   ├── privacy-policy.md
│   └── customer-contract-template.pdf
│
└── media/
    ├── logos/
    ├── screenshots/
    └── demo-video.mp4
📞 Next Steps for Implementation
Update Webflow Form
Implement new field structure
Add conditional logic
Test form submissions
Modify n8n Workflows
Update webhook parsing
Separate notification paths
Add new data fields
Update Email Templates
Create separate templates for each recipient type
Include appropriate information for each
Professional formatting
Configure Invoice System
Set up separate invoicing workflow
Link to final report delivery
Test invoice generation
## 📎 Documentation

See [`docs/Crashify_Updated_Workflow.pdf`](docs/Crashify_Updated_Workflow.pdf) for full technical and business details.

---

Built with ❤️ in Australia | Powered by AI | Transforming Insurance Assessments


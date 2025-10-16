# 🚗 Crashify – AI-Powered Vehicle Assessment Workflow

Crashify automates vehicle damage assessments using AI and remote photo uploads, while maintaining the appearance of traditional onsite assessments to the requestor.

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

## 📈 Business Model
- Light Vehicle: $250 + GST
- Heavy Vehicle: $350 + GST
- Machinery: $450 + GST
- Add-ons: Total Loss ($80), Urgent ($80), Distance ($1.70/km)

## 📎 Documentation
See [`docs/Crashify_Updated_Workflow.pdf`](docs/Crashify_Updated_Workess details.

---

Built with ❤️ in Australia | Powered by AI | Transforming Insurance Assessments

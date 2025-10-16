# Crashify-Onsite

# 🚗 Crashify Photo Upload System

**AI-powered vehicle assessment automation** that eliminates the need for on-site visits. Crashify streamlines the booking, photo collection, damage analysis, and report generation process using Webflow, n8n, and Claude AI.

---

## 📦 What This System Does
- Sends secure upload links to clients and repairers (expires in 48 hours)
- Collects mandatory vehicle photos via mobile-friendly portal
- Organizes and GPS-stamps images
- Uses Claude AI to analyze damage photos
- Generates ZIP archive ready for IQ Controls
- Sends automated reminders and expiry notifications

---

## 🧠 Unified Workflow (n8n)
- Receives bookings via Webflow
- Calculates dynamic pricing (vehicle type, urgency, distance, total loss)
- Sends tailored emails/SMS to clients, owners, and internal staff
- Manages photo uploads and AI analysis
- Tracks upload progress and expiry
- Generates damage reports and ZIP archives

---

## 💡 Why It Matters (Investor Highlights)
- **Scalable**: Fully automated, handles 200+ bookings/month
- **Cost-effective**: ~$12–15/month operating cost
- **Time-saving**: Saves up to 5 hours/day
- **Client-friendly**: Mobile-first, guided uploads, faster turnaround
- **AI-enhanced**: Claude provides professional damage assessments

---

## 🛠 Tech Stack
- **Frontend**: Webflow + React upload portal
- **Backend**: n8n automation workflows
- **AI**: Claude Sonnet 4.5 (Anthropic API)
- **Storage**: AWS S3 or Cloudflare R2

---

## 📁 Repository Structure
```
crashify-photo-assessment/
├── README.md
├── /webflow-portal/
│   └── React upload form
├── /n8n-workflows/
│   └── crashify-booking-photos.json
├── /email-templates/
│   ├── client-confirmation.html
│   ├── reminder-email.html
│   └── expiry-notification.html
├── /ai-analysis/
│   └── claude-request-template.json
├── /docs/
│   └── Crashify Photo Upload System – Setup Guide.pdf
└── LICENSE
```

---

## 🚀 Getting Started
1. Import the n8n workflow JSON
2. Configure Webflow form to trigger booking webhook
3. Deploy upload portal (Webflow or Netlify)
4. Add Claude API key to n8n
5. Test end-to-end booking → upload → AI → ZIP → report

---

## 📈 Results
- 📸 80%+ clients upload photos within 24 hours
- ⏱️ 5+ hours saved daily
- 📊 Faster claim turnaround
- 💰 Handle 2–3× more bookings

---

## 📞 Contact
For demo access or investor inquiries:
**Crashify Team**  
📧 info@crashify.com.au  
🌐 www.crashify.com.au

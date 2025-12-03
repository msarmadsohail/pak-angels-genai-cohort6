# 🛡️ ZeroPhish Gate
### AI-Powered Phishing Detection for Supply Chain Security

[![Hugging Face](https://img.shields.io/badge/🤗-Live%20Demo-yellow?style=for-the-badge)](https://huggingface.co/spaces/28-nini/nini_)
[![Paper](https://img.shields.io/badge/📄-Presentation-blue?style=for-the-badge)](./presentation/zerophish_presentation.pdf)

**48-Hour Generative AI Hackathon Project** | Pak Angels Cohort 6 | July 2025

> **Zero trust. Zero phishing. Zero compromises.**  
> A GenAI-powered security assistant that helps non-technical supply chain employees identify phishing attacks in real-time.

---

## 🎯 Problem Statement

**68% of companies experience cyberattacks, with 29% originating from vendor-targeted phishing.**

Frontline supply chain employees (procurement officers, warehouse staff, admin) interact daily with:
- Unknown external emails
- Vendor invoices and documents  
- Chat messages from suppliers
- Attachments from unfamiliar sources

**Without formal cybersecurity training**, they are vulnerable to:
- ❌ Financial fraud and data breaches
- ❌ Loss of company reputation
- ❌ Erosion of customer trust

---

## 💡 Our Solution

**ZeroPhish Gate** is a Generative AI assistant tailored to **non-technical supply chain roles**.

Unlike traditional phishing detection tools that simply flag emails, ZeroPhish Gate:
- ✅ **Explains threats in simple, everyday language** (not technical jargon)
- ✅ **Provides role-specific advice** for Procurement, Warehouse, Admin, Finance, Logistics
- ✅ **Supports 50+ languages** with voice output for accessibility
- ✅ **Generates downloadable security reports** for record-keeping
- ✅ **Uses a hybrid 3-stage AI pipeline** combining pattern detection with semantic understanding

---

## 🔬 Technical Architecture

### **3-Stage Hybrid AI Pipeline**

```
┌─────────────────────────────────────────────────────────────┐
│  INPUT: Text message, email, or PDF document               │
└──────────────────┬──────────────────────────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────────────────────────┐
│  STAGE 1: BERT Technical Pattern Detection                 │
│  → Model: ealvaradob/bert-finetuned-phishing (Hugging Face)│
│  → Detects: Phishing patterns, suspicious URLs, keywords   │
│  → Output: Classification + confidence score                │
└──────────────────┬──────────────────────────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────────────────────────┐
│  STAGE 1.5: LLaMA RAG-Based Semantic Reranking             │
│  → Model: LLaMA 3 (8B) via Groq                            │
│  → Analyzes: Social engineering, urgency, intent, context  │
│  → Reranks: Corrects false positives/negatives from BERT   │
│  → Output: Refined classification + reasoning               │
└──────────────────┬──────────────────────────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────────────────────────┐
│  STAGE 2: Final LLaMA Interpretation                       │
│  → Generates: User-friendly explanation in selected language│
│  → Includes: Threat type, risk score, actionable advice    │
│  → Output: HTML report + voice audio (gTTS)                │
└─────────────────────────────────────────────────────────────┘
```

### **Why Hybrid Approach?**

**BERT Alone:**
- ❌ High false positives on legitimate messages
- ❌ Misses sophisticated social engineering
- ❌ No contextual understanding

**LLaMA RAG Reranking:**
- ✅ Semantic understanding of intent
- ✅ Detects psychological manipulation
- ✅ Reduces false alarms for safe messages
- ✅ Combines pattern matching with contextual analysis

---

## ✨ Key Features

### **1. Multi-Modal Input Support**
- 📝 **Text:** Paste suspicious emails or messages
- 📄 **PDF/TXT Files:** Upload vendor invoices, documents, contracts
- 🔗 **File Parsing:** Automatic text extraction with PyMuPDF

### **2. Intelligent Threat Analysis**
- 🎯 **5-Level Threat Scoring (0-100%)**
  - 0-20%: 🟢 SAFE - No threat detected
  - 21-40%: 🟡 MINIMAL SUSPICION - Minor concerns
  - 41-60%: 🟠 NEEDS ATTENTION - Requires careful review
  - 61-80%: 🔴 LIKELY THREAT - High probability of danger
  - 81-100%: ⚫ SEVERE THREAT - Immediate action required

### **3. Role-Specific Guidance**
Tailored advice for:
- **Procurement:** Validate vendor invoices, verify payment requests
- **Warehouse:** Screen documents for tampering
- **Admin:** Check chat attachments and links
- **Finance:** Prevent fraudulent payment requests
- **Logistics:** Verify shipping documents

### **4. Multi-Language Support**
- **50+ Languages:** English, Urdu, Arabic, French, German, Spanish, Portuguese, Hindi, Turkish, Bengali, Russian, Chinese, Japanese, Korean, and more
- **Voice Output:** Text-to-speech explanations using gTTS

### **5. Comprehensive Reporting**
- 📊 **Risk History Log:** Track all analyzed messages
- 📄 **Downloadable Reports:** Timestamped security reports (.txt format)
- 🔔 **IT Notification:** One-click reporting to security team

### **6. Accessibility Features**
- 🔊 Audio explanations for visually impaired users
- 🌐 Glossary tooltips for technical terms
- 📱 Responsive design for mobile/desktop

---

## 🛠️ Tech Stack

| Component | Technology | Purpose |
|-----------|-----------|---------|
| **Detection Model** | BERT (ealvaradob/bert-finetuned-phishing) | Pattern-based phishing detection |
| **Semantic Analysis** | LLaMA 3 (8B) via Groq | Intent understanding & reranking |
| **UI Framework** | Gradio | Interactive web interface |
| **Text-to-Speech** | gTTS (Google Text-to-Speech) | Voice output generation |
| **PDF Processing** | PyMuPDF (fitz) | Document text extraction |
| **Deployment** | Hugging Face Spaces | Production hosting |
| **APIs** | Groq API, Hugging Face API | Model inference |

### **Python Dependencies**
```
gradio
gtts
groq
PyMuPDF
transformers
sentence-transformers
torch
huggingface_hub
```

---

## 🚀 Live Demo

**Try it yourself:** [🔗 ZeroPhish Gate on Hugging Face](https://huggingface.co/spaces/28-nini/nini_)

**Demo Video:** [📹 Watch Presentation](https://drive.google.com/file/d/1KXUa65tDNqBkxaN1tHW-zmxl3RFsl7y2/view)

**Presentation Slides:** [📊 View Slides](https://docs.google.com/presentation/d/1T-ClP4Yf2Kl61evRVdtk1oV5Cz6EFs3B/edit?usp=sharing)

---

## 📊 Use Cases

### **Scenario 1: Procurement Officer**
**Input:** Email from "vendor" requesting urgent payment to new bank account  
**ZeroPhish Analysis:**
- 🔴 Threat Score: 78%
- ⚠️ Detected: Urgency tactics, unusual payment request, domain mismatch
- ✅ Advice: Verify with vendor via known contact before proceeding

### **Scenario 2: Warehouse Staff**
**Input:** PDF invoice with suspicious formatting  
**ZeroPhish Analysis:**
- 🟡 Threat Score: 35%
- ⚠️ Detected: Minor formatting inconsistencies
- ✅ Advice: Cross-check order numbers with internal records

### **Scenario 3: Admin Assistant**
**Input:** "Hi, please review this document"  
**ZeroPhish Analysis:**
- 🟢 Threat Score: 8%
- ✅ Detected: Normal greeting, no suspicious patterns
- ✅ Advice: Safe to proceed

---

## 🎯 Future Enhancements

- [ ] **Browser Extension:** Real-time email client integration (Gmail, Outlook)
- [ ] **Mobile App:** iOS/Android application for on-the-go scanning
- [ ] **Image Analysis:** OCR for screenshot-based phishing attempts
- [ ] **Spreadsheet Support:** Excel/CSV document analysis
- [ ] **Adaptive Learning:** Continuous model updates based on emerging threats
- [ ] **Slack/Teams Integration:** Workplace chat integration

---

## 👥 Team

**ZeroPhish Gate was developed by a team of 5 during the 48-hour hackathon:**

- **Nida Nadeem** - Group Leader
- **Iqra Fatima** - AI/ML Developer
- **Adeeba Rafi** - Data Engineer
- **Muhammad Sarmad Sohail** - AI/ML Developer
- **Yawar Munir** - Backend Developer

---

## 📄 Project Files

```
hackathon/
├── README.md (this file)
├── zerophish_gate.ipynb (main implementation)
├── presentation/
│   ├── zerophish_presentation.pdf
│   └── zerophish_slides.pptx
└── demo/
    └── README.md (links to live demo & video)
```

---

## 📚 References

- **BERT Phishing Model:** [ealvaradob/bert-finetuned-phishing](https://huggingface.co/ealvaradob/bert-finetuned-phishing)
- **LLaMA 3:** [Meta AI Research](https://ai.meta.com/llama/)
- **Groq Inference:** [Groq Cloud](https://groq.com/)
- **Industry Stats:** [Supply Chain Cybersecurity Report 2024](https://www.cybersecurityventures.com/)

---

## 🙏 Acknowledgments

- **Pak Angels** for organizing the hackathon
- **Hugging Face** for model hosting and deployment platform
- **Groq** for fast LLaMA inference API

---

**⭐ Built during Pak Angels GenAI Cohort 6 Hackathon (48 hours) - July 2025**
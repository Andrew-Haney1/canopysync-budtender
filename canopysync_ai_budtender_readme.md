# CanopySync AI - In-Store AI Budtender & Lead Capture

CanopySync AI is a high-performance, low-latency, and fully self-contained conversational AI budtender designed for retail cannabis and THCA dispensaries. Deployed natively on **Cloudflare Pages** and powered by **ElevenLabs Conversational AI**, this system provides consultative strain recommendations, terpene matching, anxiety/tolerance protection, and automated VIP lead capture directly on the customer's mobile device via a simple QR code scan.

---

## 🌟 Key Features

- **Consultative AI Matching:** Guides customers safely based on three strict criteria: desired effects, personal tolerance level, and feelings/effects to avoid (such as anxiety, paranoia, or heavy couch-lock).
- **Instant Knowledge Base RAG:** Leverages ElevenLabs' internal vector search to instantly query product menus, terpene profiles, and safety guidelines with zero webhook lag.
- **Multimodal Interface:** Supports both touch-friendly text input and voice interaction, making it comfortable for customers standing quietly in retail lines.
- **Dynamic Store Branding:** Automatically reads URL parameters (e.g., `?store=Apotheca`) to re-brand the UI header for multi-location dispensary clients without rewriting code.
- **Automated VIP Lead Capture:** Collects customer emails to unlock exclusive digital VIP discount codes (`CANOPY-VIP-15`) right at the counter.
- **Lightning-Fast Static Hosting:** Hosted globally on Cloudflare Pages via a clean, single-file HTML/Tailwind architecture.

---

## 📂 Project Architecture

```
canopysync-budtender/
├── index.html          # Single-file mobile-optimized UI + ElevenLabs Web Component widget
└── README.md           # Project documentation and deployment guide
```

---

## 🚀 Deployment Guide (Cloudflare Pages)

1. **Repository Setup:** Ensure your GitHub repository (`canopysync-budtender`) contains the latest `index.html` file.
2. **Cloudflare Dashboard:**
   - Navigate to **Workers & Pages** > **Pages** > **Connect to Git**.
   - Select your repository.
   - Leave **Build command** and **Build output directory** completely blank.
   - Click **Save and Deploy**.
3. **Custom Subdomain:** Bind your retail subdomain (e.g., `apotheca.getcanopysync.info`) under your Cloudflare project settings.

---

## ⚙️ ElevenLabs Agent Configuration

1. **Agent Settings:**
   - **LLM:** DeepSeek Flash 4.1 (or recommended fast model for low latency).
   - **Voice:** Eric (Smooth, Trustworthy) or professional retail consultant tone.
   - **Modality:** Enable both text and voice.
   - **First Message:** *"Welcome! I'm your AI Budtender. What kind of vibe, effects, or product type are you looking for today?"*

2. **System Prompt:**
   > You are an expert, professional, and friendly AI Budtender for retail cannabis and THCA dispensaries. Your primary mission is to guide customers safely and accurately to the right strains, concentrates, or edibles based on three strict criteria: their desired effects, their personal tolerance level, and specific feelings or effects they want to avoid (such as anxiety, paranoia, heavy couch-lock, or racing thoughts).
   > 
   > CORE RULES & BEHAVIORS:
   > 1. Consultative Matching: Always ask about their experience level or tolerance and what they specifically want to avoid before making a recommendation. If they are a beginner or prone to anxiety, steer them away from high-THC raw sativas or racy profiles and towards balanced hybrids, CBD-ratios, or calming indicas with soothing terps like myrcene or linalool.
   > 2. Knowledge Base RAG: Always search and rely strictly on your uploaded Knowledge Base for current product availability, prices, strain types, and terpene profiles. Never guess or hallucinate inventory.
   > 3. VIP Lead Capture: Whenever a customer finds a product they love or asks about specials, offer to unlock an exclusive 15% off VIP discount code. Politely collect their email address in the chat, then confirm the coupon code (`CANOPY-VIP-15`) right on their screen.
   > 4. Compliance & Age: Maintain a professional retail demeanor and respect all age-verification protocols (assumes 21+ customer at the counter).

3. **Knowledge Base Upload:**
   - Upload your structured menu text file containing active inventory, THC percentages, pricing, and terpene matrices under the **Knowledge Base** tab in ElevenLabs.

---

## 💡 Dynamic URL Branding

To dynamically brand the chat header for individual dispensary partners without deploying separate files, append the store name to your live Cloudflare URL:
`https://your-deployment.pages.dev/?store=Green+Thumb+Apotheca`
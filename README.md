# MediLight — Smart Pharmacy Dispensing System

**AI-powered prescription reading → medication matching → LED-guided dispensing**

Upload a prescription image → Gemini AI reads it → medications matched to inventory → LED shelf lights up → pharmacist picks the right product.

![React](https://img.shields.io/badge/React-18-61DAFB?logo=react) ![Node](https://img.shields.io/badge/Node.js-Express-339933?logo=node.js) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Neon-4169E1?logo=postgresql) ![Gemini](https://img.shields.io/badge/Gemini_AI-Vision-4285F4?logo=google) ![WebSocket](https://img.shields.io/badge/WebSocket-ESP32-010101)

---

## Try It Live

| What | Link |
|------|------|
| **Dashboard** (pharmacist interface) | [medilight-dashboard.vercel.app](https://medilight-dashboard.vercel.app) |
| **Shelf Device** (LED digital twin) | [medilight-shelf.vercel.app](https://medilight-shelf.vercel.app) |
| **API Docs** (Swagger) | [medilight-backend.onrender.com/api/docs](https://medilight-backend.onrender.com/api/docs) |
| **Test Suite** (10 automated tests) | [medilight-backend.onrender.com/api/test/run-all](https://medilight-backend.onrender.com/api/test/run-all) |

> ⏳ First load takes 30-50s — the free-tier backend sleeps after 15min of inactivity. Just wait, it'll wake up.

---

## Quick Start

1. Open the **Dashboard** link
2. Go to **Workflow** → **Upload Prescription** → **Gallery** tab
3. Download a test image from the [`prescriptions/`](./prescriptions) folder and upload it
4. Click **Analyze (PHI Protected)** — watch the AI pipeline work
5. Review matched medications → Confirm order → See LEDs activate

For the full shelf experience, open the **Shelf Device** link in a second tab first and click Connect.

---

## What's In This Repo

```
├── MediLight_Project_Guide.docx    ← Full project guide (non-technical)
├── prescriptions/                  ← 6 test prescription images
│   ├── 1_clean_typed.png           ← Clean, typed format
│   ├── 2_handwritten_messy.png     ← Handwritten doctor's note
│   ├── 3_misspelled_smudged.png    ← Typos + ink smudge
│   ├── 4_abbreviated_shorthand.png ← Medical shorthand (#30 format)
│   ├── 5_low_quality_photo.png     ← Low quality, noisy photo
│   └── 6_table_format.png          ← Structured table layout
└── README.md                       ← You're reading this
```

---

## Test Prescription Images

| # | Image | Challenge | Medications |
|---|-------|-----------|------------|
| 1 | `1_clean_typed.png` | Clean, typed | Amoxicillin, Ibuprofen, Omeprazole |
| 2 | `2_handwritten_messy.png` | Handwritten | Metformin, Lisinopril, Aspirin |
| 3 | `3_misspelled_smudged.png` | Typos + smudge | Codeine, Omeprazole, Cetirizine |
| 4 | `4_abbreviated_shorthand.png` | Shorthand, # qty | Lisinopril, Alprazolam, Cetirizine, Prednisone |
| 5 | `5_low_quality_photo.png` | Low quality photo | Amoxicillin, Lorazepam, Prednisone |
| 6 | `6_table_format.png` | Table layout | Amoxicillin, Ibuprofen, Cetirizine, Prednisone |

---

## Architecture

```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│   Dashboard  │────▶│   Backend    │────▶│  PostgreSQL   │
│   (Vercel)   │     │   (Render)   │     │   (Neon)      │
│   React+Vite │     │  Express.js  │     │  12 meds +    │
└──────────────┘     └──────┬───────┘     │  orders +     │
                            │             │  audit log    │
                    ┌───────▼───────┐     └──────────────┘
                    │  Gemini AI    │
                    │  2.5 Flash    │
                    │  (Vision+Text)│
                    └───────────────┘
                            │
                    ┌───────▼───────┐
                    │ Shelf Device  │
                    │  (WebSocket)  │
                    │  LED Digital  │
                    │    Twin       │
                    └───────────────┘
```

---

## Source Code

| Repo | What |
|------|------|
| [medilight-dashboard](https://github.com/YOUR_USERNAME/medilight-dashboard) | React frontend — 5-step workflow, inventory CRUD, order history |
| [medilight-backend](https://github.com/YOUR_USERNAME/medilight-backend) | Express API — Gemini proxy, PostgreSQL, WebSocket, Swagger |
| [medilight-shelf](https://github.com/YOUR_USERNAME/medilight-shelf) | LED digital twin — WebSocket shelf device simulation |

---

## Built With

React · Vite · Express.js · Node.js · PostgreSQL (Neon) · Google Gemini 2.5 Flash · Tesseract.js · WebSocket · ESP32 · Swagger · Vercel · Render

---

*Everything runs on free tiers. No credit card required.*

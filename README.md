# 💚 HealSense — Smart Wound Monitoring

![HealSense](https://img.shields.io/badge/HealSense-Smart%20Wound%20Monitoring-0a7ea4?style=for-the-badge&logo=heart)
![HTML](https://img.shields.io/badge/HTML5-Single%20File-orange?style=flat-square)
![CSS](https://img.shields.io/badge/CSS3-Responsive-blue?style=flat-square)
![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-yellow?style=flat-square)
![Canvas API](https://img.shields.io/badge/Canvas%20API-Wound%20Morphology-purple?style=flat-square)
![No Server](https://img.shields.io/badge/Server-None%20Required-green?style=flat-square)

### 🌐 Live Website → [https://sohamrp172-sys.github.io/HealSense-Smart-Wound-Monitoring](https://sohamrp172-sys.github.io/HealSense-Smart-Wound-Monitoring)

> **A low-cost, circuit-free smart wound patch demonstration with real wound tissue morphology analysis and smartphone-based monitoring.**

HealSense is a single-page web application that analyses **real wound photographs** using Canvas API pixel-level tissue classification. Upload a photo of the wound and the system automatically detects tissue morphology — granulation, epithelial, erythema, slough, and necrotic tissue — to produce a complete clinical-style wound assessment report, including estimated pH, exudate level, temperature, infection risk score, and tissue composition breakdown.

---

## ✨ Features

| Feature | Description |
|---|---|
| 📷 **Real Wound Photo Analysis** | Upload any wound photo — system analyses actual tissue colours and morphology |
| 🔬 **Tissue Morphology Classification** | Detects Granulation, Epithelial, Erythema, Slough, and Necrotic tissue |
| 📊 **Tissue Composition Bars** | Visual breakdown showing % of each tissue type detected |
| 🧪 **Estimated pH** | Derived from tissue alkalinity markers (erythema + necrotic tissue raise pH) |
| 💧 **Exudate Level** | Dry / Normal / Wet / Excessive — from blue channel ratio analysis |
| 🌡️ **Estimated Temperature** | 35–40°C estimate based on erythema and necrotic tissue presence |
| ⚠️ **Infection Risk Score** | 0–100% score with LOW / MEDIUM / HIGH classification |
| 🩹 **3-Level Wound Status** | HEALING · NEEDS ATTENTION · DANGER / INFECTION RISK |
| 📋 **Dataset Reference** | All 10 reference records (R001–R010) with row highlighting |
| 📲 **Built-in QR Code** | Auto-generated QR code for instant access on any device |
| 📱 **Fully Responsive** | Works on mobile (360px), tablet, and desktop (1920px) |
| 🌐 **Works Offline** | Zero dependencies — open `index.html` in any browser |

---

## 🔬 How It Works — Wound Tissue Morphology Analysis

HealSense analyses the **actual wound tissue** in the uploaded photo by sampling every pixel using the Canvas API and classifying each one by its HSL colour signature.

### Tissue Classification Table

| Tissue Type | Colour Signature | HSL Range | Clinical Meaning |
|---|---|---|---|
| � **Granulation** | Warm red-pink | H: 330–20°, S ≥ 25%, L: 28–70% | Healthy vascularised tissue — good healing |
| 🌸 **Epithelial** | Light pink | H: 330–10°, S: 10–30%, L: 60–82% | Active skin closure — near-healed |
| � **Erythema** | Bright red | H: 0–15° or 345–360°, S ≥ 50%, L: 30–55% | Inflammation / infection halo |
| 🟡 **Slough** | Yellow-cream | H: 38–72°, S: 15–60%, L: 52–88% | Devitalised fibrinous tissue |
| ⚫ **Necrotic** | Dark brown/black | H: 8–45°, S: 15–60%, L: 8–36% | Dead tissue — critical indicator |

### Analysis Pipeline

```
Upload wound photo
       ↓
Canvas API draws image at max 400×400px
       ↓
Every 3rd pixel sampled → RGB converted to HSL
       ↓
Each pixel classified into tissue type
       ↓
Tissue composition percentages calculated
       ↓
pH estimated from tissue alkalinity markers
Exudate level from blue channel ratio
Temperature estimated from erythema density
Infection risk score computed (0.0–1.0)
       ↓
Overall wound condition determined:
  ┌─ HEALING: Granulation + Epithelial ≥ 45%, danger < 20%
  ├─ NEEDS ATTENTION: Mixed tissue / elevated slough
  └─ DANGER: Necrotic ≥ 20% or infection risk ≥ 55%
       ↓
Results displayed with tissue bars, sensor readings,
wound status banner, healing progress bar
```

### Wound Status Logic

| Status | Trigger Conditions | Alert |
|---|---|---|
| ✅ **HEALING** | Granulation + Epithelial ≥ 45%, danger score < 20% | 🟢 Green |
| ⚠️ **NEEDS ATTENTION** | Mixed tissue, slough present, elevated exudate | 🟡 Amber |
| 🚨 **DANGER / INFECTION RISK** | Necrotic ≥ 20%, Erythema heavy, or infection risk ≥ 55% | 🔴 Red |

---

## 📊 Sensor Readings — What Each Metric Means

| Metric | How Calculated | Range |
|---|---|---|
| **Est. pH** | Base 6.5 + erythema contribution + necrotic contribution − granulation offset | 4.5 – 9.5 |
| **Exudate Level** | Blue channel ratio vs red channel mean | Dry / Normal / Wet / Excessive |
| **Est. Temperature** | Base 36.5°C + erythema density × 0.03 + necrotic density × 0.02 | 35.0 – 40.0°C |
| **Infection Risk** | Weighted sum: erythema% × 1.5 + necrotic% × 2 + slough% × 0.8 + exudate bonus | 0% – 100% |
| **Colour Signal** | Mean RGB values across all sampled pixels | R0–255 G0–255 B0–255 |

---

## 📋 Reference Dataset

10 reference records used to contextualise analysis results.

| Record ID | pH | pH Colour | Moisture | Wound Condition | Alert |
|---|---|---|---|---|---|
| R001 | 6.2 | Yellow | Normal | Healing | 🟢 Green |
| R002 | 6.5 | Yellow | Normal | Healing | 🟢 Green |
| R003 | 6.8 | Yellow | Normal | Healing | 🟢 Green |
| R004 | 7.0 | Yellow | Normal | Healing | 🟢 Green |
| R005 | 7.4 | Yellow | High | Healing | 🟢 Green |
| R006 | 8.0 | Purple | Normal | Abnormal | 🔴 Red |
| R007 | 8.2 | Purple | High | Abnormal | 🔴 Red |
| R008 | 8.4 | Purple | High | Abnormal | 🔴 Red |
| R009 | 8.6 | Purple | High | Abnormal | 🔴 Red |
| R010 | 8.8 | Purple | High | Abnormal | 🔴 Red |

---

## 📲 QR Code

Scan this QR code on any phone or tablet to open HealSense instantly — no typing needed.

[![HealSense QR Code](https://api.qrserver.com/v1/create-qr-code/?size=200x200&data=https://sohamrp172-sys.github.io/HealSense-Smart-Wound-Monitoring)](https://sohamrp172-sys.github.io/HealSense-Smart-Wound-Monitoring)

**🌐 Live link:** [https://sohamrp172-sys.github.io/HealSense-Smart-Wound-Monitoring](https://sohamrp172-sys.github.io/HealSense-Smart-Wound-Monitoring)

> Point your phone camera at the QR code above to open the website directly. Great for demonstrations — print it out or display it on screen next to your physical patch model.

---

## 🚀 Getting Started

No installation, no server, no build step required.

1. **Download or clone** this repository
2. **Open `index.html`** in any modern browser (Chrome, Firefox, Safari, or Edge)
3. That's it — the website runs completely offline

```bash
# Clone the repo
git clone https://github.com/sohamrp172-sys/HealSense-Smart-Wound-Monitoring.git

# Open in browser (Windows)
start index.html

# Open in browser (macOS)
open index.html
```

> **No `npm install`, no server needed.** Just open and go.

---

## 📖 Usage

### Step 1 — Open the Analyse section
Click **"Analyse a Patch Photo"** on the home screen.

### Step 2 — Upload a wound photo
- Click the upload zone or drag and drop an image
- Accepted: **JPG, PNG, WEBP** · Maximum: **10 MB**
- A preview appears immediately

### Step 3 — Run the analysis
Click **"🔬 Analyse Patch"**. The system will:
- Sample every 3rd pixel in the wound photo
- Classify tissue by HSL colour signature
- Calculate pH, exudate, temperature, and infection risk
- Determine overall wound condition

### Step 4 — Read the result

**Panel 1 — Uploaded Photo**
Your wound image displayed for reference.

**Panel 2 — Wound Assessment & Sensor Readings**
- Est. pH and classification (Normal / Alkaline)
- Exudate level (Dry / Normal / Wet / Excessive)
- Estimated skin temperature (°C)
- Detected tissue type description
- Mean RGB colour signal
- Infection risk score and label
- Tissue composition bars (% of each tissue type)

**Panel 3 — Wound Status**
- HEALING / NEEDS ATTENTION / DANGER status banner
- Animated healing progress bar
- Recommended action
- Matched dataset records (highlighted in table)

### Step 5 — Reset
Click **"↩ Upload Another Photo"** to analyse a new image.

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| **HTML5** | Single-file page structure and semantic markup |
| **CSS3** | Responsive layout, CSS variables, keyframe animations, tissue bars |
| **Vanilla JavaScript** | Five IIFE modules: NavModule, UploadModule, AnalyserModule, DatasetModule, ResultsModule |
| **Canvas API** | Pixel-level wound tissue morphology classification (HSL analysis) |
| **FileReader API** | Reading uploaded image files for preview and analysis |
| **IntersectionObserver API** | Active navigation link highlighting |
| **QR Generator** | Self-contained inline QR code algorithm (no CDN) |
| **Google Fonts (Inter)** | Typography — degrades gracefully offline |

---

## 📁 Project Structure

```
HealSense-Smart-Wound-Monitoring/
│
├── index.html      ← Complete website (HTML + CSS + JS, single file)
├── tests.html      ← Test suite (property-based + unit tests)
└── README.md       ← This file
```

**`index.html` internal structure:**

```
index.html
├── <head>
│   ├── meta (charset, viewport, title, description)
│   ├── <link> Google Fonts
│   └── <style> — all CSS
└── <body>
    ├── #global-error        — fixed error banner
    ├── <nav #navbar>        — navigation + hamburger menu
    ├── <section #home>      — hero / landing
    ├── <section #upload>    — photo upload zone
    ├── <section #results>   — 3-panel analysis result
    │   ├── Panel 1: Uploaded photo
    │   ├── Panel 2: Wound assessment (tissue bars, pH, exudate, temp, infection risk)
    │   └── Panel 3: Wound status + progress bar
    ├── <section #qr>        — auto-generated QR code + download
    ├── <section #dataset>   — reference dataset table (R001–R010)
    └── <script>
        ├── DatasetModule    — static dataset + table renderer
        ├── UploadModule     — file validation, preview, drag-and-drop
        ├── AnalyserModule   — wound tissue morphology classifier (HSL pixel analysis)
        ├── ResultsModule    — result rendering + tissue bars + dataset highlighting
        ├── NavModule        — hamburger toggle + smooth scroll + active links
        └── QR Generator    — self-contained QR code algorithm
```

---

## 🧪 Running Tests

Open `tests.html` in any modern browser — all tests run automatically.

Tests cover file validation, HSL classification, dataset record counts, and property-based correctness properties.

---

## 📱 Device Compatibility

| Device | Screen Width | Support |
|---|---|---|
| Mobile (small) | 360px+ | ✅ Full support, hamburger nav |
| Tablet | 768px+ | ✅ Full support |
| Desktop | 1024px+ | ✅ Full support |
| Large screens | up to 1920px | ✅ Full support |

**Tested browsers:** Chrome · Firefox · Safari · Edge

---

## 🏫 About This Project

HealSense is a **science exhibition / school project** demonstrating how a low-cost, circuit-free smart wound patch can be monitored using a smartphone. The physical patch uses:

- Universal pH indicator paper (changes colour based on wound fluid pH)
- Absorbent tissue paper (moisture zone — absorbs blue-tinted simulated wound fluid)
- Coloured solutions applied by syringe from the side of the patch

The digital companion app (this website) analyses real wound photos using Canvas API tissue morphology classification to produce a clinical-style assessment — no Python, no server, no AI library required.

---

## ⚠️ Disclaimer

> **This website is a demonstration prototype created for educational and exhibition purposes only.**
> It is NOT intended for clinical use, medical diagnosis, or treatment decisions.
> Do not rely on this system for actual wound care or medical advice.
> Always consult a qualified healthcare professional for any medical concerns.

---

*Built with 💚 for the Smart Wound Healing Patch project · HealSense · Detect · Monitor · Heal*

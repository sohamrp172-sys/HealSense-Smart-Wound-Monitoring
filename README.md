# 💚 HealSense — Smart Wound Monitoring

![HealSense](https://img.shields.io/badge/HealSense-Smart%20Wound%20Monitoring-0a7ea4?style=for-the-badge&logo=heart)
![HTML](https://img.shields.io/badge/HTML5-Single%20File-orange?style=flat-square)
![CSS](https://img.shields.io/badge/CSS3-Responsive-blue?style=flat-square)
![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-yellow?style=flat-square)
![No Server](https://img.shields.io/badge/Server-None%20Required-green?style=flat-square)

### 🌐 Live Website → [https://sohamrp172-sys.github.io/HealSense-Smart-Wound-Monitoring](https://sohamrp172-sys.github.io/HealSense-Smart-Wound-Monitoring)

> **A low-cost, circuit-free smart wound patch demonstration with smartphone-based monitoring.**

HealSense is a single-page web application that demonstrates how a smart wound-healing patch can be monitored using only a smartphone. Upload a photo of the physical patch and the system automatically detects the pH indicator colour — **Yellow** (Healing) or **Purple** (Abnormal) — to assess wound condition instantly, without any electronic circuit or dedicated hardware.

---

## ✨ Features

| Feature | Description |
|---|---|
| 📷 **Photo Upload** | Upload a JPG, PNG, or WEBP photo of the patch (up to 10 MB) — no camera access required |
| 🎨 **Colour Detection** | Canvas API pixel-sampling detects Yellow vs Purple pH indicator automatically |
| 📊 **Results Display** | Clear wound condition card with alert badge, pH data, moisture level, and recommended action |
| 📋 **Dataset Reference** | All 10 reference records (R001–R010) displayed in a scrollable table with row highlighting |
| 📱 **Fully Responsive** | Works on any device — mobile (360px), tablet, and desktop (1920px) |
| 🌐 **Works Offline** | Zero dependencies — runs by simply opening `index.html` in any browser |
| 🚦 **Error Handling** | Inline validation messages, graceful fallbacks, no crashes during demo |

---

## 🔬 How It Works

The physical HealSense patch uses two indicator zones:

1. **pH Indicator Zone** — Universal pH indicator paper that changes colour based on wound fluid pH
2. **Moisture Indicator Zone** — Absorbent tissue that turns blue based on moisture level

### Colour → Condition Logic

| pH Indicator Colour | pH Range | Wound Condition | Alert Level |
|---|---|---|---|
| 🟡 **Yellow** | 6.2 – 7.4 | ✅ Healing | 🟢 Green |
| 🟣 **Purple** | 8.0 – 8.8 | ⚠️ Abnormal | 🔴 Red |

### Analysis Flow

```
Upload patch photo
       ↓
Canvas API samples pixels (400×400 max, 4px grid step)
       ↓
Each pixel converted: RGB → HSL
       ↓
Classify: Yellow (hue 45–65°, sat ≥40%) or Purple (hue 270–310°, sat ≥30%)
       ↓
Dominant colour (≥20% of pixels) determines wound condition
       ↓
Results displayed with pH range, moisture level, and recommended action
       ↓
Matching dataset rows highlighted in the Reference Dataset table
```

---

## 📋 Dataset

10 reference records used to validate and contextualise the analysis results.

| Record ID | Patch ID | pH Reading | pH Colour | Moisture | Wound Condition | Alert |
|---|---|---|---|---|---|---|
| R001 | P001 | 6.2 | Yellow | Normal | Healing | 🟢 Green |
| R002 | P002 | 6.5 | Yellow | Normal | Healing | 🟢 Green |
| R003 | P003 | 6.8 | Yellow | Normal | Healing | 🟢 Green |
| R004 | P004 | 7.0 | Yellow | Normal | Healing | 🟢 Green |
| R005 | P005 | 7.4 | Yellow | High | Healing | 🟢 Green |
| R006 | P006 | 8.0 | Purple | Normal | Abnormal | 🔴 Red |
| R007 | P007 | 8.2 | Purple | High | Abnormal | 🔴 Red |
| R008 | P008 | 8.4 | Purple | High | Abnormal | 🔴 Red |
| R009 | P009 | 8.6 | Purple | High | Abnormal | 🔴 Red |
| R010 | P010 | 8.8 | Purple | High | Abnormal | 🔴 Red |

**Recommended Actions:**
- **Healing (R001–R005):** Maintain current dressing. Monitor daily.
- **Abnormal (R006–R010):** Seek medical advice promptly. Do not delay.

---

## 🚀 Getting Started

No installation, no server, no build step required.

1. **Download or clone** this repository
2. **Open `index.html`** in any modern browser (Chrome, Firefox, Safari, or Edge)
3. That's it — the website runs completely offline

```bash
# Clone the repo
git clone https://github.com/your-username/healsense-website-update.git

# Open in browser (Windows)
start index.html

# Open in browser (macOS)
open index.html

# Open in browser (Linux)
xdg-open index.html
```

> **No `npm install`, no `npm start`, no Python server needed.** Just open and go.

---

## 📖 Usage

### Step 1 — Navigate to the Analyse section
Click **"Analyse a Patch Photo"** on the home screen or use the **Analyse** link in the navigation bar.

### Step 2 — Upload a patch photo
- Click the upload zone **or** drag and drop an image file
- Accepted formats: **JPG, PNG, WEBP** · Maximum size: **10 MB**
- A preview of your uploaded image will appear immediately

### Step 3 — Run the analysis
Click **"🔬 Analyse Patch"**. The system will:
- Sample the pixel colours in your image using the Canvas API
- Classify the dominant colour as Yellow or Purple
- Determine wound condition and moisture level

### Step 4 — Read the result
The result card shows:
- ✅ **Wound Condition** — Healing or Abnormal
- 🔴/🟢 **Alert Badge** — colour-coded at a glance
- **pH Colour & Range** — detected indicator colour and associated pH
- **Moisture Level & Colour** — Normal or High
- **Status Message** — plain-language interpretation
- **Recommended Action** — what to do next
- **Matched Dataset Records** — which reference records correspond to this result

Matching rows in the **Reference Dataset** table are highlighted automatically.

### Step 5 — Reset and try again
Click **"↩ Upload Another Photo"** to clear the result and upload a new image.

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| **HTML5** | Single-file page structure and semantic markup |
| **CSS3** | Responsive layout (flexbox/grid), CSS variables, keyframe animations |
| **Vanilla JavaScript** | Five IIFE modules: NavModule, UploadModule, AnalyserModule, DatasetModule, ResultsModule |
| **Canvas API** | Offscreen image pixel sampling for colour classification |
| **FileReader API** | Reading uploaded image files for preview and analysis |
| **IntersectionObserver API** | Active navigation link highlighting as user scrolls |
| **fast-check** (CDN, tests only) | Property-based testing for pure logic functions |
| **Google Fonts (Inter)** | Typography — loads from CDN, degrades gracefully offline |

---

## 📁 Project Structure

```
healsense-website-update/
│
├── index.html      ← Complete website (HTML + CSS + JS, single file, no server)
├── tests.html      ← Test suite (property-based + unit tests, open in browser)
└── README.md       ← This file
```

**`index.html` internal structure:**

```
index.html
├── <head>
│   ├── meta (charset, viewport, title, description)
│   ├── <link> Google Fonts (Inter) — optional, degrades gracefully
│   └── <style> — all CSS (design tokens, responsive layout, animations)
└── <body>
    ├── #global-error        — fixed error banner (shown only on JS crash)
    ├── <nav #navbar>        — fixed top navigation + hamburger menu
    ├── <section #home>      — hero / landing section
    ├── <section #upload>    — photo upload zone + analyse button
    ├── <section #results>   — analysis result card + reset button
    ├── <section #dataset>   — reference dataset table (R001–R010)
    └── <script>
        ├── DatasetModule    — static dataset records + table renderer
        ├── UploadModule     — file validation, preview, drag-and-drop
        ├── AnalyserModule   — Canvas pixel sampling + HSL classification
        ├── ResultsModule    — result rendering + dataset row highlighting
        └── NavModule        — hamburger toggle + smooth scroll + active links
```

---

## 🧪 Running Tests

1. Open `tests.html` in any modern browser
2. All property-based and unit tests run automatically on load
3. A summary at the bottom shows total pass/fail count

**Tests cover:**
- Property 1: File size validation boundary (0 → 10MB accepted, >10MB rejected)
- Property 2: File type validation (all non-image MIME types rejected)
- Property 3: Colour classification correctness and totality across full HSL space
- Property 4: Analysis result field completeness and internal consistency
- Property 5: Dataset record highlighting — correct records per condition
- Unit tests: `rgbToHsl`, `classifyHsl`, boundary values, `DatasetModule` record counts

---

## 📱 Device Compatibility

| Device | Screen Width | Support |
|---|---|---|
| Mobile (small) | 360px+ | ✅ Full support, hamburger nav |
| Mobile (large) | 414px+ | ✅ Full support |
| Tablet | 768px+ | ✅ Full support, full nav bar |
| Desktop | 1024px+ | ✅ Full support |
| Large screens | up to 1920px | ✅ Full support |

**Tested browsers:** Chrome · Firefox · Safari · Edge

---

## 🏫 About This Project

HealSense is a **science exhibition / school project demonstration** created to showcase how a low-cost, circuit-free smart wound patch could be monitored using a smartphone. The physical patch model uses:

- Universal pH indicator paper (pH zone — changes colour based on wound fluid acidity/alkalinity)
- Absorbent tissue paper (moisture zone — absorbs blue-tinted simulated wound fluid)
- Coloured solutions applied by syringe from the side of the patch
- A QR code linking to this website for real-time status display

The project was originally planned with an Arduino circuit but was updated to a simpler, circuit-free design on the mentor's recommendation — making it more accessible and easier to demonstrate.

---

## 📱 QR Code

Scan this QR code on any phone or tablet to open the HealSense website instantly — no typing needed.

[![HealSense QR Code](https://api.qrserver.com/v1/create-qr-code/?size=200x200&data=https://sohamrp172-sys.github.io/HealSense-Smart-Wound-Monitoring)](https://sohamrp172-sys.github.io/HealSense-Smart-Wound-Monitoring)

**🌐 Live link:** [https://sohamrp172-sys.github.io/HealSense-Smart-Wound-Monitoring](https://sohamrp172-sys.github.io/HealSense-Smart-Wound-Monitoring)

> Point your phone camera at the QR code above to open the website directly. Great for demonstrations — print it out or display it on screen next to your physical patch model.

---

## ⚠️ Disclaimer

> **This website is a demonstration prototype created for educational and exhibition purposes only.**
> It is NOT intended for clinical use, medical diagnosis, or treatment decisions.
> Do not rely on this system for actual wound care or medical advice.
> Always consult a qualified healthcare professional for any medical concerns.

---

## 📄 Licence

This project is open source and free to use for educational purposes.

---

*Built with 💚 for the Smart Wound Healing Patch project · HealSense · Detect · Monitor · Heal*

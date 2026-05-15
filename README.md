# 🎓 Matilda's Uni App — Primary Education QTS Finder

A mobile-first, single-file web app to help Matilda find and compare UK Primary Education with QTS undergraduate courses for **September 2027 UCAS entry**.

All course data is verified directly from [ucas.com](https://www.ucas.com). No frameworks, no dependencies, no external API calls — just a single HTML file you can open in any browser.

---

## ✨ Features

### 🔍 Search & Filter
- **Live search** across university name, course title, city, region, institution code and course code
- **Region filter chips** — London, North West, North East, Yorkshire, Midlands, South East, South West
- Cards sorted best-first by the **CUG Education Subject League Table** rank

### 🎯 UCAS Points Calculator
- Enter predicted or actual **A-Level** (up to 3 grades), **BTEC Extended Diploma** or **Access to HE** grades
- Instantly calculates your estimated UCAS tariff total
- Cards **highlight green** when you meet the entry requirement, **dim** when out of reach, and show an **amber tag** when you're within 16 points
- Shows a count of courses you qualify for and how many are just within reach

### ⚖️ Compare Mode
- Tap the ⚖️ button on up to **3 courses** to add them to a comparison
- Side-by-side table showing rank, points, fee, duration, UCAS codes, Ofsted rating and more
- **Best values highlighted in green** (lowest CUG rank, lowest entry points)
- Floating compare bar shows how many courses are currently selected

### ⭐ Shortlist
- Star any course to save it to your shortlist
- Shortlist sorted by CUG rank (best first)
- **Floating shortlist bar** appears as soon as a course is saved
- **Print / PDF** button generates a clean, formatted printable summary of shortlisted courses

### 📋 Course Modals
Each course card opens a detailed modal containing:
- UCAS institution code and course code (verified from ucas.com)
- Direct link to the UCAS course listing
- Open days information
- Full entry requirements
- Annual tuition fee and **total estimated course cost** (3 or 4 years)
- Campus location with Google Maps link
- Ofsted Outstanding badge where applicable
- Accommodation details and booking link

### ✍️ Personal Statement Tips
- **4 tailored tips per course** inside each modal, specific to that university's known priorities, ethos and admissions approach
- Covers school experience expectations, course-specific themes, campus culture and professional values

### 📝 Course Notes
- Write and save your own notes inside any course modal
- Notes persist in memory during the session
- A **"Has note"** tag appears on the card so you can see at a glance which courses you have annotated

### 📅 UCAS Deadline Countdown
- Live countdown showing days remaining until the **13 January 2027** equal consideration deadline (18:00 UK time)
- Displayed prominently above the course listings

### 🌙 Dark / Light Mode
- Dark mode by default, toggle to light mode via the header button

---

## 📊 Course Data

| Detail | Info |
|---|---|
| Total courses | 24 |
| Universities | 22 |
| Data source | Verified from ucas.com |
| Entry cycle | September 2027 |
| Typical graduation | 2030 (3-year courses) |
| Ranking basis | CUG Education Subject League Table |
| UCAS equal consideration deadline | 13 January 2027, 18:00 UK time |

### Regions covered
London · North West · North East · Yorkshire · Midlands · South East · South West

### Notable flags
- **⚠️ 4-year course** — Nottingham Trent University (graduates 2031)
- **⭐ Ofsted Outstanding** — Winchester, Roehampton (×2), Edge Hill, Worcester
- **Grade-based entry** — University of Reading uses A-Level grades, not UCAS tariff points

---

## 🚀 Getting Started

No installation required. Just download the file and open it.

```bash
# Clone the repo
git clone https://github.com/YOUR-USERNAME/matildas-uni-app.git

# Open in your browser
open primary-ed-qts-finder.html
```

Or simply [download the HTML file](./primary-ed-qts-finder.html) and double-click it.

> Works in all modern browsers — Chrome, Firefox, Safari and Edge. No internet connection required once downloaded (fonts load from Google Fonts on first open if online).

---

## 🏗️ Technical Details

| Detail | Info |
|---|---|
| Stack | Vanilla HTML, CSS and JavaScript |
| Dependencies | None |
| File size | ~88 KB (single file) |
| Fonts | Syne (headings) + Plus Jakarta Sans via Google Fonts |
| Default theme | Dark mode |
| Data storage | In-memory only (no cookies, no localStorage) |
| Responsive | Mobile-first, works on all screen sizes |

All course data is embedded directly in the JavaScript array `ALL[]` inside the file. No API calls are made. The app is fully self-contained.

---

## 📁 File Structure

```
matildas-uni-app/
│
├── primary-ed-qts-finder.html    # The entire app — one file
└── README.md                     # This file
```

---

## 📋 Data Sources & Accuracy

All UCAS institution codes, course codes, entry requirements and tariff points are verified directly from individual course pages on [ucas.com](https://www.ucas.com).

- CUG rankings sourced from the **Complete University Guide Education Subject League Table**
- Ofsted ratings sourced from published Ofsted inspection reports
- Personal statement tips are editorial suggestions based on publicly available information about each institution's ethos and priorities
- Tuition fees current as of May 2025. The standard fee for 2027/28 entry is expected to be **£9,790/yr** for most providers, rising to **£10,050/yr** in subsequent years (subject to Parliamentary approval)

> ⚠️ Always confirm all details directly with the university before submitting a UCAS application. Course details, entry requirements and fees may change.

---

## 🛠️ Updating the Data

All course data lives in the `ALL` array inside the `<script>` block. Each course object follows this structure:

```javascript
{
  cugRank: 17,                          // CUG Education Subject rank
  uni: "University of Winchester",      // University name
  course: "Primary Education with QTS", // Full course title
  campus: "Main Site",                  // Campus name
  city: "Winchester",                   // City
  region: "South East",                 // Region (used by filter chips)
  instCode: "W76",                      // UCAS institution code
  courseCode: "X120",                   // UCAS course code
  points: "120",                        // Display string for entry points
  minPts: 120,                          // Numeric minimum for calculator (null = grade-based)
  duration: "3 years",                  // "3 years" or "4 years"
  fee: "£9,790/yr",                     // Annual tuition fee display string
  qual: "BA (Hons)",                    // Qualification awarded
  ofsted: true,                         // Ofsted Outstanding badge
  ucasUrl: "https://...",               // Direct link to UCAS listing
  psTips: ["Tip 1", "Tip 2", ...],      // 4 personal statement tips
  detail: {                             // Expanded modal content
    gradYear: "2030",
    duration: "3 years, graduating 2030",
    locationFull: "Winchester, Hampshire",
    mapsQ: "University of Winchester",
    entryReqs: "Full entry requirements text...",
    courseFee: "£9,790 per year",
    openDays: ["Check winchester.ac.uk for dates"],
    accommodation: "Description of halls...",
    accommodationUrl: "https://..."
  }
}
```

To add a new course, copy an existing object, update all fields, and add it to the `ALL` array. The app will automatically sort it into the correct position by `cugRank`.

---

## 📌 UCAS Key Dates (2027 Entry)

| Date | Event |
|---|---|
| 12 May 2026 | UCAS Hub opens — applications can be started |
| 1 September 2026 | Applications can be submitted to UCAS |
| 15 October 2026 | Deadline for Oxford, Cambridge, Medicine, Dentistry, Vet Science |
| **13 January 2027** | **Equal consideration deadline for all other undergraduate courses** |
| 25 February 2027 | UCAS Extra opens |
| August 2027 | A-Level results published |
| September 2027 | Course start date 🎓 |

---

## 💜 About

Built with love for Matilda, who is applying to train as a primary school teacher. The goal was to create something more useful and personal than the standard UCAS search tool — something that puts everything she actually needs in one place, in a format that works beautifully on her phone.

---

## ⚖️ Licence

This project is for personal, non-commercial use. All UCAS data remains the property of UCAS. University names and trademarks belong to their respective institutions.

---

*Last updated: May 2025 · Data verified from ucas.com*

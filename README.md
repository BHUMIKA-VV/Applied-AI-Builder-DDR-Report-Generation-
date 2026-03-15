# DDR Forge — AI Diagnostic Report Generator

> **Applied AI Builder Assignment** | Converts raw inspection + thermal data into structured, client-ready Detailed Diagnostic Reports (DDR) using Claude AI.

---

## 🎯 What This Does

Upload two source documents:
- **Inspection Report** — site observations, issue descriptions, photo references
- **Thermal Report** — temperature readings, thermal imaging findings

The AI reads both documents, intelligently merges findings, flags data conflicts, handles missing information, and generates a fully structured **Detailed Diagnostic Report (DDR)** — ready to hand to a client.

---

## 🚀 Quick Start

### Option A — Open Directly (No Setup)
1. Open `ddr_report_generator.html` in any modern browser
2. Click **"Load Sample Documents"** to try a demo instantly
3. Click **"Generate DDR Report with AI"**

### Option B — Use Your Own Documents
1. Open `ddr_report_generator.html` in any modern browser
2. Upload your **Inspection Report** (PDF, TXT, DOCX)
3. Upload your **Thermal Report** (PDF, TXT, DOCX)
4. Choose language style, severity scale, and detail level
5. Click **Generate DDR Report with AI**
6. Download the HTML report or print it

---

## 📁 Project Structure

```
ddr-system/
├── ddr_report_generator.html     ← Main application (self-contained)
├── README.md                     ← This file
├── sample-inputs/
│   ├── inspection_report_sample.txt   ← Sample inspection document
│   └── thermal_report_sample.txt      ← Sample thermal imaging document
└── sample-output/
    └── sample_ddr_output.json         ← Example AI-generated DDR JSON
```

---

## 🏗️ How It Works

```
[User uploads 2 docs]
        ↓
[Files read as base64 (PDF) or text]
        ↓
[Both docs sent to Claude API as message content]
        ↓
[AI extracts, merges, and structures data]
        ↓
[Returns structured JSON with 7 DDR sections]
        ↓
[Frontend renders interactive report]
        ↓
[User downloads HTML or prints]
```

### AI Prompt Design

The system prompt enforces strict rules:
- ❌ No invented facts — only what's in the documents
- ⚠️ Conflicts flagged explicitly (e.g., "Inspection says 600mm, Thermal says 700mm")
- 📭 Missing info written as `"Not Available"` — never omitted or guessed
- 🔗 Related findings merged — not duplicated
- 🖼️ All photo/thermal image references extracted and listed

---

## 📋 DDR Output Structure

| Section | Contents |
|---------|----------|
| 1. Property Issue Summary | Headline, severity counts (Critical/High/Medium/Low), overall condition |
| 2. Area-wise Observations | Per-area visual + thermal findings, temperature readings, image references |
| 3. Probable Root Causes | Issue → cause → supporting evidence → contributing factors |
| 4. Severity Assessment | Risk matrix table with urgency timelines and "risk if ignored" |
| 5. Recommended Actions | Priority-ordered action list with specialist requirements |
| 6. Additional Notes | Scope limitations, areas not inspected, data conflicts |
| 7. Missing / Unclear Info | All gaps marked "Not Available" or "Conflicting" |

---

## ⚙️ Configuration Options

| Option | Choices | Description |
|--------|---------|-------------|
| Language | Client-Friendly / Technical | Adjusts terminology level in the report |
| Severity Scale | 4-Level / 3-Level | Critical+High+Med+Low or High+Med+Low |
| Detail | Full Report / Summary Only | Comprehensive vs condensed output |

---

## 🛠️ Technical Details

| Item | Detail |
|------|--------|
| **Frontend** | Pure HTML/CSS/JS — zero dependencies, zero build step |
| **AI Model** | `claude-sonnet-4-20250514` via Anthropic Messages API |
| **PDF Support** | PDFs sent as base64 documents; AI reads them natively |
| **Output Format** | Structured JSON → rendered HTML |
| **Hosting** | Open locally — no server needed |
| **API** | Anthropic `/v1/messages` — API key handled by claude.ai proxy |

---

## 🔁 Generalisation

This system works on **any similar inspection reports** — not just the samples:

- Any property type (commercial, residential, industrial)
- Any inspection format (formal report, field notes, structured forms)
- Any thermal imaging report style
- Any language/format — the AI adapts to what's in the document

The AI will:
- Identify matching observations across both documents automatically
- Adjust its output based on what information is actually present
- Gracefully handle missing sections (marks as "Not Available")






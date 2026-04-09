# The Esq.

**Legal risk analysis and IP intelligence — powered by live USPTO data and AI research.**

The Esq. is a free, open-source legal analysis tool that helps product counsel, IP attorneys, and legal teams evaluate AI tools and intellectual property. It combines live USPTO data with AI-powered analysis to generate risk assessments, compliance calendars, and formal legal memos.

---

## What It Does

### ⚖️ AI Tool Risk Analysis
Enter any AI tool name and get a comprehensive legal risk assessment covering:
- **Data flow mapping** — where data goes in, how it's processed, who has access
- **Enforcement history** — real lawsuits and investigations against the specific tool
- **Liability buckets** — IP, privacy, consumer protection, employment, bias, national security, contracts
- **State & federal law analysis** — specific statutes, penalties, and compliance actions
- **International exposure** — EU AI Act, GDPR, UK, Canada, and more
- **Dollar exposure** — statutory damages, settlement ranges, insurance recommendations
- **Comparable cases** — real cases with outcomes and damage amounts
- **Compliance calendar** — deadlines with consequences if missed
- **Opposing counsel arguments** — what the other side would argue in litigation
- **Contract/ToS red flags** — output ownership, indemnification gaps, training use
- **Vendor security posture** — SOC 2, ISO 27001, breach history
- **Transparency compliance** — model card, AB 2013, EU AI Act status

### 🔍 IP Search (Trademark, Patent, Copyright)
- **Trademark** — live USPTO TSDR data, DuPont factor analysis, prosecution history, conflicting marks, clearance opinions
- **Patent** — live PatentsView data, claim charts, FTO analysis, validity risk, related patents
- **Copyright** — fair use four-factor test, DMCA exposure, AI authorship analysis, ownership chain

### 📄 Memo Generation
- Auto-generates formal legal memos in **CREAC, IRAC, Issue Memo, Client Advisory, or Due Diligence** format
- Custom letterhead (firm name, attorney, title)
- One-click **email**, **copy**, or **download**
- PDF export with branded headers, page numbers, and confidentiality footers

### 📊 Dashboard & History
- All searches saved locally (never leaves your browser)
- Risk scores tracked over time
- Full analysis recallable from history
- Executive summary toggle (CEO-friendly vs. full legal analysis)

---

## Live Data Sources

| Source | What It Provides | API Key Needed? |
|---|---|---|
| **USPTO TSDR API** | Trademark registration status, owner, dates, classes | No (free) |
| **USPTO Search API** | Trademark keyword search | No (free) |
| **USPTO Assignment API** | Ownership transfer records | No (free) |
| **PatentsView API** | Patent details, inventors, assignees, claims | No (free) |
| **Gemini 2.0 Flash** | AI analysis + Google Search grounding | Yes (free tier) |

When USPTO APIs are blocked by CORS (common on GitHub Pages), the app automatically falls back to Gemini's Google Search grounding to find the same data.

---

## Getting Started

### 1. Get a Gemini API Key (free)
Go to [aistudio.google.com/apikey](https://aistudio.google.com/apikey) and create a key. The free tier is generous enough for regular use.

### 2. Open the app
Visit the live site or open `index.html` locally in your browser.

### 3. Paste your API key
Enter it in the key field at the top. It stays in your browser — it's never sent anywhere except Google's API.

### 4. Analyze
Type an AI tool name or trademark/patent/copyright and hit Analyze or Search.

---

## Deploy Your Own

### GitHub Pages (free, 2 minutes)
```bash
git clone https://github.com/YOUR-USERNAME/the-esq.git
cd the-esq
# index.html is already here
git push origin main
# Go to Settings → Pages → Deploy from branch → main → Save
```

Your site will be live at `https://YOUR-USERNAME.github.io/the-esq/`

### Custom Domain (optional)
1. Buy a domain (e.g. `theesq.ai`)
2. Add a `CNAME` file to your repo containing just the domain name
3. In GitHub Settings → Pages → Custom domain, enter your domain
4. Configure DNS: CNAME record pointing to `YOUR-USERNAME.github.io`

---

## How It Works

1. **User enters a query** (AI tool name, trademark, patent, or copyright)
2. **Live API calls** fetch real data from USPTO/PatentsView
3. **Gemini 2.0 Flash** receives the live data as context, plus has Google Search grounding enabled to find current enforcement actions, recent cases, and regulatory guidance
4. **Structured JSON response** is parsed and rendered as an interactive risk assessment
5. **Memo generation** sends the analysis back to Gemini with a legal writing prompt
6. **Everything stays client-side** — no backend, no database, no tracking

---

## Configuration Options

| Setting | Where | Options |
|---|---|---|
| Industry | AI Tool tab | Healthcare, Finance, Education, HR, Consumer, Government, Legal |
| Jurisdictions | AI Tool tab | Any combination of 50 US states |
| International | AI Tool tab | EU, UK, Canada, Australia, Brazil, Japan, Korea |
| Memo format | Config section | CREAC, IRAC, Issue Memo, Client Advisory, Due Diligence |
| Letterhead | Config section | Firm name, attorney, title, logo URL |
| Matter # | Top bar | Free-text, appears on PDFs and in history |

---

## Tech Stack

- **Frontend:** Vanilla HTML/CSS/JS (no framework, no build step)
- **AI:** Google Gemini 2.0 Flash with Google Search grounding
- **Data:** USPTO TSDR API, USPTO Search API, PatentsView API
- **PDF:** jsPDF
- **Storage:** localStorage (browser-only, no server)
- **Hosting:** GitHub Pages (static)

---

## Privacy & Security

- Your API key is stored only in your browser's memory (not localStorage)
- Search history is stored in localStorage on your device only
- No analytics, no tracking, no cookies, no server
- All API calls go directly from your browser to Google (Gemini) and USPTO
- No data is ever sent to any third-party server

---

## Limitations

- **Not legal advice.** This tool is for informational purposes only. It does not create an attorney-client relationship. Always consult a licensed attorney.
- **AI can hallucinate.** Case names, statutes, and citations should be independently verified. The verification checklist at the bottom of each analysis is there for a reason.
- **USPTO CORS.** Some USPTO endpoints may be blocked by browser CORS policies on GitHub Pages. The app falls back to Gemini's Google Search grounding when this happens.
- **Gemini rate limits.** The free tier has usage limits. If you hit them, wait a few minutes or upgrade to a paid key.

---

## Contributing

Pull requests welcome. If you're adding a feature, please keep it in the single `index.html` file (no build step = easier for legal professionals to deploy).

Ideas for contributions:
- Cloudflare Worker for USPTO CORS proxy
- .docx export for memos
- Additional jurisdiction support
- Better mobile responsiveness
- Accessibility improvements
- Localization

---

## License

MIT — use it however you want.

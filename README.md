# PMF-MCR Questionnaire
### TTCL NICTBB Generator Maintenance Research — Data Collection Web Application

**Researcher:** Katakweba, Conrad M. | Reg. No. 240165454411 | DIT ME24MM  
**Supervisor:** Dr. Sosthenes Karugaba | Dar es Salaam Institute of Technology  
**Study:** Factors Affecting Generator Maintenance Cost at TTCL NICTBB Sites

---

## What this application does

A fully self-contained, GitHub Pages-hosted research data collection app with **no external backend, no Google Forms, no database server required**. Everything runs in the browser.

| Feature | Details |
|---|---|
| Public survey form | 5-part Likert questionnaire (25 items), accessible to anyone |
| Pre-loaded dataset | 40 seed responses (R01–R40) with timestamps May 1–Jun 10, 2026 |
| Admin dashboard | Password-protected results viewer |
| Download data | CSV and JSON export for SPSS / Excel |
| RII analysis | Auto-computed for all 21 factors |
| Add responses | Via public form OR direct quick-add panel |
| Storage | localStorage (browser) — new responses persist per device |

---

## Live URL (after deployment)

```
https://YOUR-GITHUB-USERNAME.github.io/pmf_mcr_questionnaire/
```

- **Public form link:** the URL above — share with respondents  
- **Admin / Results:** click "Admin / Results" tab → password: `PMF2025`

---

## Deploy to GitHub in 3 steps

### Step 1 — Create the repository

1. Go to [github.com](https://github.com) → click **New repository**
2. Repository name: **`pmf_mcr_questionnaire`** (exact name as shown)
3. Visibility: **Public**
4. Do NOT add README or .gitignore (you'll upload files)
5. Click **Create repository**

### Step 2 — Upload the files

**Option A — GitHub web interface (easiest):**
1. In your new repository, click **Add file → Upload files**
2. Upload `index.html` and `README.md`
3. Commit message: `Initial deployment — PMF-MCR Questionnaire n=40`
4. Click **Commit changes**

**Option B — Git command line:**
```bash
git clone https://github.com/YOUR-USERNAME/pmf_mcr_questionnaire.git
cd pmf_mcr_questionnaire
# copy index.html and README.md into this folder
git add .
git commit -m "Initial deployment — PMF-MCR Questionnaire n=40"
git push origin main
```

**Option C — Claude Code (if connected):**
Claude Code can push files directly to your repository. Ask Claude to push `index.html` and `README.md` to your `pmf_mcr_questionnaire` repository.

### Step 3 — Enable GitHub Pages

1. In your repository, go to **Settings → Pages**
2. Under **Source**, select **Deploy from a branch**
3. Branch: **main** | Folder: **/ (root)**
4. Click **Save**
5. Wait 2–3 minutes → your app is live at:
   ```
   https://YOUR-USERNAME.github.io/pmf_mcr_questionnaire/
   ```

---

## How to use

### Sharing with respondents
Send the public URL. Anyone can open it and complete the form — no login required.

### Viewing results (admin)
1. Open the app URL
2. Click **Admin / Results** in the top navigation
3. Password: `PMF2025` (change this in `index.html` — search for `ADMIN_PASSWORD`)
4. View all responses, RII table, or the Add Response panel

### Downloading data
Inside Admin → All Responses tab:
- **Download CSV** — opens in Excel / SPSS
- **Download JSON** — machine-readable format
- **Download RII CSV** — ranked factor analysis table

### Adding more responses
**Method 1 — Public form:**  
Use the public survey link yourself (or share it). Each submitted response is added to the dataset automatically.

**Method 2 — Admin quick-add:**  
Admin → Add Response tab → fill in all fields → Save Response.

---

## Admin password

Default: **`PMF2025`**

To change it, open `index.html` in a text editor, find:
```javascript
const ADMIN_PASSWORD = 'PMF2025';
```
Replace `PMF2025` with your chosen password, save, and re-upload the file to GitHub.

---

## Dataset structure

Each response contains:

| Field | Description |
|---|---|
| `id` | Respondent ID (R01–R40, then R41-NEW, etc.) |
| `timestamp` | ISO datetime of submission |
| `stratum` | Functional category |
| `exp` | Years of experience |
| `edu` | Education level |
| `pdm` | PdM familiarity |
| `TF1`–`TF6` | Technical factor scores (1–5) |
| `OF1`–`OF7` | Operational factor scores (1–5) |
| `EF1`–`EF3` | Environmental factor scores (1–5) |
| `CF1`–`CF5` | Company policy factor scores (1–5) |
| `total` | Sum of all 21 Likert items (max 105) |

**Seed data timestamps:** randomised between 01 May 2026 08:00 and 10 Jun 2026 19:00.

---

## RII Formula

> **RII = Σ(W) / (A × N)**  
> where W = individual weight (1–5), A = 5 (max scale), N = number of respondents  
> Threshold: **RII ≥ 0.70 = Significant**

---

## Data persistence

- The 40 seed responses are **always present** (embedded in `index.html`)
- New responses submitted via form or quick-add are stored in **browser localStorage**
- This means new responses appear only on the same browser/device
- For permanent multi-device storage, responses should be downloaded as CSV/JSON regularly

---

## Citation

> Katakweba, C.M. (2025). *Factors Affecting Generator Maintenance Cost at TTCL NICTBB Sites: A Predictive Maintenance Framework Study*. M.Eng (Maintenance Management) Dissertation, Dar es Salaam Institute of Technology. Supervisor: Dr. Sosthenes Karugaba.

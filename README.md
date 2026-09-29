# SWRLS Interlending Prototype

A lightweight, single-page web prototype for the **South Western Regional Library Services (SWRLS)** to coordinate and manage reciprocal inter-library lending (ILL) requests between member libraries.

See the official SWRLS interlending background: [SWRLS Inter-library Loans](https://www.swrls.org.uk/inter-library-loans).

---

## 🌟 Key Features

1. **Category-Driven Discovery**:
   - Members start by choosing a book or subject category (e.g. *Painting*, *Nursing*, *Ceramics*, *Sustainable Fashion*, *Plumbing*).
   - Includes full support for 104 specialist subject categories across public, academic, specialist, and NHS healthcare collections in the South West.
   - Includes quick search, A-Z letter filters, and a dropdown selector.

2. **Annual Quota Enforcement**:
   - Tracks each member institution's annual loaned items against their agreed quota (10 items/year).
   - **Available Institutions (< 10 loans)**: Highlighted in green with remaining quota count and an active **"Select & Request"** button.
   - **Quota Fulfilled Institutions (10/10 loans)**: Clearly identified with a distinct status badge and explanation; disabled and unavailable for selection.

3. **Pre-filled Email Request Generator**:
   - Selecting an available institution displays their direct contact details.
   - Generates a pre-filled `mailto:` link with a pre-configured subject line (`SWRLS Interlending Request [Category]`).
   - Optional interactive fields for the requesting library to include their library name and book/author/ISBN details in the pre-filled email body.
   - Quick one-click buttons to **"Copy Email"** or **"Copy Full Text"** (for webmail users).

4. **Self-Contained & GitHub Pages Ready**:
   - Single HTML file (`index.html`) using Tailwind CSS via CDN.
   - External data loaded from `institutions.csv`.
   - Includes embedded fallback dataset for opening offline or directly via `file://`.
   - Built-in "Upload CSV File" feature in the footer to test custom CSV datasets on the fly.

---

## 📁 Project Structure

```text
swrls-interlending/
├── index.html         # Main single-page web application (publishable to GitHub Pages)
├── institutions.csv   # Data file defining member libraries, subject categories, and loan counts
├── swrls_logo.jpg     # SWRLS brand logo
└── README.md          # Project documentation
```

### CSV Data Schema (`institutions.csv`)

| Column | Type | Description |
| :--- | :--- | :--- |
| `id` | String | Unique identifier (e.g., `arts-univ-plymouth`) |
| `name` | String | Institution name |
| `type` | String | Sector (`Public Library`, `Higher Education`, `Further Education`, `NHS / Health Library`) |
| `contact_name` | String | Department or person responsible for ILL |
| `contact_email` | String | Email address for loan requests |
| `catalogue_url` | String | (Optional) URL to online public library catalogue |
| `categories` | String | Semicolon-delimited list of supported subject categories |
| `loans_this_year` | Number | Number of items loaned this year (e.g., `4` or `10`) |
| `quota_limit` | Number | Annual maximum quota (default: `10`) |
| `notes` | String | Special collection strengths or status notes |

---

## 🚀 How to Run Locally

### Option 1: Direct File Open
Double-click `index.html` in your file browser to open it directly in Chrome, Edge, Safari, or Firefox. The built-in embedded dataset will automatically load.

### Option 2: Local HTTP Server (Recommended)
To load live data from `institutions.csv`:
```bash
# Using Python
python -m http.server 8000

# Using Node.js (npx)
npx serve .
```
Then visit `http://localhost:8000` in your browser.

---

## 🌐 Publishing to GitHub Pages

1. Commit and push `index.html` and `institutions.csv` to your GitHub repository:
   ```bash
   git add .
   git commit -m "Add SWRLS interlending demo prototype"
   git push origin main
   ```
2. In your repository on GitHub, navigate to **Settings** > **Pages**.
3. Under **Build and deployment** > **Source**, choose **Deploy from a branch**.
4. Set the branch to `main` and folder to `/ (root)`.
5. Click **Save**. Your site will be published at `https://<username>.github.io/swrls-interlending/`.


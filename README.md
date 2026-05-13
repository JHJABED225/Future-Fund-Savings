# Future Fund Savings — Deployment Guide

## 🚀 Deploy to GitHub + Netlify (Free)

### Step 1: GitHub Setup

1. Create a free account at [github.com](https://github.com)
2. Click **New Repository** → name it `future-fund-savings`
3. Set visibility to **Private** (recommended for financial data)
4. Upload these files to the repository:
   - `index.html` ← Main website
   - `netlify.toml` ← Netlify config
   - `README.md` ← This file

### Step 2: Netlify Deployment

1. Go to [netlify.com](https://netlify.com) → Sign up free
2. Click **Add new site** → **Import an existing project**
3. Connect to **GitHub** → Select `future-fund-savings` repo
4. Build settings:
   - **Build command:** *(leave blank)*
   - **Publish directory:** `.` *(or leave blank)*
5. Click **Deploy site**
6. Your site will be live at `https://random-name.netlify.app`
7. Optional: Set a custom domain under **Domain Settings**

---

## 🔗 Google Sheets Integration

### Step 1: Create the Google Sheet

1. Go to [sheets.google.com](https://sheets.google.com) → Create new sheet
2. Name it **"Future Fund Savings Data"**
3. Copy the Sheet ID from the URL:
   `https://docs.google.com/spreadsheets/d/`**`THIS_PART`**`/edit`

### Step 2: Deploy the Apps Script

1. Go to [script.google.com](https://script.google.com)
2. Click **New Project** → paste contents of `google-apps-script.js`
3. Replace `YOUR_GOOGLE_SHEET_ID_HERE` with your Sheet ID
4. Run `setupSpreadsheet()` once to create tabs
5. Click **Deploy** → **New Deployment**:
   - Type: **Web App**
   - Execute as: **Me**
   - Who has access: **Anyone**
6. Click **Deploy** → copy the **Web App URL**

### Step 3: Connect to Website

1. Open your deployed website
2. Click **🔑 Admin** → enter password (default: `admin123`)
3. Go to **Settings** → paste the Web App URL
4. Click **Save Settings**
5. Click **🔄 Sync Now** to push data to Sheets

---

## 🔐 Admin Password

**Default password:** `admin123`

⚠️ **Change immediately after first login:**
1. Login as Admin
2. Go to Settings → Admin Settings
3. Enter current password and set a new one

---

## 📁 File Structure

```
future-fund-savings/
├── index.html              ← Complete website (single file)
├── netlify.toml            ← Netlify routing config
├── google-apps-script.js   ← Google Sheets backend
└── README.md               ← This guide
```

---

## 💡 Features

| Feature | Details |
|---|---|
| **Home** | Logo, motto, 25 members, core committee, stats |
| **Dashboard** | Totals, yearly/monthly breakdown, personal growth |
| **Payments** | Add/edit/delete deposits and charges |
| **Expenses** | Track all fund expenditures by category |
| **Members** | 25 members, 7 core committee, full profiles |
| **Admin Auth** | Password-protected editing and management |
| **Google Sheets** | Two-way sync via Apps Script |
| **Responsive** | Mobile + desktop optimized |
| **Export** | JSON backup and restore |

---

## 🛡️ Security Notes

- The website stores data in **browser localStorage** by default
- Google Sheets sync pushes/pulls all data via your Apps Script
- Admin password is stored locally — use a strong password
- For production, consider restricting the Sheets API to specific domains
- Keep your repository **Private** if it contains real member data

---

## 🆘 Troubleshooting

**Sync not working?**
- Ensure Apps Script is deployed as "Anyone" access
- Check browser console for CORS errors
- Re-deploy the Apps Script after any code changes

**Lost admin password?**
- Open browser DevTools → Application → Local Storage
- Find `ffs_state` → edit `adminPassword` field

**Data not showing?**
- Try **Import JSON Backup** to restore a previous export
- Or clear localStorage and re-import

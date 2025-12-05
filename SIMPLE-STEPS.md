# Simple Steps to Get Google OAuth Working

## Step 1: Get Your Google OAuth Credentials (5 minutes)

1. **Open Google Cloud Console** (I already opened it in your browser)
   - If not open, go to: https://console.cloud.google.com/

2. **Create a Project** (if you don't have one)
   - Click the project dropdown at top
   - Click "New Project"
   - Name: "Portfolio Website"
   - Click "Create"

3. **Enable Google Identity API**
   - Click "APIs & Services" → "Library" (left menu)
   - Search: "Google Identity"
   - Click "Google Identity Services API"
   - Click "Enable"

4. **Set Up OAuth Consent Screen**
   - Click "APIs & Services" → "OAuth consent screen"
   - Choose "External" → Click "Create"
   - App name: "Portfolio Website"
   - User support email: (your email)
   - Developer contact: (your email)
   - Click "Save and Continue" (3 times)
   - Click "Back to Dashboard"

5. **Create OAuth Credentials**
   - Click "APIs & Services" → "Credentials"
   - Click "Create Credentials" → "OAuth client ID"
   - Application type: "Web application"
   - Name: "Portfolio Website"
   - Authorized redirect URIs: 
     - Click "Add URI"
     - Paste: `http://localhost:5000/api/auth/google/callback`
   - Click "Create"

6. **Copy Your Credentials**
   - You'll see a popup with:
     - **Client ID** (long string ending in .apps.googleusercontent.com)
     - **Client Secret** (starts with GOCSPX-)
   - **COPY BOTH** - you'll need them in Step 2!

## Step 2: Add Credentials to .env File

**Option A: Tell me your credentials**
- Just paste them here and I'll add them automatically!

**Option B: Use the script**
```powershell
cd backend
.\update-env.ps1 -ClientID "paste-your-client-id-here" -ClientSecret "paste-your-client-secret-here"
```

## Step 3: Restart Backend Server

After adding credentials:
```powershell
# Stop current server (Ctrl+C in the terminal running backend)
cd backend
npm start
```

## Step 4: Test Login

1. Go to: http://localhost:5173
2. Click "Login"
3. Sign in with Google
4. You should be redirected back and logged in!

---

## Quick Summary:
1. ✅ Get Client ID and Client Secret from Google Cloud Console
2. ✅ Tell me your credentials OR run the update script
3. ✅ Restart backend server
4. ✅ Try logging in!

**Need help?** Just paste your Client ID and Client Secret here and I'll do everything else!


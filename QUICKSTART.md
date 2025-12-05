# Quick Start Guide

Follow these steps to get your portfolio website up and running:

## Step 1: Install Dependencies

### Backend
```bash
cd backend
npm install
```

### Frontend
```bash
cd frontend
npm install
```

## Step 2: Set Up Google OAuth

1. Visit [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project (or use existing)
3. Enable **Google+ API** or **Google Identity API**
4. Go to **Credentials** → **Create Credentials** → **OAuth client ID**
5. Select **Web application**
6. Add authorized redirect URI: `http://localhost:5000/api/auth/google/callback`
7. Copy your **Client ID** and **Client Secret**

## Step 3: Configure Backend

Create `backend/.env` file:

```env
PORT=5000
SESSION_SECRET=your-random-secret-key-here-make-it-long-and-random
GOOGLE_CLIENT_ID=paste-your-google-client-id-here
GOOGLE_CLIENT_SECRET=paste-your-google-client-secret-here
FRONTEND_URL=http://localhost:5173
```

**Important:** Generate a strong random string for `SESSION_SECRET`. You can use:
- Online generator: https://randomkeygen.com/
- Or run: `node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"`

## Step 4: Start the Servers

### Terminal 1 - Backend
```bash
cd backend
npm start
```

You should see: `Server running on http://localhost:5000`

### Terminal 2 - Frontend
```bash
cd frontend
npm run dev
```

You should see: `Local: http://localhost:5173`

## Step 5: Access the Website

1. Open your browser and go to: `http://localhost:5173`
2. Click **Login** button
3. Sign in with your Google account
4. After login, click **Dashboard** to manage your portfolio
5. Edit the "About Me" section and add certificates!

## Troubleshooting

### Backend won't start
- Make sure port 5000 is not in use
- Check that `.env` file exists in `backend/` folder
- Verify all environment variables are set correctly

### Frontend won't start
- Make sure port 5173 is not in use
- Try deleting `node_modules` and running `npm install` again

### Google OAuth not working
- Verify redirect URI matches exactly: `http://localhost:5000/api/auth/google/callback`
- Check that Google Client ID and Secret are correct in `.env`
- Make sure Google+ API is enabled in Google Cloud Console

### Database errors
- The database file (`portfolio.db`) will be created automatically
- If you need to reset, delete `backend/portfolio.db` and restart the server

## Next Steps

- Customize the styling in `frontend/src/components/*.css`
- Add more features to the portfolio
- Deploy to production (see main README.md)


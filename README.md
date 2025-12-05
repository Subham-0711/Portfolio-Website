# Portfolio Website

A full-stack portfolio website with Google OAuth authentication, allowing you to manage your "About Me" section and certificates.

## Features

- 🔐 **Google OAuth Authentication** - Secure login using Google accounts only
- ✏️ **Editable About Section** - Update your "About Me" content from the dashboard
- 📜 **Certificate Management** - Add, view, and delete certificates with descriptions
- 🎨 **Modern UI** - Beautiful, responsive design with smooth animations
- 💾 **SQLite Database** - Simple, file-based database (no setup required)

## Tech Stack

### Backend
- Node.js with Express
- Passport.js for Google OAuth
- SQLite3 for database
- Express Session for authentication

### Frontend
- React with Vite
- React Router for navigation
- Axios for API calls
- Modern CSS with responsive design

## Setup Instructions

### Prerequisites
- Node.js (v16 or higher)
- npm or yarn
- Google Cloud Console account (for OAuth credentials)

### 1. Google OAuth Setup

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select an existing one
3. Enable the Google+ API
4. Go to "Credentials" → "Create Credentials" → "OAuth client ID"
5. Choose "Web application"
6. Add authorized redirect URI: `http://localhost:5000/api/auth/google/callback`
7. Copy your Client ID and Client Secret

### 2. Backend Setup

```bash
cd backend
npm install
```

Create a `.env` file in the `backend` folder:

```env
PORT=5000
SESSION_SECRET=your-random-secret-key-here
GOOGLE_CLIENT_ID=your-google-client-id
GOOGLE_CLIENT_SECRET=your-google-client-secret
FRONTEND_URL=http://localhost:5173
```

Start the backend server:

```bash
npm start
# or for development with auto-reload:
npm run dev
```

The backend will run on `http://localhost:5000`

### 3. Frontend Setup

Open a new terminal:

```bash
cd frontend
npm install
npm run dev
```

The frontend will run on `http://localhost:5173`

### 4. Access the Application

1. Open `http://localhost:5173` in your browser
2. Click "Login" to authenticate with Google
3. After login, click "Dashboard" to manage your portfolio
4. Edit the "About Me" section and add/manage certificates

## Project Structure

```
Portfolio Website/
├── backend/
│   ├── server.js          # Express server and routes
│   ├── database.js        # Database operations
│   ├── package.json
│   └── .env              # Environment variables (create this)
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Login.jsx
│   │   │   ├── Home.jsx
│   │   │   └── Dashboard.jsx
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── package.json
│   └── vite.config.js
└── README.md
```

## API Endpoints

### Authentication
- `GET /api/auth/google` - Initiate Google OAuth
- `GET /api/auth/google/callback` - OAuth callback
- `GET /api/auth/logout` - Logout user
- `GET /api/auth/me` - Get current user info

### About Section
- `GET /api/about` - Get about content
- `PUT /api/about` - Update about content (authenticated)

### Certificates
- `GET /api/certificates` - Get all certificates
- `POST /api/certificates` - Add certificate (authenticated)
- `DELETE /api/certificates/:id` - Delete certificate (authenticated)

## Production Deployment

For production deployment:

1. Update `FRONTEND_URL` in backend `.env` to your production frontend URL
2. Update Google OAuth redirect URI in Google Cloud Console
3. Set `NODE_ENV=production` in backend `.env`
4. Use a secure `SESSION_SECRET`
5. Build the frontend: `cd frontend && npm run build`
6. Serve the frontend build folder using a web server or hosting service

## Security Notes

- Never commit `.env` files to version control
- Use strong, random `SESSION_SECRET` in production
- Enable HTTPS in production
- Keep your Google OAuth credentials secure

## License

MIT License - feel free to use this project for your portfolio!


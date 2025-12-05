# How to Fix npm start Errors

## Common Error: Port Already in Use

If you see: `Error: listen EADDRINUSE: address already in use :::5000`

### Quick Fix (PowerShell):

```powershell
# Kill process on port 5000
Get-Process -Id (Get-NetTCPConnection -LocalPort 5000).OwningProcess | Stop-Process -Force

# Then start server
cd backend
npm start
```

### Or Use the Script:

```powershell
cd backend
.\start-server.ps1
```

---

## Step-by-Step Fix:

1. **Stop all Node processes:**
   ```powershell
   Get-Process node -ErrorAction SilentlyContinue | Stop-Process -Force
   ```

2. **Navigate to backend:**
   ```powershell
   cd backend
   ```

3. **Install dependencies (if needed):**
   ```powershell
   npm install
   ```

4. **Start server:**
   ```powershell
   npm start
   ```

---

## If You Still See Errors:

1. **Check if multer is installed:**
   ```powershell
   npm list multer
   ```
   If not installed: `npm install multer`

2. **Check for missing dependencies:**
   ```powershell
   npm install
   ```

3. **Check the error message** - it will tell you what's wrong

---

## Alternative: Use Different Port

Edit `backend/.env` file:
```
PORT=5001
```

Then start server:
```powershell
npm start
```




# 🚀 Complete Setup Guide - FTC Scout

## Problem: NPM Not Installing

If you get an error like `npm: The term 'npm' is not recognized`, it means Node.js isn't installed yet.

## Solution: Install Node.js

### Windows - Step by Step

1. **Download Node.js**
   - Go to https://nodejs.org/
   - Click the **green "LTS" button** (Recommended For Most Users)
   - This downloads a file like `node-v20.11.0-x64.msi`

2. **Run the Installer**
   - Double-click the downloaded `.msi` file
   - Click "Next" through the setup wizard
   - **Important:** On the "Tools for Native Modules" screen, check the box
   - Click "Finish"

3. **Restart Your Computer**
   - This is important! Windows needs to refresh its PATH

4. **Verify Installation**
   - Open PowerShell (Windows key + X → Windows PowerShell)
   - Type: `node --version`
   - Should show: `v20.11.0` (or similar)
   - Type: `npm --version`
   - Should show: `10.2.4` (or similar)

## Now Install the App

Once Node.js is installed:

1. **Open PowerShell in the FTCSCOUT folder**
   - Navigate to `C:\Users\mmuen\FTCSCOUT`
   - Hold Shift + Right-click in the folder
   - Select "Open PowerShell window here"

2. **Install Dependencies**
   ```powershell
   npm install
   ```
   - This takes 30-60 seconds
   - Downloads all required packages

3. **Start the Server**
   ```powershell
   npm start
   ```
   - You should see: `🤖 FTC Scout server running on port 3000`

4. **Open Your Browser**
   - Go to: http://localhost:3000
   - Your app is now running!

## Making It Public

### Option 1: Render (Easiest, Free Forever)

1. **Create a GitHub Account** (if you don't have one)
   - Go to https://github.com/signup

2. **Install Git** (if not installed)
   - Download from https://git-scm.com/download/win
   - Install with default settings

3. **Create a Repository on GitHub**
   - Go to https://github.com/new
   - Name: `ftcscout-22351`
   - Keep it Public
   - Click "Create repository"

4. **Push Your Code**
   ```powershell
   git init
   git add .
   git commit -m "Initial FTC Scout app"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/ftcscout-22351.git
   git push -u origin main
   ```

5. **Deploy on Render**
   - Go to https://render.com
   - Sign up (free) using your GitHub account
   - Click "New +" → "Web Service"
   - Click "Connect account" to link GitHub
   - Select your `ftcscout-22351` repository
   - Settings:
     - **Name:** `ftcscout-22351`
     - **Environment:** `Node`
     - **Build Command:** `npm install`
     - **Start Command:** `npm start`
     - **Plan:** Free
   - Click "Advanced" → "Add Environment Variable"
     - **Key:** `VIEW_PASSWORD`
     - **Value:** `your-secure-password` (choose something strong!)
   - Click "Create Web Service"
   - Wait 5-10 minutes for deployment

6. **Your App is Live!**
   - URL will be like: `https://ftcscout-22351.onrender.com`
   - Share the submit page with other teams: `https://ftcscout-22351.onrender.com/submit.html`
   - View data (password protected): `https://ftcscout-22351.onrender.com/view.html`

### Option 2: Railway (Alternative)

1. Follow steps 1-4 from Render guide above
2. Go to https://railway.app
3. Sign up with GitHub
4. Click "New Project" → "Deploy from GitHub repo"
5. Select your repository
6. Add environment variable: `VIEW_PASSWORD`
7. Deploy!

## Changing the Password

### For Local Development
Edit line 11 in `server.js`:
```javascript
const VIEW_PASSWORD = process.env.VIEW_PASSWORD || 'YOUR_NEW_PASSWORD';
```

### For Deployed App
1. Go to your Render/Railway dashboard
2. Select your project
3. Go to "Environment" or "Variables"
4. Change `VIEW_PASSWORD` value
5. Redeploy

## Troubleshooting

### "Running scripts is disabled on this system"

This is a Windows PowerShell security setting. Here's how to fix it:

**Option 1: Run as Administrator (Recommended)**
1. Close PowerShell
2. Press Windows key, type "PowerShell"
3. Right-click "Windows PowerShell"
4. Select "Run as administrator"
5. Run this command:
   ```powershell
   Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
   ```
6. Type `Y` and press Enter
7. Now try `npm install` again

**Option 2: Bypass for Single Command**
Instead of `npm install`, run:
```powershell
npx npm install
```

**Option 3: Use Command Prompt Instead**
1. Press Windows key + R
2. Type `cmd` and press Enter
3. Navigate to your folder:
   ```cmd
   cd C:\Users\mmuen\FTCSCOUT
   ```
4. Run `npm install`

### "npm install" fails
- Make sure you restarted your computer after installing Node.js
- Try closing and reopening PowerShell
- Run PowerShell as Administrator

### "Port 3000 is already in use"
- Another app is using port 3000
- Change the port in `server.js` or kill the process:
  ```powershell
  netstat -ano | findstr :3000
  taskkill /PID [PID_NUMBER] /F
  ```

### Can't access on mobile devices
- Make sure your phone is on the same WiFi
- Find your computer's IP: `ipconfig`
- Access from phone: `http://YOUR_IP:3000`

### Data not saving
- Check that the `data` folder exists
- Make sure you have write permissions
- Check console for errors (F12 in browser)

## Next Steps

1. ✅ Install Node.js
2. ✅ Run `npm install`
3. ✅ Run `npm start`
4. ✅ Test locally
5. ✅ Deploy to Render
6. ✅ Share with your team!

Need help? Check the main README.md or open an issue on GitHub.

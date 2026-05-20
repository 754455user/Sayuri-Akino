# 🚀 Render.com Deployment Guide

## Bugs Fixed in This Version:
1. ✅ `FloodWait.x` → `FloodWait.value` (helper_func.py, start.py)
2. ✅ Sync `pymongo` → Async `motor` (database.py)
3. ✅ Python 3.10 Dockerfile
4. ✅ Added render.yaml

## Step-by-Step Render Deployment:

### 1. Push to GitHub
```bash
git add .
git commit -m "Fix bugs + Render deployment"
git push
```

### 2. Create Render Account
- Go to https://render.com
- Sign up / Login

### 3. New Service
- Click "New +" → "Background Worker"
- Connect your GitHub repo
- Select the repo

### 4. Configure Settings
| Setting | Value |
|---------|-------|
| Name | file-sharing-bot |
| Environment | Python 3 |
| Build Command | `pip install -r requirements.txt` |
| Start Command | `python3 main.py` |

### 5. Add Environment Variables
Go to Environment tab and add:

| Variable | Value |
|----------|-------|
| `TG_BOT_TOKEN` | Your bot token from @BotFather |
| `APP_ID` | From my.telegram.org |
| `API_HASH` | From my.telegram.org |
| `CHANNEL_ID` | Your DB channel ID (e.g. -1001234567890) |
| `OWNER_ID` | Your Telegram user ID |
| `DATABASE_URL` | MongoDB URI from MongoDB Atlas |
| `DATABASE_NAME` | filesharexbot |
| `FORCE_SUB_CHANNEL` | 0 (or channel ID if want force sub) |
| `PORT` | 8080 |

### 6. Deploy
- Click "Create Background Worker"
- Wait for build to complete ✅

## MongoDB Atlas Free Setup:
1. Go to https://mongodb.com/atlas
2. Create free cluster
3. Get connection string
4. Replace `<password>` in URI
5. Add to DATABASE_URL env var

## Common Errors & Fixes:
- **FloodWait error** → Already fixed in this version
- **Database error** → Check DATABASE_URL is correct MongoDB URI
- **Bot not starting** → Check TG_BOT_TOKEN is valid
- **CHANNEL_ID error** → Make sure bot is admin in the channel

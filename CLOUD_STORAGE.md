# Cloud Storage Integration Guide

## Overview
The FTC Scout app currently stores data locally in JSON files. This guide explains how to integrate cloud storage for data persistence and synchronization.

## Supported Cloud Services

### Option 1: Firebase (Recommended)
**Pros:** Free tier, real-time sync, easy setup  
**Best for:** Quick deployment, real-time updates

**Setup Steps:**
1. Install Firebase Admin SDK:
   ```bash
   npm install firebase-admin
   ```

2. Create Firebase project at https://console.firebase.google.com

3. Add to `server.js`:
   ```javascript
   const admin = require('firebase-admin');
   const serviceAccount = require('./firebase-key.json');
   
   admin.initializeApp({
     credential: admin.credential.cert(serviceAccount),
     databaseURL: "https://your-project.firebaseio.com"
   });
   ```

4. Uncomment cloud sync functions in `server.js`

### Option 2: MongoDB Atlas
**Pros:** Free tier, flexible queries, scalable  
**Best for:** Complex data analysis, large datasets

**Setup Steps:**
1. Install MongoDB driver:
   ```bash
   npm install mongodb
   ```

2. Create cluster at https://www.mongodb.com/cloud/atlas

3. Add connection string to environment variables:
   ```
   CLOUD_STORAGE_URL=mongodb+srv://username:password@cluster.mongodb.net/ftc
   ```

### Option 3: AWS S3 + DynamoDB
**Pros:** Highly scalable, enterprise-grade  
**Best for:** Large-scale deployment

**Setup Steps:**
1. Install AWS SDK:
   ```bash
   npm install aws-sdk
   ```

2. Configure AWS credentials

3. Set environment variables:
   ```
   AWS_ACCESS_KEY_ID=your_key
   AWS_SECRET_ACCESS_KEY=your_secret
   AWS_REGION=us-east-1
   ```

## Environment Variables

Add these to your `.env` file or hosting platform:

```env
# Enable cloud storage
CLOUD_STORAGE_ENABLED=true

# Cloud service URL (varies by provider)
CLOUD_STORAGE_URL=your_cloud_url

# API key or credentials
CLOUD_STORAGE_KEY=your_api_key

# Optional: Backup to local files
LOCAL_BACKUP=true
```

## Implementation Checklist

- [ ] Choose cloud provider
- [ ] Install required packages
- [ ] Create cloud account and project
- [ ] Configure credentials
- [ ] Uncomment cloud sync functions in `server.js`
- [ ] Test data upload/download
- [ ] Set up automatic backups
- [ ] Update environment variables on Render

## Testing

Test cloud storage locally before deploying:

```bash
# Set environment variable
$env:CLOUD_STORAGE_ENABLED="true"  # Windows PowerShell
export CLOUD_STORAGE_ENABLED=true   # Mac/Linux

# Start server
npm start

# Submit test data and verify it appears in cloud dashboard
```

## Deployment on Render

1. Go to Render dashboard → Your service → Environment
2. Add environment variables
3. Redeploy service

## Data Migration

To migrate existing local data to cloud:

1. Export current data:
   - Go to dashboard → Tools tab → Backup All Data

2. Upload to cloud:
   - Run migration script (create one based on your cloud provider)
   - Or manually import JSON to cloud database

## Need Help?

Common cloud providers documentation:
- Firebase: https://firebase.google.com/docs
- MongoDB Atlas: https://docs.atlas.mongodb.com
- AWS: https://docs.aws.amazon.com

For FTC-specific questions, check the team documentation or ask your team lead.

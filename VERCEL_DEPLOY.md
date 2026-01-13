# Vercel Deployment Guide

## 🚀 Quick Start (3 Steps)

### Step 1: Install Vercel CLI
```bash
npm install -g vercel
```

### Step 2: Login to Vercel
```bash
vercel login
```
Follow the prompts to authenticate.

### Step 3: Deploy
```bash
vercel
```
Follow the prompts:
- **Set up and deploy?** → Yes
- **Which scope?** → Your account
- **Link to existing project?** → No
- **Project name?** → ftc-scout-22351 (or your choice)
- **Directory?** → ./ (press Enter)
- **Override settings?** → No

Done! Your app will be live at: `https://your-project.vercel.app`

## 🔐 Set Environment Variables

After first deployment, add your passwords:

```bash
vercel env add VIEW_PASSWORD
# Enter: 22351

vercel env add DEV_PASSWORD
# Enter: dev22351admin
```

Then redeploy:
```bash
vercel --prod
```

## 🔄 Automatic Deployments (GitHub)

### One-time setup:
1. Push your code to GitHub
2. Go to https://vercel.com/dashboard
3. Click "New Project"
4. Import your GitHub repository
5. Add environment variables in Vercel dashboard:
   - `VIEW_PASSWORD` = `22351`
   - `DEV_PASSWORD` = `dev22351admin`
6. Deploy!

**Now every git push automatically deploys!** 🎉

## 📝 Custom Domain (Optional)

1. Go to Vercel dashboard → Your project → Settings → Domains
2. Add your domain (e.g., `team22351.com`)
3. Update DNS records as instructed
4. SSL certificate added automatically

## 🆚 Vercel vs Render

| Feature | Vercel | Render |
|---------|--------|--------|
| Cold starts | ❌ None | ✅ 15-min sleep |
| Speed | ⚡ Fast | 🐌 Slower |
| Free tier | ✅ Generous | ⚠️ Limited |
| Setup time | 30 seconds | 5 minutes |
| Auto-deploy | ✅ Yes | ✅ Yes |

## 🛠️ Troubleshooting

### Data persistence:
Vercel is serverless, so file storage won't persist between deployments. You'll need cloud storage for production:
- Enable Firebase/MongoDB (see CLOUD_STORAGE.md)
- Or use Vercel KV storage (Redis-based, built-in)

### To use Vercel KV:
```bash
npm install @vercel/kv
```

Then in your code:
```javascript
import { kv } from '@vercel/kv';

// Store data
await kv.set('match-data', matchData);

// Retrieve data
const data = await kv.get('match-data');
```

### Logs:
View real-time logs:
```bash
vercel logs
```

Or check dashboard: https://vercel.com/dashboard

## 🎯 Production Checklist

- [ ] Deploy to Vercel
- [ ] Add environment variables
- [ ] Test login with password
- [ ] Submit test scouting data
- [ ] Set up cloud storage (Firebase recommended)
- [ ] Add custom domain (optional)
- [ ] Test on mobile devices

## 💡 Pro Tips

1. **Preview deployments**: Every branch gets its own URL for testing
2. **Rollback**: Instant rollback to previous deployments in dashboard
3. **Analytics**: Free analytics built-in (vercel.com/analytics)
4. **Edge functions**: Runs your code globally (super fast)

## 🆘 Need Help?

- Vercel Docs: https://vercel.com/docs
- Discord: https://vercel.com/discord
- Or ask your team lead!

## ⚡ Your App URLs

After deployment, you'll have:
- Production: `https://ftc-scout-22351.vercel.app`
- Preview: `https://ftc-scout-22351-git-branch.vercel.app` (per branch)
- Local: `http://localhost:3000`

**Always on. No sleep. Lightning fast.** 🚀

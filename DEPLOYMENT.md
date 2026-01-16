# 🚀 Deployment Guide

## Render.com Deployment

### Prerequisites
- GitHub account
- Render.com account
- MongoDB Atlas account

### Step 1: Prepare MongoDB Atlas
1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a free cluster
3. Create a database user
4. Whitelist all IPs (0.0.0.0/0) for Render.com
5. Get your connection string

### Step 2: Deploy Backend

1. Go to [Render Dashboard](https://dashboard.render.com/)
2. Click "New +" → "Web Service"
3. Connect your GitHub repository
4. Configure:
   - **Name**: `telegram-clone-backend`
   - **Region**: Oregon (US West)
   - **Branch**: `main`
   - **Root Directory**: `server`
   - **Environment**: `Node`
   - **Build Command**: `npm install`
   - **Start Command**: `node index.js`
   - **Plan**: Free

5. Add Environment Variables:
   ```
   NODE_ENV=production
   PORT=3001
   MONGODB_URI=your_mongodb_connection_string
   JWT_SECRET=your_random_secret_key_here
   CLIENT_URL=https://your-frontend-url.onrender.com
   ```

6. Click "Create Web Service"

### Step 3: Deploy Frontend

1. In Render Dashboard, click "New +" → "Static Site"
2. Connect your GitHub repository
3. Configure:
   - **Name**: `telegram-clone-frontend`
   - **Branch**: `main`
   - **Root Directory**: `client`
   - **Build Command**: `npm install && npm run build`
   - **Publish Directory**: `dist`

4. Add Environment Variable:
   ```
   VITE_API_URL=https://your-backend-url.onrender.com
   ```

5. Click "Create Static Site"

### Step 4: Update Environment Variables

After both services are deployed:

1. Go to backend service settings
2. Update `CLIENT_URL` with your frontend URL
3. Go to frontend service settings  
4. Update `VITE_API_URL` with your backend URL
5. Trigger manual deploy for both services

### Step 5: Test

1. Visit your frontend URL
2. Try logging in with phone number
3. Send messages
4. Upload files
5. Create groups

## Alternative: Vercel + Railway

### Frontend (Vercel)
```bash
npm install -g vercel
cd client
vercel
```

### Backend (Railway)
1. Go to [Railway](https://railway.app/)
2. New Project → Deploy from GitHub
3. Select your repository
4. Add environment variables
5. Deploy

## Troubleshooting

### Build Errors
- Check Node.js version (use v18 or higher)
- Clear build cache in Render dashboard
- Check environment variables

### Connection Issues
- Verify MongoDB Atlas IP whitelist
- Check CORS settings in backend
- Verify environment variable URLs

### File Upload Issues
- Render free tier has ephemeral storage
- Consider using cloud storage (AWS S3, Cloudinary)

## Performance Tips

1. **Enable Caching**: Add cache headers in backend
2. **Optimize Images**: Compress before upload
3. **Use CDN**: For static assets
4. **Database Indexing**: Already configured in models

## Monitoring

- Check Render logs for errors
- Monitor MongoDB Atlas metrics
- Set up uptime monitoring (UptimeRobot)

## Costs

- **Render Free Tier**: 
  - 750 hours/month
  - Sleeps after 15 min inactivity
  - 512 MB RAM

- **MongoDB Atlas Free Tier**:
  - 512 MB storage
  - Shared cluster

## Upgrade Options

For production use, consider:
- Render Starter ($7/month) - No sleep
- MongoDB Atlas M10 ($57/month) - Dedicated cluster
- Cloud storage for files

---

Need help? Open an issue on GitHub!

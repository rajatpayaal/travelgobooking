# Quick Setup Guide: Connect Frontend to Your Render Backend

## 🎯 What You Need to Do

The IP addresses you provided (35.160.120.126, etc.) are Render's infrastructure IPs. You need your **service URL** instead.

## 📍 Step 1: Find Your Backend Service URL

1. Go to your [Render Dashboard](https://dashboard.render.com)
2. Click on your **backend service** (not the frontend)
3. Look for the URL at the top - it will look like:
   ```
   https://your-service-name.onrender.com
   ```

## 📍 Step 2: Configure Your Frontend

When deploying your frontend to Render, add this environment variable:

**Environment Variable:**
- **Key**: `VITE_API_BASE`
- **Value**: `https://psquare-assignment-1z8u.onrender.com/api`

## 📍 Step 3: Your Specific Configuration

Your backend service URL is `https://psquare-assignment-1z8u.onrender.com`, so set:
```
VITE_API_BASE=https://psquare-assignment-1z8u.onrender.com/api
```

## 📍 Step 4: Deploy Your Frontend

1. Push your code to GitHub
2. Create a new **Static Site** on Render
3. Connect your repository
4. Use these settings:
   - **Build Command**: `npm install && npm run build`
   - **Publish Directory**: `dist`
   - **Environment Variable**: `VITE_API_BASE` = your backend URL

## ✅ Your Frontend is Already Configured!

Your `apiService.js` will automatically use the environment variable:
```javascript
baseURL: import.meta.env.VITE_BACKEND_URL || import.meta.env.VITE_API_BASE || 'http://localhost:5000/api'
```

## 🔧 Troubleshooting

- **Can't find backend URL?** Look in your Render dashboard under your backend service
- **API calls failing?** Check CORS settings on your backend
- **Environment variable not working?** Make sure it starts with `VITE_`

Need the exact backend URL? Check your Render dashboard and share the service name!
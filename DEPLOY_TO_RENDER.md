# Deploying Travel Booking Frontend to Render

## Prerequisites
- A GitHub repository with your frontend code
- A Render account (sign up at https://render.com)
- Your backend API already deployed (if applicable)

## Step-by-Step Deployment Guide

### 1. Prepare Your Repository
Make sure your code is pushed to GitHub with all the configuration files:
- `render.yaml` (already created)
- `public/_redirects` (already created)
- Updated `vite.config.js` (already updated)

### 2. Create a New Web Service on Render

1. **Log in to Render Dashboard**
   - Go to https://dashboard.render.com
   - Click "New +" button
   - Select "Static Site"

2. **Connect Your Repository**
   - Choose "Connect a repository"
   - Select your GitHub repository: `travelgobooking`
   - Click "Connect"

### 3. Configure Your Static Site

**Basic Settings:**
- **Name**: `travel-booking-frontend` (or your preferred name)
- **Branch**: `master` (or your main branch)
- **Root Directory**: Leave empty (uses root of repo)

**Build Settings:**
- **Build Command**: `npm install && npm run build`
- **Publish Directory**: `dist`

**Advanced Settings:**
- **Node Version**: `18` (or latest LTS)
- **Auto-Deploy**: Yes (recommended)

### 4. Environment Variables

Add these environment variables in Render:

**Required Variables:**
- `VITE_API_BASE`: Your backend API URL (e.g., `https://your-backend-service-name.onrender.com/api`)
- `VITE_BACKEND_URL`: Same as above (backup variable)

**Optional Variables:**
- `NODE_ENV`: `production`
- `VITE_APP_NAME`: `Travel Booking System`

#### How to Find Your Backend URL:
1. Go to your Render dashboard
2. Click on your backend service
3. Copy the URL from the service overview (e.g., `https://your-service-name.onrender.com`)
4. Add `/api` at the end if your backend uses `/api` as the base path

**Example:**
If your backend service URL is `https://travel-booking-api.onrender.com`, then set:
- `VITE_API_BASE` = `https://travel-booking-api.onrender.com/api`

### 5. Deploy

1. Click "Create Static Site"
2. Render will automatically:
   - Clone your repository
   - Install dependencies
   - Build your application
   - Deploy to a Render URL

### 6. Custom Domain (Optional)

After deployment:
1. Go to your service dashboard
2. Click "Settings" tab
3. Scroll to "Custom Domains"
4. Add your domain and configure DNS

## Important Notes

### API Configuration
Your frontend is configured to use:
```javascript
baseURL: import.meta.env.VITE_BACKEND_URL || import.meta.env.VITE_API_BASE || 'http://localhost:5000/api'
```

Make sure to set `VITE_API_BASE` environment variable to your deployed backend URL.

### Routing
The `_redirects` file ensures all routes are handled by your React Router:
```
/*    /index.html   200
```

### Build Optimization
Your `vite.config.js` is optimized for production:
- Output directory: `dist`
- Chunk size warning limit: 1600kb
- Source maps disabled for production

## Troubleshooting

### Common Issues:

1. **Build Fails**
   - Check Node.js version (should be 18+)
   - Ensure all dependencies are in `package.json`
   - Check for TypeScript errors

2. **API Calls Fail**
   - Verify `VITE_API_BASE` environment variable
   - Check CORS settings on your backend
   - Ensure backend is deployed and accessible

3. **404 Errors on Refresh**
   - Ensure `_redirects` file exists in `public` directory
   - Check that the file is being copied to `dist` during build

4. **Environment Variables Not Working**
   - Vite only includes variables prefixed with `VITE_`
   - Variables must be set in Render dashboard
   - Restart deployment after adding variables

## Next Steps

1. Deploy your backend API (if not already done)
2. Update the `VITE_API_BASE` environment variable
3. Test all functionality on the deployed site
4. Set up custom domain (optional)
5. Configure monitoring and analytics

## Resources

- [Render Static Sites Documentation](https://render.com/docs/static-sites)
- [Vite Environment Variables](https://vitejs.dev/guide/env-and-mode.html)
- [React Router on Static Hosts](https://reactrouter.com/en/main/guides/deploy)
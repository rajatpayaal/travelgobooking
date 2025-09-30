# ✅ Frontend to Backend Connection - READY TO DEPLOY!

## Your Backend URL
🔗 **https://psquare-assignment-1z8u.onrender.com**

## Configuration Summary

### ✅ Files Updated:
- `.env.local` - For local development
- `.env.example` - Template with your backend URL
- `QUICK_SETUP.md` - Updated with your specific URL

### ✅ Environment Variable to Use:
```
VITE_API_BASE=https://psquare-assignment-1z8u.onrender.com/api
```

## 🚀 Next Steps:

### 1. Test Locally (Optional)
```bash
npm install
npm run dev
```
Your frontend will now connect to your deployed backend!

### 2. Deploy to Render
1. Push your code to GitHub
2. Go to [Render Dashboard](https://dashboard.render.com)
3. Create new **Static Site**
4. Connect your `travelgobooking` repository
5. Use these settings:
   - **Build Command**: `npm install && npm run build`
   - **Publish Directory**: `dist`
   - **Environment Variable**: 
     - Key: `VITE_API_BASE`
     - Value: `https://psquare-assignment-1z8u.onrender.com/api`

### 3. Your API Calls Will Work!
Your `apiService.js` is already configured to use:
```javascript
baseURL: import.meta.env.VITE_BACKEND_URL || import.meta.env.VITE_API_BASE || 'http://localhost:5000/api'
```

## 🔧 CORS Configuration (Important!)
Make sure your backend at `https://psquare-assignment-1z8u.onrender.com` allows CORS for your frontend domain.

## ✅ Ready to Deploy!
Everything is configured. Your frontend will successfully connect to your backend once deployed!
# 🚀 Deployment Guide

This guide covers different deployment options for the Vapi Call Center application.

## 📋 Prerequisites

Before deploying, ensure you have:
- All required Vapi credentials (API keys, Assistant ID, Phone Number ID)
- A hosting service account (Vercel, Netlify, Railway, etc.)
- Environment variables configured

## 🌐 Frontend Deployment

### Vercel (Recommended)

1. **Connect Repository**
   ```bash
   # Install Vercel CLI
   npm i -g vercel
   
   # Deploy from project directory
   vercel
   ```

2. **Environment Variables**
   Add these in Vercel dashboard:
   ```
   VITE_VAPI_PUBLIC_API_KEY=your_public_key
   VITE_ASSISTANT_ID=your_assistant_id
   VITE_DEFAULT_PHONE_NUMBER_ID=your_phone_number_id
   ```

3. **Build Settings**
   - Build Command: `npm run build`
   - Output Directory: `dist`
   - Install Command: `npm install`

### Netlify

1. **Deploy via Git**
   - Connect your GitHub repository
   - Set build command: `npm run build`
   - Set publish directory: `dist`

2. **Environment Variables**
   Add in Netlify dashboard under Site Settings > Environment Variables

## 🖥️ Backend Deployment

### Railway (Recommended)

1. **Connect Repository**
   ```bash
   # Install Railway CLI
   npm install -g @railway/cli
   
   # Login and deploy
   railway login
   railway link
   railway up
   ```

2. **Environment Variables**
   ```bash
   railway variables set VAPI_API_KEY=your_private_key
   railway variables set PORT=3001
   railway variables set N8N_WEBHOOK_URL=your_webhook_url
   ```

### Render

1. **Create Web Service**
   - Connect GitHub repository
   - Build Command: `npm run build:server`
   - Start Command: `npm run start:server`

2. **Environment Variables**
   Add in Render dashboard:
   ```
   VAPI_API_KEY=your_private_key
   PORT=10000
   NODE_ENV=production
   ```

### Heroku

1. **Deploy via Git**
   ```bash
   # Install Heroku CLI and login
   heroku create your-app-name
   
   # Set environment variables
   heroku config:set VAPI_API_KEY=your_private_key
   heroku config:set NODE_ENV=production
   
   # Deploy
   git push heroku main
   ```

2. **Procfile**
   Create a `Procfile` in project root:
   ```
   web: npm run start:server
   ```

## 🔄 Full-Stack Deployment

### Single Platform (Vercel + Serverless Functions)

1. **API Routes**
   Move server endpoints to `api/` directory for Vercel serverless functions

2. **Configuration**
   Update `vercel.json`:
   ```json
   {
     "functions": {
       "api/**/*.ts": {
         "runtime": "@vercel/node"
       }
     },
     "rewrites": [
       {
         "source": "/api/(.*)",
         "destination": "/api/$1"
       }
     ]
   }
   ```

### Docker Deployment

1. **Create Dockerfile**
   ```dockerfile
   FROM node:18-alpine
   
   WORKDIR /app
   
   COPY package*.json ./
   RUN npm ci --only=production
   
   COPY . .
   RUN npm run build
   RUN npm run build:server
   
   EXPOSE 3001
   
   CMD ["npm", "run", "start:server"]
   ```

2. **Docker Compose**
   ```yaml
   version: '3.8'
   services:
     app:
       build: .
       ports:
         - "3001:3001"
       environment:
         - VAPI_API_KEY=${VAPI_API_KEY}
         - NODE_ENV=production
   ```

## 🔒 Security Considerations

### Environment Variables
- Never commit `.env` files
- Use platform-specific secret management
- Rotate API keys regularly

### HTTPS
- Always use HTTPS in production
- Configure SSL certificates
- Enable HSTS headers

### CORS
- Configure CORS for your domain
- Restrict origins in production
- Use environment-specific settings

## 📊 Monitoring & Analytics

### Error Tracking
```bash
# Add Sentry for error tracking
npm install @sentry/react @sentry/node
```

### Performance Monitoring
- Use platform-specific monitoring (Vercel Analytics, Railway Metrics)
- Monitor API response times
- Track voice call success rates

## 🔧 Production Optimizations

### Frontend
- Enable gzip compression
- Configure CDN for static assets
- Implement service worker for caching
- Optimize bundle size

### Backend
- Enable request compression
- Implement rate limiting
- Add request logging
- Configure health checks

## 🚨 Troubleshooting

### Common Issues

1. **CORS Errors**
   - Check origin configuration
   - Verify environment variables
   - Test API endpoints directly

2. **Voice Connection Issues**
   - Verify Vapi API keys
   - Check browser permissions
   - Test with different browsers

3. **Build Failures**
   - Check Node.js version compatibility
   - Verify all dependencies are installed
   - Review build logs for specific errors

### Health Checks

Test your deployment:
```bash
# Backend health check
curl https://your-api-domain.com/api/health

# Frontend accessibility
curl https://your-frontend-domain.com
```

## 📈 Scaling Considerations

- Use load balancers for high traffic
- Implement database for call history
- Add Redis for session management
- Consider microservices architecture

---

For deployment support, check the platform-specific documentation or create an issue in the repository.
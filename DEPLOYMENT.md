# Deployment Guide

This guide will help you deploy your AI-powered chatbot to various platforms.

## Full-Stack Solution

This chatbot frontend works with a separate backend server. For the complete full-stack solution:

**Backend Repository**: [AI Chatbot Server](https://github.com/yourusername/ai-chatbot-server)

### Quick Setup (Full-Stack)

1. **Clone both repositories**:

   ```bash
   # Frontend (this repo)
   git clone https://github.com/yourusername/ai-chatbot.git
   cd ai-chatbot

   # Backend (separate repo)
   git clone https://github.com/yourusername/ai-chatbot-server.git
   cd ai-chatbot-server
   ```

2. **Start the backend server**:

   ```bash
   cd ai-chatbot-server
   npm install
   npm start
   # Server will run on http://localhost:5100
   ```

3. **Start the frontend**:
   ```bash
   cd ../ai-chatbot
   npm install
   npm start
   # Frontend will be available at http://localhost:8000
   ```

The frontend is pre-configured to connect to `http://localhost:5100/api` for local development.

## GitHub Pages

1. **Push to GitHub**:

   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/yourusername/ai-chatbot.git
   git push -u origin main
   ```

2. **Enable GitHub Pages**:

   - Go to your repository settings
   - Scroll down to "Pages" section
   - Select "Deploy from a branch"
   - Choose "main" branch and "/ (root)" folder
   - Click "Save"

3. **Access your chatbot**:
   - Your chatbot will be available at: `https://yourusername.github.io/ai-chatbot/chatbot.html`

## Netlify

1. **Connect your repository**:

   - Go to [Netlify](https://netlify.com)
   - Click "New site from Git"
   - Connect your GitHub repository

2. **Configure build settings**:

   - Build command: (leave empty)
   - Publish directory: (leave empty or set to root)

3. **Deploy**:
   - Click "Deploy site"
   - Your chatbot will be available at the provided Netlify URL

## Vercel

1. **Install Vercel CLI**:

   ```bash
   npm install -g vercel
   ```

2. **Deploy**:

   ```bash
   vercel
   ```

3. **Follow the prompts** and your chatbot will be deployed.

## Custom Server

1. **Upload files** to your web server
2. **Ensure your server serves static files**
3. **Update API endpoints** in the JavaScript code if needed
4. **Configure HTTPS** for secure operation

## Environment Configuration

For production deployment, consider:

- **API Endpoint**: Update the `API_BASE_URL` constant in `chatbot.html`
  ```javascript
  const API_BASE_URL = "https://your-backend-domain.com/api";
  ```
- **Backend Deployment**: Deploy the server using the instructions in the [backend repository](https://github.com/yourusername/ai-chatbot-server)
- **CORS Settings**: Ensure your backend allows requests from your frontend domain
- **Security**: Implement proper authentication if needed
- **Analytics**: Add tracking code if required

## Production Deployment (Full-Stack)

### Option 1: Separate Hosting

1. **Deploy Backend**:
   - Deploy the server repo to Heroku, Railway, or your preferred platform
   - Update the `API_BASE_URL` in the frontend code
2. **Deploy Frontend**:
   - Use any of the methods below (GitHub Pages, Netlify, etc.)

### Option 2: Same Platform

1. **Vercel/Netlify with Serverless Functions**:
   - Deploy backend as serverless functions
   - Deploy frontend as static site
   - Configure environment variables

### Option 3: VPS/Cloud Server

1. **Deploy both on the same server**:
   - Set up reverse proxy (nginx)
   - Configure SSL certificates
   - Set up process management (PM2)

## Troubleshooting

### CORS Issues

If you encounter CORS errors:

1. Ensure your backend server includes proper CORS headers
2. Use a proxy server for development
3. Consider using a CORS proxy service

### LocalStorage Issues

- LocalStorage works only over HTTPS in production
- Consider using sessionStorage for temporary data
- Implement server-side session management for critical data

### Performance

- Minify CSS and JavaScript for production
- Optimize images in the assets folder
- Use a CDN for better global performance

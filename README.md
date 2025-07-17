[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=19951764&assignment_repo_type=AssignmentRepo)
# Deployment and DevOps for MERN Applications

This assignment focuses on deploying a full MERN stack application to production, implementing CI/CD pipelines, and setting up monitoring for your application.

## Assignment Overview

You will:
1. Prepare your MERN application for production deployment
2. Deploy the backend to a cloud platform
3. Deploy the frontend to a static hosting service
4. Set up CI/CD pipelines with GitHub Actions
5. Implement monitoring and maintenance strategies

## Getting Started

1. Accept the GitHub Classroom assignment invitation
2. Clone your personal repository that was created by GitHub Classroom
3. Follow the setup instructions in the `Week7-Assignment.md` file
4. Use the provided templates and configuration files as a starting point

## Files Included

- `Week7-Assignment.md`: Detailed assignment instructions
- `.github/workflows/`: GitHub Actions workflow templates
- `deployment/`: Deployment configuration files and scripts
- `.env.example`: Example environment variable templates
- `monitoring/`: Monitoring configuration examples

## Requirements

- A completed MERN stack application from previous weeks
- Accounts on the following services:
  - GitHub
  - MongoDB Atlas
  - Render, Railway, or Heroku (for backend)
  - Vercel, Netlify, or GitHub Pages (for frontend)
- Basic understanding of CI/CD concepts

## Deployment Platforms

### Backend Deployment Options
- **Render**: Easy to use, free tier available
- **Railway**: Developer-friendly, generous free tier
- **Heroku**: Well-established, extensive documentation

### Frontend Deployment Options
- **Vercel**: Optimized for React apps, easy integration
- **Netlify**: Great for static sites, good CI/CD
- **GitHub Pages**: Free, integrated with GitHub

## CI/CD Pipeline

The assignment includes templates for setting up GitHub Actions workflows:
- `frontend-ci.yml`: Tests and builds the React application
- `backend-ci.yml`: Tests the Express.js backend
- `frontend-cd.yml`: Deploys the frontend to your chosen platform
- `backend-cd.yml`: Deploys the backend to your chosen platform

## Submission

Your work will be automatically submitted when you push to your GitHub Classroom repository. Make sure to:

1. Complete all deployment tasks
2. Set up CI/CD pipelines with GitHub Actions
3. Deploy both frontend and backend to production
4. Document your deployment process in the README.md
5. Include screenshots of your CI/CD pipeline in action
6. Add URLs to your deployed applications

## Resources

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [MongoDB Atlas Documentation](https://docs.atlas.mongodb.com/)
- [Render Documentation](https://render.com/docs)
- [Railway Documentation](https://docs.railway.app/)
- [Vercel Documentation](https://vercel.com/docs)
- [Netlify Documentation](https://docs.netlify.com/)
  ## answer
  # GitHub Actions CI/CD Workflow (.github/workflows/main.yml)

  name: MERN CI/CD Pipeline

on:

  push:
  
    branches: [ main ]
    
  pull_request:
  
    branches: [ main ]

jobs:

  backend:
  
    runs-on: ubuntu-latest
    
    name: Backend Test and Deploy
    
    steps:
    
      - name: Checkout code
      
        uses: actions/checkout@v3

      - name: Set up Node.js
      
        uses: actions/setup-node@v3
        
        with:
        
          node-version: 18

      - name: Install backend dependencies
      
        run: |
        
          cd backend
          
          npm ci

      - name: Run backend tests
      
        run: |
        
          cd backend
          
          npm test

  frontend:
  
    runs-on: ubuntu-latest
    
    name: Frontend Build and Deploy
    
    steps:
    
      - name: Checkout code
      
        uses: actions/checkout@v3

      - name: Set up Node.js
      
        uses: actions/setup-node@v3
        
        with:
        
          node-version: 18

      - name: Install frontend dependencies
      
        run: |
        
          cd frontend
          
          npm ci

      - name: Build React App
      
        run: |
        
          cd frontend
          
          npm run build

      - name: Deploy to Vercel
      
        uses: amondnet/vercel-action@v25
        
        with:
        
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          
          working-directory: ./frontend
          
##  Environment Variable Templates
# backend/.env.example

PORT=5000

MONGO_URI=your_mongodb_uri_here

NODE_ENV=production

JWT_SECRET=your_jwt_secret_here

SENTRY_DSN=your_sentry_dsn_here

# frontend/.env.example

REACT_APP_API_URL=https://your-backend-api-url.com/api

REACT_APP_SENTRY_DSN=your_sentry_dsn_here

##  MERN Stack Application Deployment

This is a full-stack MERN application deployed to production with CI/CD automation, environment configuration, and application monitoring.

## 🚀 Live Links

- **Frontend**: [https://your-frontend-url.vercel.app](https://your-frontend-url.vercel.app)
- 
- **Backend API**: [https://your-backend-url.onrender.com/api](https://your-backend-url.onrender.com/api)

---

## 📦 Tech Stack

- **Frontend**: React, Vite/CRA, TailwindCSS (if used)
- 
- **Backend**: Node.js, Express
- 
- **Database**: MongoDB Atlas
- 
- **CI/CD**: GitHub Actions
- 
- **Deployment**:
- 
  - Frontend: Vercel
  - 
  - Backend: Render
  - 
- **Monitoring**: Sentry, UptimeRobot, Logging with Morgan/Winston

---

## 📁 Project Structure

root/
│
├── frontend/ # React App
│ └── .env # Environment variables
│
├── backend/ # Express App
│ └── .env # Environment variables
│
└── .github/workflows/ # GitHub Actions CI/CD
└── main.yml


## ⚙️ Environment Variables

### `backend/.env.example`
```env
PORT=5000

MONGO_URI=your_mongo_connection_string

JWT_SECRET=your_jwt_secret

NODE_ENV=production

SENTRY_DSN=your_sentry_dsn

## To Deploy

# Push changes to main

git add .

git commit -m "Deploy new feature"

git push origin main

## Testing
# frontend

cd frontend

npm run test

# backend

cd backend

npm test



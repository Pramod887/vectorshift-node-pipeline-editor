# Deployment Package

This folder contains the production-ready build of the VectorShift Pipeline Builder.

## Contents

- **Frontend**: Production build of the React application
- **Backend**: Python FastAPI server files

## Deployment Instructions

### Frontend Deployment

The frontend is a static React build. You can deploy it to:

- **Static Hosting**: Netlify, Vercel, GitHub Pages, AWS S3
- **Web Server**: Nginx, Apache, or any static file server

**To serve locally:**
```bash
# Install serve globally
npm install -g serve

# Serve the dist folder
serve -s .
```

### Backend Deployment

The backend is a FastAPI application. Deploy to:

- **Cloud Platforms**: Heroku, Railway, Render, AWS Elastic Beanstalk
- **VPS**: Any server with Python 3.8+

**To run the backend:**
```bash
cd backend
pip install -r requirements.txt
uvicorn main:app --host 0.0.0.0 --port 8000
```

### Environment Configuration

**Frontend API URL:**
Update the API endpoint in `frontend/src/submit.js` if your backend is hosted at a different URL:
```javascript
const response = await fetch('YOUR_BACKEND_URL/pipelines/parse', {
  // ...
});
```

**Backend CORS:**
Update CORS origins in `backend/main.py` to match your frontend domain:
```python
allow_origins=["http://localhost:3000", "YOUR_FRONTEND_URL"]
```

## Production Checklist

- [ ] Update API endpoint in frontend
- [ ] Configure CORS in backend
- [ ] Set up environment variables if needed
- [ ] Configure HTTPS/SSL certificates
- [ ] Set up database if required
- [ ] Configure logging and monitoring

## File Structure

```
dist/
├── static/          # Frontend static assets (JS, CSS, images)
├── index.html       # Main HTML file
├── backend/         # Backend Python files
│   ├── main.py
│   └── requirements.txt
└── README.md        # This file
```

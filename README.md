PM Internship Recommendation System
An AI-powered internship recommendation engine designed for the PM Internship Scheme. This system provides personalized internship suggestions based on user profiles, skills, and preferences using machine learning algorithms.
🚀 Features

AI-Powered Matching: Uses TF-IDF vectorization and cosine similarity for intelligent recommendations
Mobile-First Design: Responsive UI optimized for users with limited digital exposure
Real-Time Recommendations: Instant results with comprehensive match scoring
Multi-Factor Analysis: Considers skills, education, location, sector preferences, and experience
Simple & Intuitive: Clean interface with visual cues and minimal text
Scalable Architecture: Lightweight backend suitable for integration with existing portals

🏗️ Architecture
Frontend (Next.js + TypeScript)
↓ HTTP/JSON
Backend (FastAPI + Python)
↓ ML Processing
CSV Data Source
Technology Stack
Frontend:

Next.js 14 with TypeScript
Tailwind CSS for responsive design
React Hook Form for form management
Axios for API communication
Lucide React for icons

Backend:

FastAPI for high-performance API
scikit-learn for ML algorithms
pandas for data processing
Pydantic for data validation
Uvicorn as ASGI server

📋 Prerequisites
Before running this application, make sure you have:

Node.js 18+ and npm installed
Python 3.8+ installed
Git for version control
A code editor (VS Code recommended)

🔧 Installation & Setup
Step 1: Clone the Repository
bashgit clone <repository-url>
cd PM_INTERNSHIP_RECOMMENDATION_SYSTEM
Step 2: Backend Setup
bash# Navigate to backend directory
cd backend

# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Verify installation
python -c "import fastapi, uvicorn, pandas, sklearn; print('✅ All dependencies installed')"
Step 3: Frontend Setup
bash# Navigate to frontend directory (from project root)
cd frontend

# Install dependencies
npm install

# Verify installation
npm run type-check
Step 4: Running the Application
Terminal 1 - Start Backend Server:
bashcd backend
source venv/bin/activate  # On Windows: venv\Scripts\activate
python run.py
The backend will start at http://localhost:8000
Terminal 2 - Start Frontend Server:
bashcd frontend
npm run dev
The frontend will start at http://localhost:3000
Step 5: Test the Application

Open your browser and go to http://localhost:3000
Fill out the internship form with your details
Click "Get Recommendations" to see AI-powered suggestions

📊 Sample Data
The system comes with 30 sample internships across various sectors:

Technology (Software Development, Mobile Apps, Cybersecurity)
Healthcare (Research, Psychology, Biotechnology)
Finance, Marketing, Media
Engineering (Mechanical, Civil, Electrical, Chemical)
And many more...

🧠 AI/ML Features
Recommendation Algorithm

Text Vectorization: Uses TF-IDF to convert skills and job descriptions to numerical vectors
Cosine Similarity: Calculates similarity between user profile and internship requirements
Multi-Factor Scoring: Combines content similarity with business rules:

Skills matching (25% weight)
Content similarity (40% weight)
Location preference (20 points)
Sector preference (15 points)
Experience level matching (5 points)



Intelligent Filtering

Education Level: Ensures recommendations match qualification requirements
Skills Analysis: Identifies overlapping skills between user and job requirements
Location Matching: Prioritizes internships in preferred locations
Sector Preferences: Boosts scores for preferred industry sectors

🌐 API Documentation
Endpoints
GET /health - Health check
json{
  "status": "healthy",
  "data_loaded": true,
  "total_internships": 30
}
POST /recommend - Get recommendations
json{
  "name": "Rahul Sharma",
  "education_level": "undergraduate",
  "field_of_study": "Computer Science",
  "skills": ["Python", "JavaScript", "React"],
  "preferred_sectors": ["Technology", "Healthcare"],
  "preferred_location": "Delhi",
  "experience_years": 0
}
GET /sectors - Available sectors
GET /locations - Available locations
Interactive API Docs
Visit http://localhost:8000/docs for interactive Swagger documentation.
🔒 CORS Configuration
The backend is configured to accept requests from:

http://localhost:3000 (development frontend)
http://127.0.0.1:3000 (alternative localhost)

For production, update the allow_origins in app/main.py.
📱 Mobile Optimization
The interface is designed for users with limited digital exposure:

Large Touch Targets: Easy-to-tap buttons and form fields
Clear Visual Hierarchy: Important information stands out
Minimal Text: Uses icons and visual cues where possible
Responsive Design: Works on all screen sizes
Simple Navigation: Intuitive user flow

🚀 Deployment Options
Frontend Deployment (Vercel - Recommended)
bash# Install Vercel CLI
npm i -g vercel

# From frontend directory
cd frontend
vercel

# Follow prompts to deploy
Backend Deployment Options
Railway (Recommended):

Push code to GitHub
Connect Railway to your repository
Set up Python service
Deploy automatically

Render:

Connect GitHub repository
Create new Web Service
Use Python environment
Set build command: pip install -r requirements.txt
Set start command: python run.py

Heroku:
bash# Create Procfile in backend directory
echo "web: python run.py" > Procfile

# Deploy to Heroku
heroku create your-app-name
git push heroku main
🌍 Multi-Language Support (Future Enhancement)
To add regional language support:

Frontend: Use next-i18next for internationalization
Backend: Add language field to user profile
Data: Translate internship descriptions
UI: Add language selector component

Example implementation:
typescript// utils/i18n.ts
import { useTranslation } from 'next-i18next';

export const useI18n = () => {
  const { t, i18n } = useTranslation();
  return { t, changeLanguage: i18n.changeLanguage };
};
🔧 Environment Variables
Frontend (.env.local)
bashNEXT_PUBLIC_API_URL=http://localhost:8000
Backend (.env)
bashAPI_HOST=0.0.0.0
API_PORT=8000
CORS_ORIGINS=http://localhost:3000,http://127.0.0.1:3000
🧪 Testing
Backend Tests
bashcd backend
pip install pytest pytest-asyncio
pytest
Frontend Tests
bashcd frontend
npm install --save-dev @testing-library/react @testing-library/jest-dom jest
npm test
🐛 Troubleshooting
Common Issues
Backend won't start:

Check if Python virtual environment is activated
Verify all dependencies are installed: pip list
Check if port 8000 is available

Frontend can't connect to backend:

Ensure backend is running on port 8000
Check CORS settings in app/main.py
Verify NEXT_PUBLIC_API_URL environment variable

No recommendations returned:

Check backend logs for errors
Verify CSV data is loaded properly
Ensure at least one skill and sector is provided

Module import errors:

Check Python path: python -c "import sys; print(sys.path)"
Verify virtual environment: which python

Debug Mode
Backend Debug:
bash# Add to run.py
uvicorn.run(app, host="0.0.0.0", port=8000, reload=True, log_level="debug")
Frontend Debug:
bash# Add to next.config.js
module.exports = {
  reactStrictMode: true,
  logging: {
    fetches: {
      fullUrl: true,
    },
  },
}
📈 Performance Optimization
Backend Optimizations

Caching: Implement Redis for frequent queries
Database: Move from CSV to PostgreSQL/MongoDB
Async Processing: Use background tasks for heavy ML operations
Load Balancing: Use multiple server instances

Frontend Optimizations

Code Splitting: Implement dynamic imports
Image Optimization: Use Next.js Image component
Caching: Implement SWR or React Query
Bundle Analysis: Use @next/bundle-analyzer

🤝 Contributing

Fork the repository
Create feature branch: `git checkout -b feature/

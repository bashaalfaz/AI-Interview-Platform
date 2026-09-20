AI Interview Preparation Platform
An AI-powered full-stack interview and resume preparation platform that
analyzes a candidate's resume/profile against a target job description
and generates a personalized interview strategy, including technical
questions, behavioral questions, skill-gap analysis, preparation
roadmap, and an ATS-friendly tailored resume.

Overview
The platform helps candidates prepare for interviews by combining:

Resume and candidate-profile analysis

Job description matching

AI-generated technical interview questions

AI-generated behavioral interview questions

Skill-gap identification

Day-wise interview preparation roadmap

AI-powered ATS-friendly resume generation

Downloadable PDF resumes

Persistent interview reports and history

Secure user authentication

The application uses React.js for the frontend, Node.js +
Express.js for the backend, MongoDB for persistence, and Google
Gemini for AI-powered analysis and content generation.

Key Features
1. AI-Powered Resume & Job Matching
Accepts a target job description.

Accepts a candidate resume/profile.

Uses Google Gemini to analyze the candidate against the job
requirements.

Generates a match score from 0--100.

Identifies skills that may require additional preparation.

2. Personalized Technical Questions
Generates technical interview questions based on the candidate profile
and target role.

Each question includes: - Interview question - Interviewer's intention -
Model answer / key points to cover

3. Behavioral Interview Preparation
Generates personalized behavioral questions with: - Question -
Interviewer's intention - Suggested answer strategy

4. Skill-Gap Analysis
The AI identifies missing or weak skills and assigns a severity level:

low

medium

high

This allows candidates to prioritize preparation based on the
requirements of the target role.

5. Day-Wise Preparation Roadmap
Generates a structured preparation plan containing:

Day number

Focus area

Specific preparation tasks

The roadmap can cover topics such as technical concepts, role-specific
preparation, system design, behavioral preparation, and mock interviews
depending on the target job.

6. ATS-Friendly Resume Generation
The platform can generate a job-tailored resume using:

Existing resume content

Candidate self-description

Target job description

The generated HTML resume is converted into a downloadable A4 PDF
using Puppeteer.

The AI prompt specifically targets: - ATS-friendly structure - Relevant
skills and experience - Professional formatting - Concise 1--2 page
output - Job-specific customization

7. Authentication & User Accounts
Includes: - User registration - Login/logout - JWT authentication -
HTTP-only cookie-based token transport - Password hashing using bcrypt -
JWT token blacklisting during logout - Protected interview-report routes

8. Interview Report History
Generated reports are stored in MongoDB and can be retrieved later.

Users can access: - Previous interview plans - Match scores - Technical
questions - Behavioral questions - Skill gaps - Preparation roadmap -
Generated resume PDF

Performance / Project Metrics
The project achieved the following reported evaluation results:

Metric Result

Candidate--Job Matching Accuracy 94%
Interview Evaluation Accuracy 90%

These metrics are based on the project's evaluation described in the
resume.

Tech Stack
Frontend
React.js

React Router

Axios

Sass

Vite

JavaScript

Backend
Node.js

Express.js

MongoDB

Mongoose

JWT

bcryptjs

Multer

Zod

Puppeteer

pdf-parse

AI / Generative AI
Google Gemini

Structured JSON generation

Zod schemas

zod-to-json-schema

Development Tools
Git

GitHub

VS Code

npm

System Architecture
                    ┌──────────────────────┐
                    │      React.js        │
                    │      Frontend        │
                    └──────────┬───────────┘
                               │
                         REST API / Axios
                               │
                    ┌──────────▼───────────┐
                    │    Node.js +         │
                    │     Express.js       │
                    └───────┬───────┬──────┘
                            │       │
             ┌──────────────┘       └────────────────┐
             │                                       │
     ┌───────▼────────┐                    ┌─────────▼─────────┐
     │    MongoDB     │                    │   Google Gemini   │
     │    + Mongoose  │                    │    AI Analysis    │
     └────────────────┘                    └─────────┬─────────┘
                                                     │
                                          ┌──────────▼──────────┐
                                          │ Interview Strategy  │
                                          │ Questions / Gaps /  │
                                          │ Roadmap / Resume    │
                                          └──────────┬──────────┘
                                                     │
                                             ┌───────▼───────┐
                                             │   Puppeteer   │
                                             │  HTML → PDF   │
                                             └───────────────┘
Project Structure
AI-Interview-Preparation-Platform/
│
├── Backend/
│   ├── src/
│   │   ├── config/
│   │   │   └── database.js
│   │   ├── controllers/
│   │   │   ├── auth.controller.js
│   │   │   └── interview.controller.js
│   │   ├── middlewares/
│   │   │   ├── auth.middleware.js
│   │   │   └── file.middleware.js
│   │   ├── models/
│   │   │   ├── blacklist.model.js
│   │   │   ├── interviewReport.model.js
│   │   │   └── user.model.js
│   │   ├── routes/
│   │   │   ├── auth.routes.js
│   │   │   └── interview.routes.js
│   │   ├── services/
│   │   │   └── ai.service.js
│   │   └── app.js
│   ├── server.js
│   └── package.json
│
└── Frontend/
    ├── src/
    │   ├── features/
    │   │   ├── auth/
    │   │   └── interview/
    │   ├── App.jsx
    │   ├── app.routes.jsx
    │   └── main.jsx
    ├── package.json
    └── vite.config.js
Data Flow
Interview Strategy Generation
Resume / Self Description
          +
    Job Description
          │
          ▼
    React Frontend
          │
          ▼
    Express API
          │
          ▼
    PDF Text Extraction
       (pdf-parse)
          │
          ▼
    Google Gemini
          │
          ▼
 Structured Interview Report
          │
    ┌─────┼──────────┬────────────┐
    ▼     ▼          ▼            ▼
 Match  Technical  Behavioral   Skill Gaps
 Score  Questions   Questions
          │
          ▼
    Preparation Roadmap
          │
          ▼
       MongoDB
Tailored Resume Generation
Stored Candidate Profile
          +
    Job Description
          │
          ▼
    Google Gemini
          │
          ▼
   Structured HTML Resume
          │
          ▼
      Puppeteer
          │
          ▼
    Downloadable PDF
API Endpoints
Authentication
Method Endpoint Description

POST /api/auth/register Register a new user
POST /api/auth/login Login user
GET /api/auth/logout Logout and blacklist token
GET /api/auth/get-me Get authenticated user

Interview
Method Endpoint Description

POST /api/interview/ Generate personalized
interview report

GET /api/interview/ Get user's
interview-report
history

GET /api/interview/report/:interviewId Get a specific
interview report

Installation
Prerequisites
Make sure you have installed:

Node.js

npm

MongoDB or a MongoDB Atlas database

Google Gemini API key

1. Clone the repository
git clone <your-repository-url>
cd AI-Interview-Preparation-Platform
2. Install backend dependencies
cd Backend
npm install
3. Configure backend environment variables
Create a .env file inside the Backend directory:

MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
GOOGLE_GENAI_API_KEY=your_google_gemini_api_key
4. Start the backend
npm run dev
The backend runs on:

http://localhost:3000
5. Install frontend dependencies
Open another terminal:

cd Frontend
npm install
6. Start the frontend
npm run dev
The frontend runs on the Vite development server, typically:

http://localhost:5173
Environment Variables
Variable Description

MONGO_URI MongoDB connection string
JWT_SECRET Secret used to sign JWT tokens
GOOGLE_GENAI_API_KEY Google Gemini API key

Never commit your .env file or API keys to GitHub.

Authentication Flow
User registers with username, email, and password.

Password is hashed using bcryptjs.

Server generates a JWT.

JWT is stored in a cookie.

Protected routes validate the cookie token.

Logout stores the token in a blacklist and clears the cookie.

Protected interview reports are associated with the authenticated
user's MongoDB ID.

AI Output Structure
The interview report is generated as structured JSON using a Zod schema.

Interview Report
│
├── title
├── matchScore
├── technicalQuestions[]
│   ├── question
│   ├── intention
│   └── answer
│
├── behavioralQuestions[]
│   ├── question
│   ├── intention
│   └── answer
│
├── skillGaps[]
│   ├── skill
│   └── severity
│
└── preparationPlan[]
    ├── day
    ├── focus
    └── tasks[]
Using structured AI output makes the generated data predictable and
easier for the frontend to render.

Frontend Experience
The application provides a dedicated interface for:

Creating an interview plan

Uploading a resume

Adding a self-description

Reviewing match scores

Expanding technical questions

Expanding behavioral questions

Viewing skill gaps

Following the preparation roadmap

Downloading an AI-generated resume

Security & Reliability
The project implements several backend security and reliability
mechanisms:

Password hashing with bcrypt

JWT-based authentication

Token blacklist on logout

Protected API routes

User-specific report access

Request validation with Zod for AI response structure

File-size limits through Multer

MongoDB persistence

Structured error/status responses

Current File Upload Note
The current backend extracts resume content using pdf-parse, so the
implemented resume-processing flow is designed around PDF resumes.
The frontend upload UI also displays DOCX as an option, but DOCX parsing
is not implemented in the current backend.

Future Improvements
Potential extensions include:

DOCX resume parsing

Resume section-level scoring

More detailed ATS keyword analysis

Interview simulation with voice input/output

Real-time AI interviewer

Coding-round generation and evaluation

Role-specific question banks

Mock interview performance tracking

Advanced analytics across interview sessions

Production deployment with environment-specific CORS configuration

Automated testing and CI/CD

Learning & Engineering Highlights
This project demonstrates practical experience with:

Full-stack JavaScript development

REST API design

React component architecture

JWT authentication

Password hashing

MongoDB schema design

AI API integration

Structured LLM outputs

Prompt engineering

Resume parsing

PDF generation

File uploads

Protected routes

Client-server state management

AI-driven personalization

Author
Sayyad Yusuff Basha
B.Tech Mechanical & Aerospace Engineering, IIT Hyderabad

Project Focus
Full-Stack Development · Generative AI · LLM Applications · Resume
Intelligence · Interview Automation

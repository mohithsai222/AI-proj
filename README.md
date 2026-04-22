# AI Interview Practice Tool

A full-stack application for practicing job interviews with AI using voice interaction. Built with React, Node.js, Express, MongoDB, Socket.IO, and Google Gemini AI.

![AI Interview Practice](https://img.shields.io/badge/AI-Interview-blue)
![React](https://img.shields.io/badge/React-18.2-61dafb)
![Node.js](https://img.shields.io/badge/Node.js-18+-green)
![MongoDB](https://img.shields.io/badge/MongoDB-7.0-green)

## 🎯 Features

- **Voice-Based Interviews**: Speak your answers and hear AI responses
- **Real-time Communication**: Socket.IO for instant AI responses
- **AI-Powered Questions**: Google Gemini generates contextual interview questions
- **User Authentication**: Signup/Login system
- **Interview Customization**: Choose position, experience level, and difficulty
- **Chat Transcript**: All interviews are saved to database

## 🛠️ Tech Stack

### Frontend
- React 18.2 + Vite
- React Router DOM
- Axios
- Socket.IO Client
- Web Speech API (for voice recognition)

### Backend
- Node.js + Express
- MongoDB + Mongoose
- Socket.IO
- Google Generative AI (Gemini)
- CORS

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

1. **Node.js** (v18 or higher)
   - Download: https://nodejs.org/

2. **MongoDB** 
   - **Option A (Recommended for Beginners)**: MongoDB Atlas (Cloud)
     - Sign up: https://www.mongodb.com/cloud/atlas
     - Create a free cluster
   - **Option B**: MongoDB Community Edition (Local)
     - Download: https://www.mongodb.com/try/download/community

3. **Google Gemini API Key**
   - Get your free API key: https://makersuite.google.com/app/apikey
   - Click "Create API Key"

4. **Code Editor** (Recommended)
   - VS Code: https://code.visualstudio.com/

## 🚀 Installation & Setup

### Step 1: Extract the ZIP file
```bash
# Extract ai-interview-app.zip to your desired location
# Navigate to the extracted folder
cd ai-interview-app
```

### Step 2: Setup Backend

```bash
# Navigate to backend folder
cd backend

# Install dependencies
npm install

# Configure environment variables
# Edit the .env file and add your credentials:
# - Replace "your_gemini_api_key_here" with your actual Gemini API key
# - If using MongoDB Atlas, replace MONGODB_URI with your connection string
```

**Example .env configuration:**
```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/ai-interview
# OR for MongoDB Atlas:
# MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/ai-interview

GEMINI_API_KEY=AIzaSyD...your_actual_key_here
```

### Step 3: Setup Frontend

```bash
# Open a new terminal
# Navigate to frontend folder
cd frontend

# Install dependencies
npm install
```

### Step 4: Start the Application

**Terminal 1 - Start MongoDB (if using local MongoDB):**
```bash
mongod
```

**Terminal 2 - Start Backend:**
```bash
cd backend
npm run dev
```

You should see:
```
✅ MongoDB Connected
🚀 Server running on port 5000
```

**Terminal 3 - Start Frontend:**
```bash
cd frontend
npm run dev
```

You should see:
```
  VITE v5.x.x  ready in xxx ms
  ➜  Local:   http://localhost:5173/
```

### Step 5: Access the Application

Open your browser and go to: **http://localhost:5173/**

## 📱 How to Use

1. **Sign Up**: Create a new account with your details
2. **Login**: Sign in with your credentials
3. **Dashboard**: Review interview settings (Position, Experience, Difficulty)
4. **Start Interview**: Click "Start Interview" button
5. **Allow Microphone**: Grant microphone permissions when prompted
6. **Speak**: Click the microphone button and speak your answer
7. **Listen**: AI will respond with questions via voice and text
8. **Stop**: Click "Stop Interview" when finished

## 🎤 Voice Recognition Tips

- **Best Browser**: Use Google Chrome for best voice recognition
- **Microphone**: Ensure your microphone is working properly
- **Permissions**: Allow microphone access when prompted
- **Speaking**: Speak clearly and wait for recording to stop before speaking
- **Internet**: Stable internet connection required for speech recognition

## 📁 Project Structure

```
ai-interview-app/
├── backend/
│   ├── models/
│   │   ├── User.js           # User schema
│   │   └── Interview.js      # Interview schema
│   ├── server.js             # Main server file
│   ├── package.json          # Backend dependencies
│   └── .env                  # Environment variables
│
├── frontend/
│   ├── src/
│   │   ├── pages/
│   │   │   ├── Login.jsx     # Login page
│   │   │   ├── Signup.jsx    # Signup page
│   │   │   ├── Dashboard.jsx # Dashboard page
│   │   │   └── Interview.jsx # Interview page
│   │   ├── App.jsx           # Main app component
│   │   ├── main.jsx          # Entry point
│   │   └── index.css         # Global styles
│   ├── index.html            # HTML template
│   ├── package.json          # Frontend dependencies
│   └── vite.config.js        # Vite configuration
│
└── README.md                 # This file
```

## 🔌 API Endpoints

### Authentication
- `POST /api/signup` - Create new user account
- `POST /api/login` - Login user
- `GET /api/user/:userId` - Get user details

### Interview
- `POST /api/interview/start` - Start new interview
- `POST /api/interview/stop/:interviewId` - Stop interview

### Socket.IO Events
- `join-interview` - Join interview room
- `user-message` - Send user message to AI
- `ai-response` - Receive AI response

## 🐛 Troubleshooting

### Issue: Port Already in Use
**Solution**: Change the PORT in `backend/.env` to 5001 or any available port

### Issue: MongoDB Connection Error
**Solution**: 
- Ensure MongoDB is running (if local)
- Check your connection string (if Atlas)
- Verify network connectivity

### Issue: Voice Recognition Not Working
**Solution**:
- Use Google Chrome browser
- Check microphone permissions in browser settings
- Ensure you're using HTTPS or localhost

### Issue: Gemini API Error
**Solution**:
- Verify your API key is correct in `.env`
- Check API key has proper permissions
- Ensure you haven't exceeded rate limits

### Issue: CORS Errors
**Solution**:
- Ensure backend server is running
- Check that frontend is calling `http://localhost:5000`
- Verify CORS settings in `server.js`

## 🔐 Security Notes

⚠️ **Important**: This is a beginner-friendly demo application. For production use, you should:

- Hash passwords using bcrypt
- Add JWT authentication
- Implement rate limiting
- Add input validation and sanitization
- Use environment-specific configurations
- Add HTTPS in production

## 🌟 Future Enhancements

- [ ] Password hashing with bcrypt
- [ ] JWT authentication
- [ ] Interview history and analytics
- [ ] Multiple interview types
- [ ] Feedback and scoring system
- [ ] Resume upload and analysis
- [ ] Email notifications
- [ ] Mobile app version

## 📝 Database Schema

### User Collection
```javascript
{
  firstName: String,
  lastName: String,
  email: String (unique),
  password: String,
  createdAt: Date,
  updatedAt: Date
}
```

### Interview Collection
```javascript
{
  userId: ObjectId (ref: User),
  position: String,
  experience: String,
  difficulty: String,
  isStart: Boolean,
  chatTranscript: [{
    role: String,
    message: String,
    timestamp: Date
  }],
  createdAt: Date,
  updatedAt: Date
}
```

## 🤝 Contributing

This is an educational project. Feel free to fork and modify for your learning!

## 📄 License

MIT License - Feel free to use this project for learning purposes.

## 👨‍💻 Support

If you encounter any issues:
1. Check the troubleshooting section above
2. Ensure all prerequisites are installed correctly
3. Verify environment variables are set properly
4. Check that all terminals show no errors

## 🎓 Learning Resources

- [React Documentation](https://react.dev/)
- [Node.js Documentation](https://nodejs.org/docs/)
- [MongoDB Documentation](https://docs.mongodb.com/)
- [Socket.IO Documentation](https://socket.io/docs/)
- [Google Gemini API](https://ai.google.dev/docs)

---

**Built with ❤️ for Interview Practice**

Happy Interviewing! 🚀

# Healthcare Chatbot

A modern, AI-powered healthcare assistant chatbot built with Next.js, FastAPI, and OpenAI. This application provides a beautiful, responsive interface for users to ask health-related questions and receive informative, empathetic responses from an AI assistant.

## ✨ Features

- 🤖 **AI-Powered Assistance**: Uses OpenAI GPT-3.5-turbo for intelligent, context-aware responses
- 💬 **Beautiful Chat Interface**: Modern, intuitive UI with smooth animations and transitions
- 🎨 **Responsive Design**: Works seamlessly on desktop, tablet, and mobile devices
- ⚡ **Fast & Efficient**: Optimized API calls and conversation history management
- 🔒 **Healthcare-Focused**: Specialized prompts with proper medical disclaimers
- 📝 **Auto-Resizing Input**: Textarea automatically adjusts to content
- 🎯 **Error Handling**: Comprehensive error handling with user-friendly messages
- 💾 **Conversation History**: Maintains context throughout the conversation

## 🛠️ Tech Stack

- **Frontend**: 
  - Next.js 14 (App Router)
  - React 18
  - TypeScript
  - Tailwind CSS
  - Axios for API calls

- **Backend**: 
  - FastAPI
  - Python 3.8+
  - OpenAI Python SDK
  - Pydantic for data validation

- **AI**: 
  - OpenAI GPT-3.5-turbo

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** 18+ and npm (or yarn)
- **Python** 3.8 or higher
- **OpenAI API Key** ([Get one here](https://platform.openai.com/api-keys))
- **pip** (Python package manager)

## 🚀 Setup Instructions

### Step 1: Clone or Navigate to the Project

```bash
cd /home/developer/Music/Chatbot
```

### Step 2: Install Frontend Dependencies

```bash
npm install
```

This will install all required Node.js packages including Next.js, React, TypeScript, and Tailwind CSS.

### Step 3: Install Backend Dependencies

```bash
pip install -r requirements.txt
```

Or if you prefer using a virtual environment (recommended):

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### Step 4: Configure Environment Variables

Create a `.env` file in the root directory:

```bash
cp env.example .env
```

Edit `.env` and add your OpenAI API key:

```env
OPENAI_API_KEY=sk-your-actual-openai-api-key-here
```

**⚠️ Important**: Never commit your `.env` file to version control. It's already in `.gitignore`.

### Step 5: Run the Backend Server

In your terminal, navigate to the project root and run:

```bash
cd backend
python main.py
```

Or from the root directory:

```bash
python backend/main.py
```

The FastAPI server will start on `http://localhost:8000`

You should see:
```
INFO:     Uvicorn running on http://0.0.0.0:8000
```

You can verify it's working by visiting:
- API Root: `http://localhost:8000/`
- Health Check: `http://localhost:8000/health`
- API Docs: `http://localhost:8000/docs` (FastAPI automatic documentation)

### Step 6: Run the Frontend Development Server

Open a **new terminal window** and run:

```bash
npm run dev
```

The Next.js app will start on `http://localhost:3000`

You should see:
```
✓ Ready in [time]
○ Local:        http://localhost:3000
```

## 🎯 Usage

1. **Open your browser** and navigate to `http://localhost:3000`
2. **Start chatting** with the healthcare assistant
3. **Ask health-related questions** such as:
   - "What are the symptoms of a common cold?"
   - "How can I improve my sleep quality?"
   - "What should I know about maintaining a healthy diet?"
   - "When should I see a doctor for a headache?"

4. **Features you can use**:
   - Press `Enter` to send a message
   - Press `Shift + Enter` for a new line
   - Click "Clear Chat" to start a new conversation
   - The chat maintains context throughout your conversation

## ⚠️ Important Medical Disclaimer

**This chatbot provides general health information and educational content only. It is NOT a replacement for professional medical advice, diagnosis, or treatment.**

- Always consult qualified healthcare providers for serious, persistent, or worsening symptoms
- For medical emergencies, call emergency services immediately
- Never delay seeking professional medical advice based on information from this chatbot
- The AI assistant is designed to provide general information and encourage professional consultation when appropriate

## 📁 Project Structure

```
Chatbot/
├── app/                      # Next.js app directory
│   ├── page.tsx             # Main chat interface component
│   ├── layout.tsx           # Root layout with metadata
│   └── globals.css          # Global styles and animations
├── backend/                  # FastAPI backend
│   ├── __init__.py          # Python package init
│   └── main.py              # FastAPI server and API endpoints
├── .env                      # Environment variables (create this)
├── env.example               # Environment variables template
├── package.json              # Frontend dependencies and scripts
├── requirements.txt         # Backend Python dependencies
├── tailwind.config.js       # Tailwind CSS configuration
├── tsconfig.json            # TypeScript configuration
├── next.config.js           # Next.js configuration
└── README.md                # This file
```

## 🔧 Development

### Running in Development Mode

**Terminal 1 - Backend:**
```bash
python backend/main.py
```

**Terminal 2 - Frontend:**
```bash
npm run dev
```

### Building for Production

**Frontend:**
```bash
npm run build
npm start
```

**Backend:**
The FastAPI server can be run with uvicorn directly:
```bash
uvicorn backend.main:app --host 0.0.0.0 --port 8000
```

Or with production settings:
```bash
uvicorn backend.main:app --host 0.0.0.0 --port 8000 --workers 4
```

## 🐛 Troubleshooting

### Backend Issues

- **Port 8000 already in use**: Change the port in `backend/main.py` or kill the process using port 8000
- **OpenAI API errors**: Verify your API key is correct and you have credits in your OpenAI account
- **Module not found errors**: Ensure all dependencies are installed with `pip install -r requirements.txt`

### Frontend Issues

- **Port 3000 already in use**: Next.js will automatically use the next available port
- **Cannot connect to backend**: Ensure the backend server is running on `http://localhost:8000`
- **Build errors**: Clear `.next` folder and `node_modules`, then reinstall: `rm -rf .next node_modules && npm install`

### CORS Issues

If you encounter CORS errors, ensure the backend CORS middleware includes your frontend URL in `allow_origins` in `backend/main.py`.

## 📝 API Endpoints

- `GET /` - API root endpoint
- `GET /health` - Health check endpoint
- `POST /api/chat` - Main chat endpoint
  - Request body:
    ```json
    {
      "message": "Your question here",
      "conversation_history": [
        {"role": "user", "content": "Previous message"},
        {"role": "assistant", "content": "Previous response"}
      ]
    }
    ```
  - Response:
    ```json
    {
      "response": "AI response text",
      "status": "success"
    }
    ```

## 🔐 Security Notes

- Never expose your OpenAI API key in client-side code
- Keep your `.env` file secure and never commit it to version control
- Consider implementing rate limiting for production use
- Add authentication/authorization for production deployments

## 📄 License

MIT License - feel free to use this project for learning and development.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📧 Support

For issues or questions, please open an issue on the repository.

---

**Built with ❤️ for better healthcare information access**


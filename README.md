# 🎯 Vapi Call Center

A modern AI-powered call center application built with **Vapi Voice Agents**, featuring real-time voice conversations and outbound calling capabilities.

![Vapi Call Center](https://img.shields.io/badge/Vapi-Voice%20AI-blue?style=for-the-badge)
![React](https://img.shields.io/badge/React-18.3.1-61DAFB?style=for-the-badge&logo=react)
![TypeScript](https://img.shields.io/badge/TypeScript-5.8.3-3178C6?style=for-the-badge&logo=typescript)
![Express](https://img.shields.io/badge/Express-5.1.0-000000?style=for-the-badge&logo=express)

## ✨ Features

- 🎙️ **Real-time Voice Conversations** - Natural AI voice interactions using Vapi Web SDK
- 📞 **Outbound Calling** - Secure server-side call initiation with phone keypad interface
- 💬 **Live Transcription** - Real-time conversation transcripts with deduplication
- 🎨 **Modern UI** - Beautiful interface built with shadcn/ui and Tailwind CSS
- 🔒 **Secure Backend** - Express.js server with proper API key management
- 📊 **Call Analytics** - Transcript forwarding to webhooks for analysis
- 🌐 **Full-Stack TypeScript** - End-to-end type safety

## 🚀 Quick Start

### Prerequisites

Before running this application, ensure you have:

- **Node.js 18+** and **npm** installed
- A **Vapi account** with the following credentials:
  - Public Web API Key
  - Server (private) API Key  
  - Assistant ID
  - Phone Number ID (for outbound calls)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/khaleed-m/vapi-call-center.git
   cd vapi-call-center
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment Setup**
   
   Create a `.env` file in the project root:
   ```env
   # Backend (private - NEVER expose in client)
   VAPI_API_KEY=your_private_server_token
   PORT=3001

   # Frontend (public - safe to expose in browser)
   VITE_VAPI_PUBLIC_API_KEY=your_public_web_api_key
   VITE_ASSISTANT_ID=your_assistant_id
   VITE_DEFAULT_PHONE_NUMBER_ID=your_phone_number_id

   # Optional: Webhook for transcript forwarding
   N8N_WEBHOOK_URL=your_webhook_url
   ```

4. **Start the application**
   ```bash
   npm run dev
   ```

   The application will be available at:
   - **Frontend**: http://localhost:8080
   - **Backend**: http://localhost:3001

## 🏗️ Project Structure

```
vapi-call-center/
├── 📁 public/                 # Static assets
├── 📁 server/                 # Express.js backend
│   └── index.ts              # Main server file with Vapi integration
├── 📁 src/                   # React frontend source
│   ├── 📁 components/        # Reusable UI components
│   │   ├── 📁 ui/           # shadcn/ui components
│   │   └── 📁 voice/        # Voice-specific components
│   │       ├── VoiceAgent.tsx        # Main voice interface
│   │       └── OutboundCallForm.tsx  # Outbound calling form
│   ├── 📁 pages/            # Application pages
│   │   └── Index.tsx        # Main application page
│   └── 📁 lib/              # Utility functions
├── .env.example             # Environment variables template
├── package.json             # Project dependencies and scripts
└── README.md               # This file
```

## 🔧 Available Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Start both client and server in development mode |
| `npm run dev:client` | Start only the Vite frontend server |
| `npm run dev:server` | Start only the Express backend server |
| `npm run build` | Build the frontend for production |
| `npm run build:server` | Compile TypeScript server code |
| `npm run start:server` | Run the compiled server |

## 🌐 API Endpoints

### Health Check
- **GET** `/api/health` - Server status check

### Outbound Calling
- **POST** `/api/vapi/outbound-call`
  ```json
  {
    "phoneNumberId": "string",
    "assistantId": "string", 
    "customer": {
      "number": "string",
      "name": "string (optional)"
    }
  }
  ```

- **POST** `/api/vapi/outbound-campaign`
  ```json
  {
    "name": "string",
    "phoneNumberId": "string",
    "assistantId": "string",
    "customer": {
      "number": "string", 
      "name": "string (optional)"
    }
  }
  ```

### Transcript Forwarding
- **POST** `/api/transcripts` - Forward call transcripts to configured webhook

## 🔐 Environment Variables

### Backend Variables (Private)
| Variable | Description | Required |
|----------|-------------|----------|
| `VAPI_API_KEY` | Your Vapi server API key | ✅ |
| `PORT` | Server port (default: 3001) | ❌ |
| `N8N_WEBHOOK_URL` | Webhook URL for transcript forwarding | ❌ |

### Frontend Variables (Public)
| Variable | Description | Required |
|----------|-------------|----------|
| `VITE_VAPI_PUBLIC_API_KEY` | Your Vapi public web API key | ✅ |
| `VITE_ASSISTANT_ID` | Your Vapi assistant ID | ✅ |
| `VITE_DEFAULT_PHONE_NUMBER_ID` | Default phone number for outbound calls | ✅ |

> ⚠️ **Security Note**: Never put your private `VAPI_API_KEY` in any `VITE_` variable as it will be exposed in the browser bundle.

## 🎨 Key Components

### VoiceAgent Component
- Handles real-time voice conversations using Vapi Web SDK
- Manages call states (connected, speaking, listening)
- Displays live transcription with role-based messaging
- Animated voice visualizations and call status indicators

### OutboundCallForm Component  
- Phone keypad interface for entering destination numbers
- Input validation and E.164 phone number formatting
- Integration with backend API for secure call initiation

### Backend Server
- Express.js server with CORS and security middleware
- Vapi Server SDK integration for outbound calling
- Phone number validation and normalization
- Webhook integration for transcript forwarding

## 🔄 Development Workflow

1. **Development Mode**: Run `npm run dev` to start both frontend and backend with hot reload
2. **API Proxy**: Vite proxies `/api/*` requests to the Express server to avoid CORS issues
3. **Environment**: Restart the dev server after modifying `.env` variables
4. **Type Safety**: Full TypeScript support across frontend and backend

## 🚀 Deployment

### Frontend (Vite Build)
```bash
npm run build
# Deploy the 'dist' folder to your static hosting service
```

### Backend (Node.js)
```bash
npm run build:server
npm run start:server
# Deploy to your Node.js hosting service
```

## 🛠️ Tech Stack

- **Frontend**: React 18, TypeScript, Vite, Tailwind CSS, shadcn/ui
- **Backend**: Express.js, TypeScript, Vapi Server SDK
- **Voice AI**: Vapi Web SDK for real-time voice interactions
- **Validation**: Zod for runtime type checking
- **Development**: Concurrently for running multiple processes

## 📝 Getting Vapi Credentials

1. Sign up at [Vapi.ai](https://vapi.ai)
2. Create a new assistant in the Vapi dashboard
3. Get your API keys from the settings:
   - **Public Key**: For frontend voice interactions
   - **Private Key**: For backend server operations
4. Configure a phone number for outbound calling
5. Note down your Assistant ID and Phone Number ID

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [Vapi.ai](https://vapi.ai) for the amazing voice AI platform
- [shadcn/ui](https://ui.shadcn.com/) for the beautiful UI components
- [Tailwind CSS](https://tailwindcss.com/) for the utility-first CSS framework

---

**Built with ❤️ by [Khaleed M](https://github.com/khaleed-m)**
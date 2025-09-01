# Google Calendar Telegram Bot - n8n Workflow

An intelligent scheduling assistant that manages your Google Calendar through natural conversation via Telegram, powered by AI and n8n automation.

## 🤖 What It Does

**PlanMaster** is an AI-powered Telegram bot that acts as your personal scheduling assistant. Simply chat with it naturally to:

- 📅 **Schedule events** - "Book a team meeting tomorrow at 2pm"
- 🔍 **Check availability** - "What's on my calendar today?"
- ✏️ **Update events** - "Move my 3pm call to 4pm"
- 🗑️ **Delete events** - "Cancel my lunch meeting"
- 🎤 **Voice commands** - Send voice messages for hands-free scheduling
- 🤝 **Conflict resolution** - Automatically detects overlaps and suggests alternatives

## 🚀 Key Features

### Multi-Modal Input
- **Text messages**: Type your scheduling requests naturally
- **Voice messages**: Speak your requests and get automatic transcription via Google Gemini

### Smart Calendar Management
- **Conflict detection**: Automatically checks for scheduling conflicts
- **Intelligent suggestions**: Proposes alternative times when conflicts exist
- **Comprehensive CRUD operations**: Create, read, update, and delete calendar events
- **Timezone awareness**: Handles timezone conversions (default: Europe/Amsterdam)

### Conversational AI
- **Natural language processing**: Understands casual scheduling requests
- **Context memory**: Remembers conversation history for seamless interactions
- **Confirmation workflow**: Always confirms before making calendar changes
- **Smart defaults**: 1-hour duration, proper formatting, and more

## 🏗️ Architecture

This n8n workflow consists of several interconnected nodes:

### Core Components
- **Telegram Trigger**: Listens for incoming messages and voice notes
- **AI Agent**: Google Gemini-powered conversational AI with calendar management capabilities
- **Voice Processing**: Automatic transcription using Google Gemini for voice messages
- **Memory System**: Maintains conversation context per user

### Calendar Integration
- **MCP (Model Context Protocol)**: Advanced calendar tool integration
- **Google Calendar Tools**: Direct API integration for calendar operations
  - Create events
  - Get events (single/multiple)
  - Update events
  - Delete events

### Smart Routing
- **Message Type Detection**: Automatically routes text vs. voice messages
- **Input Processing**: Normalizes different input types for the AI agent

## 📋 Prerequisites

### Required Accounts & APIs
1. **n8n Cloud or Self-hosted instance**
2. **Telegram Bot Token**
   - Create a bot via [@BotFather](https://t.me/botfather)
   - Get your bot token
3. **Google Calendar API**
   - OAuth2 credentials for calendar access
4. **Google Gemini API**
   - For AI processing and voice transcription

### Required Credentials in n8n
- **Telegram API**: Create a credential with your Telegram bot token
- **Google Calendar OAuth2**: Create a credential with your Google Calendar OAuth2 access
- **Google Gemini API**: Create a credential with your Google Gemini API key

## 🛠️ Setup Instructions

### 1. Import the Workflow
- Download the `Google_Calendar_Telegram.json` file
- Import it into your n8n instance
- Activate the workflow

### 2. Configure Credentials
Set up the following credentials in n8n:
- **Telegram API**: Add your bot token
- **Google Calendar OAuth2**: Authorize calendar access
- **Google Gemini API**: Add your API key

### 3. Update Calendar Settings
- **IMPORTANT**: Replace the calendar email in ALL Google Calendar nodes with YOUR email address
- Navigate to each Google Calendar node in the workflow
- Update the calendar field to your primary Google Calendar email
- This ensures the bot manages YOUR calendar, not the example one

### 4. MCP Server Configuration
- **SECURITY NOTE**: The workflow includes an MCP server endpoint that you must replace
- Update the MCP Client Tool node with YOUR own MCP server endpoint
- **Do NOT use the example endpoint** - set up your own MCP server for security
- Refer to n8n MCP documentation for server setup instructions

## 💬 Usage Examples

### Basic Scheduling
```
"Schedule a dentist appointment tomorrow at 10am"
"Book lunch with Sarah on Friday at noon"
"Set up a team standup every Monday at 9am"
```

### Checking Calendar
```
"What's on my calendar today?"
"Show me my meetings tomorrow"
"Do I have anything at 3pm?"
```

### Modifications
```
"Move my 2pm meeting to 3pm"
"Cancel my lunch appointment"
"Update the client call to include video link"
```

### Voice Commands
Simply send a voice message with any of the above requests for hands-free operation.

## 🎯 Workflow Logic

1. **Message Reception**: Telegram trigger captures incoming messages
2. **Input Routing**: Switch node determines if it's text or voice
3. **Voice Processing**: If voice, download → transcribe → normalize
4. **AI Processing**: Gemini agent processes the request with calendar context
5. **Calendar Operations**: Executes appropriate calendar actions via MCP/API
6. **Response**: Sends formatted response back to Telegram

## 🔧 Customization Options

### Timezone Configuration
- Default timezone: `Europe/Amsterdam`
- Modify in the AI Agent system message

### Response Language
- Currently configured for English
- Modify the AI Agent prompt for other languages

### Default Event Duration
- Currently: 1 hour
- Adjustable in the AI Agent system message

### Calendar Selection
- **REQUIRED**: Update ALL calendar email addresses in Google Calendar nodes to YOUR email
- Review each Google Calendar node in the workflow
- Replace any hardcoded email addresses with your own
- Can be extended to support multiple calendars

## 🤝 Contributing

This workflow can be extended with:
- Multiple calendar support
- Integration with other messaging platforms
- Advanced recurring event patterns
- Meeting room booking
- Attendee management
- Email notifications

## 📝 License

This project is provided as-is for educational and personal use.

## ⚠️ Important Security Notes

- **CRITICAL**: Replace ALL email addresses and endpoints with your own before use
- Always test in a non-production environment first
- **Never share** your API keys, credentials, or workflow files publicly
- Review all nodes for hardcoded personal information before deployment
- Ensure proper security for API keys and credentials
- The workflow requires active n8n instance to function
- Voice transcription requires Google Gemini API quota
- **Set up your own MCP server** - do not use example endpoints in production

---

**Built with ❤️ using n8n, Google Gemini, and Telegram**
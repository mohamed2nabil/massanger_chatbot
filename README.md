# 🤖 Facebook Messenger AI Chatbot

An intelligent chatbot for Facebook Messenger built with n8n workflow automation and powered by Google Gemini AI. This chatbot provides natural, context-aware conversations with message history support.

## ✨ Features

- **AI-Powered Responses**: Uses Google Gemini Chat Model for intelligent, human-like conversations
- **Conversation Memory**: Maintains context across messages using Simple Memory storage
- **Webhook Integration**: Real-time message processing through Facebook Messenger webhooks
- **Automated Workflow**: Built entirely on n8n for easy maintenance and scalability
- **Field Editing**: Custom message processing and formatting before AI response
- **Production Ready**: Configured for production deployment with proper error handling

## 🏗️ Architecture

The chatbot follows this workflow:

1. **Webhook** → Receives incoming messages from Facebook Messenger
2. **Edit Fields** → Processes and formats the incoming data
3. **AI Agent** → Generates intelligent responses using:
   - **Google Gemini Chat Model** → Main AI engine
   - **Simple Memory** → Stores conversation history
4. **HTTP Request** → Sends the response back to Messenger
5. **Respond to Webhook** → Confirms message receipt to Facebook

## 🚀 Quick Start

### Prerequisites

- n8n instance (self-hosted or cloud)
- Facebook Developer Account
- Facebook Page
- Google Cloud Account (for Gemini API)

### Setup Instructions

#### 1. Facebook Messenger Setup

1. Create a Facebook App at [developers.facebook.com](https://developers.facebook.com)
2. Add Messenger product to your app
3. Generate a Page Access Token
4. Set up webhook with your n8n webhook URL:
   ```
   https://your-domain.com/webhook/fb-chat
   ```
5. Subscribe to webhook events: `messages`, `messaging_postbacks`

#### 2. n8n Workflow Configuration

1. Import the workflow into your n8n instance
2. Configure the **Webhook** node:
   - Set path to `/fb-chat`
   - Enable production mode
3. Configure **Google Gemini Chat Model**:
   - Add your Google Cloud API credentials
   - Select your preferred model (e.g., gemini-pro)
4. Configure **HTTP Request** node:
   - Add Facebook Page Access Token
   - Set Messenger Send API endpoint

#### 3. Activate Workflow

1. Ensure workflow is set to **Active**
2. Execute the workflow once to initialize production webhook
3. Test by sending a message to your Facebook Page

## ⚙️ Configuration

### Environment Variables

Configure these in your n8n settings or workflow:

```bash
FACEBOOK_PAGE_ACCESS_TOKEN=your_token_here
GOOGLE_GEMINI_API_KEY=your_api_key_here
WEBHOOK_URL=https://your-domain.com/webhook/fb-chat
```

### Workflow Settings

- **Execution Order**: v1 (recommended)
- **Timezone**: Set to your local timezone (e.g., Africa/Cairo)
- **Save Executions**: Default - Save
- **Error Handling**: Stop Workflow on error

## 📝 Usage

Once configured, users can interact with the bot by:

1. Sending messages to your Facebook Page
2. The bot responds automatically with AI-generated replies
3. Conversation context is maintained across messages

### Example Conversation

```
User: مرحبا
Bot: مرحباً! كيف يمكنني مساعدتك اليوم؟

User: ما هي خدماتكم؟
Bot: [AI-generated response based on your configuration]
```

## 🛠️ Customization

### Modify AI Behavior

Edit the **AI Agent** node to customize:
- System prompts
- Response style
- Context length
- Temperature settings

### Add Custom Logic

Insert additional nodes between workflow steps to:
- Filter messages
- Add custom validation
- Integrate with other services
- Store data in databases

## 📊 Monitoring

Access execution logs in n8n:

1. Navigate to **Executions** tab
2. View successful and failed runs
3. Debug issues with detailed execution data

## 🐛 Troubleshooting

### Webhook Not Receiving Messages

- Verify webhook URL is accessible publicly
- Check Facebook webhook verification
- Ensure workflow is **Active**
- Confirm webhook is in **Production mode** (not test mode)

### AI Not Responding

- Check Google Gemini API credentials
- Verify API quota limits
- Review execution logs for errors

### Messages Not Sending

- Verify Facebook Page Access Token
- Check token permissions
- Ensure HTTP Request node configuration

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## 📄 License

This project is licensed under the MIT License.

## 👨‍💻 Author

**Mohamed Nabil**
- GitHub: [@mohamed2nabil](https://github.com/mohamed2nabil)

## 🙏 Acknowledgments

- Built with [n8n](https://n8n.io)
- Powered by [Google Gemini AI](https://deepmind.google/technologies/gemini/)
- Facebook Messenger Platform

---

⭐ If you find this project useful, please consider giving it a star on GitHub!

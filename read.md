
---

## Main Workflow (`My-workflow-19.json`)

- **Trigger**: Telegram bot receives a message.  
- **AI Agent**: Uses Gemini through OpenRouter to manage the conversation.  
- **Logic**: Collects user data in a strict order:  
  - Email → Name → Country → Phone → Date/Time → Topic  
- **Integrations**:  
  - Google Calendar (read/create/delete events with conflict checks)  
  - Google Sheets (store/update user info)  
  - Zoom (create meeting links)  
  - Gmail (send confirmation emails)  
- **Flow**: Once all details are collected, the workflow creates the appointment, updates records, sends an email, and replies back in Telegram with a confirmation.  

---

## Sub-Workflow (`TG-2-Email-Sender.json`)

- Triggered by the main workflow.  
- Takes inputs (`emailAddress`, `subject`, `body`).  
- Sends the email using Gmail credentials.  
- Keeps responsibilities separated for cleaner design.  

### Import workflows into n8n:

Go to Workflows → Import from File.
Upload both JSON files.

### Create and connect the required credentials in n8n:

Google Calendar OAuth2

Google Sheets OAuth2

Gmail OAuth2

Zoom OAuth2

Telegram Bot API key

Gemini (Google AI API key via OpenRouter or Vertex)

Replace placeholder IDs (sheet ID, calendar ID, etc.) with your own.

Activate both workflows.


### possible Upgrades

Add WhatsApp(actually I first tried to make this with whatsapp but ran out out api credits in testing :) ) 

Enable voice input and transcription for more natural interaction.

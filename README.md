# Captain Tugzy - Discord AI Chatbot

Captain Tugzy is an interactive, pirate-themed AI chatbot built with Python. Powered by the high-speed Llama-3.1-8b model via the Groq API, it operates directly inside Discord servers and direct messages.

---

## 🛠️ Discord Developer Portal Configuration

To invite the bot and configure its permissions:

1. Visit the [Discord Developer Portal](https://discord.com/developers/applications).
2. Click **New Application** and name it `Captain Tugzy`.
3. Go to the **Bot** tab on the left sidebar.
4. Locate the **Privileged Gateway Intents** section and toggle **ON**:
   - **Message Content Intent** (Required to process mentions/messages)
5. Generate and save the **Token** using the Reset Token button. This value will serve as your `DISCORD_TOKEN`.
6. Go to the **OAuth2** tab, select **URL Generator**, and check the following scopes and permissions:
   - **Scopes**: `bot`
   - **Bot Permissions**: 
     - `Read Messages/View Channels`
     - `Send Messages`
     - `Read Message History`
     - `Add Reactions`
7. Copy the generated authorization link and paste it into your browser to invite the bot to your desired Discord servers.

---

## 🔑 Groq API Key Setup

1. Sign up/Log in to the [Groq Console](https://console.groq.com/).
2. Navigate to the **API Keys** section.
3. Generate a new API Key and save it safely. This value will serve as your `GROQ_API_KEY`.

---

## 🚀 Deployment to Render

This repository contains all configuration elements necessary for direct deployment to Render.

### Option 1: Blueprint Deployment (Fastest)
1. Commit these files into a private or public GitHub/GitLab repository.
2. In your Render Dashboard, click **New +** and select **Blueprint**.
3. Select your repository. Render will automatically read the `render.yaml` file and configure the service.
4. Input your `DISCORD_TOKEN` and `GROQ_API_KEY` under the prompted environment variables when configuring the blueprint.

### Option 2: Manual Web Service Deployment
1. Create a **New +** -> **Web Service** on Render.
2. Connect your Git repository.
3. Configure the following options:
   - **Runtime**: `Python`
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `python app.py`
4. Expand the **Advanced** section and add the following Environment Variables:
   - `DISCORD_TOKEN`: (Your Discord Bot token)
   - `GROQ_API_KEY`: (Your Groq API key)
   - `PORT`: `8080` (Standard port binding)
5. Click **Deploy Web Service**.

*Note: Since free tier web services on Render go to sleep after 15 minutes of inactivity, you can use a free pinging service (like UptimeRobot) targeting your Render app URL to keep the bot active constantly.*

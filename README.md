# 🤖 linkedin-multiagent-autoposter

An end-to-end **LinkedIn post automation pipeline** built with a multi-agent architecture. Submit a form, and the system autonomously generates a post description, image prompt, title, and cover image — then publishes it to LinkedIn and sends a Slack notification.

---

## 🧠 Architecture Overview

```
Form Submission
     │
     ▼
Description Generator Agent  ←──  Google Gemini Chat Model
     │                        ←──  Search in Tavily (web research)
     ▼
Image Prompt Generator Agent
     │
     ▼
Generate Title Agent
     │
     ▼
Image Generation (AI Image)
     │
     ▼
Create a Post (LinkedIn)
     │
     ▼
Send a Message (Slack)
```

---

## ⚙️ Agents & Components

| Node | Role |
|------|------|
| **On Form Submission** | Trigger — kicks off the pipeline when a form is submitted |
| **Description Generator Agent** | Uses Google Gemini + Tavily search to craft a compelling LinkedIn post description |
| **Image Prompt Generator Agent** | Transforms the description into an optimized AI image generation prompt |
| **Generate Title Agent** | Creates an attention-grabbing headline for the post |
| **Image** | Generates a cover image based on the image prompt |
| **Create a Post** | Publishes the full post (title + description + image) to LinkedIn |
| **Send a Message** | Sends a Slack notification confirming the post was published |

---

## 🔧 Tools & Integrations

- **Google Gemini Chat Model** — LLM powering the description and content generation agents
- **Tavily Search** — Real-time web search for grounding the description in current, relevant content
- **LinkedIn API** — Auto-publishing generated posts
- **Slack API** — Post-publish notifications

---

## 🚀 Getting Started

### Prerequisites

- Access to an n8n (or compatible) workflow automation platform
- API keys for:
  - Google Gemini
  - Tavily
  - LinkedIn
  - Slack

### Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/linkedin-multiagent-autoposter.git
   cd linkedin-multiagent-autoposter
   ```

2. **Import the workflow** into your n8n instance via the Editor.

3. **Configure credentials** for each integration node:
   - Google Gemini Chat Model
   - Tavily (Search in Tavily)
   - LinkedIn (Create a Post)
   - Slack (Send a Message)

4. **Activate the workflow** and submit a test form to validate the pipeline.

---

## 📋 How It Works

1. A user fills out a form (topic, keywords, or raw content idea).
2. The **Description Generator Agent** researches the topic using Tavily and writes a LinkedIn-optimized post body with Gemini.
3. The **Image Prompt Generator Agent** translates the description into a visual prompt.
4. The **Generate Title Agent** creates a punchy, engagement-focused headline.
5. An **AI image** is generated from the prompt.
6. The full post is **published to LinkedIn** automatically.
7. A **Slack message** is sent to confirm the successful post.

---

## 📁 Repository Structure

```
linkedin-multiagent-autoposter/
├── workflow/
│   └── linkedin_automation.json   # Exportable workflow definition
├── README.md
└── .env.example                   # Template for required environment variables
```

---

## 🤝 Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss what you'd like to change.

---

## 📄 License

[MIT](LICENSE)

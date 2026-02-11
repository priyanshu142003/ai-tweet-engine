# ai-tweet-engine
An AI-driven n8n workflow that writes and posts brand-consistent tweets on X automatically.
Love it — let’s make this README **clean, professional, and GitHub-star worthy** ⭐
You can copy-paste this directly into `README.md`.

I’ll assume the repo name is **`n8n-x-ai-influencer`** (you can rename it easily).

---

 n8n X AI Influencer

Automated, brand-consistent tweet generation and posting system for **X (Twitter)** powered by **n8n + LLMs (OpenRouter)**.

This project enables creators, solo founders, and builders to grow their presence on X without manually writing or scheduling tweets — while still preserving **voice, tone, and quality**.

---

 Features

* 🤖 AI-generated tweets using OpenRouter (GPT-4o, Claude, Mixtral, etc.)
* 🎯 Influencer profile support (niche, tone, style, inspiration)
* 🧠 Human-like tweet generation (hooks, clarity, personality)
* 📏 Strict 280-character enforcement with auto-regeneration
* 🔁 Retry logic for invalid tweets
* ⏰ Manual or scheduled execution (every 6 hours with randomness)
* 🔐 Secure X (Twitter) OAuth2 posting
* ⚙️ Fully unattended automation via n8n

---

 System Architecture

```
Manual / Cron Trigger
        ↓
Influencer Profile (Edit Fields)
        ↓
Prompt Builder (Code Node)
        ↓
OpenRouter LLM (HTTP Request)
        ↓
280 Char Validator (Code Node)
        ↓
Retry / Regenerate (IF Node)
        ↓
X (Twitter) API Post
```

---

 Use Case

* Solo creators who tweet daily
* Indie hackers & founders
* AI / tech influencers
* Automation enthusiasts
* Anyone who wants consistent X growth without manual effort

---

 Tech Stack

* **n8n** – Workflow automation
* **OpenRouter** – LLM gateway
* **JavaScript** – Validation & logic
* **X (Twitter) API v2** – Tweet publishing
* **OAuth2** – Secure authentication

---

 Prerequisites

Before you start, make sure you have:

* n8n (cloud or self-hosted)
* OpenRouter account + API key
* X (Twitter) Developer account
* X OAuth2 credentials (Client ID & Secret)

---

 Required Credentials

 OpenRouter API Key

Used for tweet generation.

* Provider: **HTTP Header Auth**
* Header Name:

  ```
  Authorization
  ```
* Header Value:

  ```
  Bearer YOUR_OPENROUTER_API_KEY
  ```

---

 X (Twitter) OAuth2

Used for posting tweets.

Scopes required:

```
tweet.read
tweet.write
users.read
offline.access
```

---

 Influencer Profile Example

Configured using **Edit Fields** node in n8n:

```json
{
  "niche": "AI & Automation",
  "tone": "Casual, confident",
  "style": "Short lines, strong hooks",
  "audience": "Founders & builders",
  "inspiration": "Naval Ravikant"
}
```

This profile is injected into the LLM prompt every time.

---

 Tweet Length Validation (280 chars)

The workflow automatically:

* Checks tweet length
* Rejects tweets > 280 characters
* Regenerates content until valid
* Posts only approved tweets

No manual intervention required.

---

Triggers

* ✅ Manual Trigger (testing)
* ✅ Cron Trigger (every 6 hours)
* 🎲 Optional random minute offset for human-like behavior

---

 Output

* Tweets are posted directly to your X account
* Fully compliant with character limits
* Brand-consistent over long periods

---

Testing

Recommended testing flow:

1. Use **Manual Trigger**
2. Run workflow step-by-step
3. Verify:

   * Prompt correctness
   * LLM output
   * Character validation
   * Successful tweet posting

---

 Common Issues & Fixes

| Issue              | Solution                   |
| ------------------ | -------------------------- |
| Tweet not posting  | Check OAuth scopes         |
| 401 Unauthorized   | Regenerate X token         |
| LLM not responding | Check OpenRouter credits   |
| Tweet too long     | Validation node auto-fixes |

---

Project Status

 Stable
 Actively improving
 Open for contributions

---

 Contributing

Contributions are welcome!

You can help by:

* Improving prompts
* Adding analytics
* Multi-account support
* Media (image) tweets
* Thread generation

---

  License

MIT License
Use it freely, modify it, ship it 🚀

---

  Support

If this repo helped you:

* Give it a  on GitHub
* Share it with builders
* Build something awesome on top of it


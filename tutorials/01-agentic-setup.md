# Setting up for agentic coding
We will use two different apps for coding:

1. an app from a major AI company that offers high usage limits on a subscription basis (e.g. ChatGPT or Claude), and
2. an app that lets you easily connect with an API-based AI inference provider

Instructions for setting these up follow.

## Set up a subscription-based app
The three biggest players in the frontier AI model landscape are Open AI, Anthropic, and Google. Each of them offers a consumer subscription that currently gives far more AI usage then you can get by paying directly for AI on a per token basis. They each have their own special agentic coding app that works well with their own models:

| Company | Product | Current Models (as of Sep 2026) |
| --- | --- | --- |
| OpenAI | ChatGPT / API | GPT-6 Astra (flagship, released Sep 4, 2026); GPT-5.6 Sol, GPT-5.6 Terra, GPT-5.6 Luna (frontier family, Jul 9, 2026); GPT-5.5 / GPT-5.5 Pro; GPT-5.4 / GPT-5.4 Pro; GPT-5.4 mini & nano |
| Anthropic | Claude Code/Cowork App | Claude Fable 5.1 (released Sep 1, 2026, most capable GA model); Claude Opus 5; Claude Sonnet 5; Claude Haiku 4.5; Claude Mythos 5.1 (restricted access) |
| Google | Antigravity | Gemini models|

By default, we will use the ChatGPT app from OpenAI, because they are currently (through October 2026) offering a free 4-month GPT Plus subscription to students.

### 1. Sign up for a "Plus" or "Pro" subscription
If this free offer for 4 months of GPT Plus applies to you, you can sign up here: https://z.umn.edu/2521chatgptoffer
If not, or if you prefer to use another provider, you can sign up for Claude Pro ($20/month if billed monthly) at https://claude.ai, or Google AI Pro ($19.99/month) at https://gemini.google.com.

### 2. Download and install the app, and sign in
If using ChatGPT, go to https://chatgpt.com/download/. Download and install the ChatGPT app on your computer. Open it and sign in.

If using Claude, go to https://claude.com/download. Download and install the Claude Desktop app, then open the app and sign in.

If using Gemini (Google), go to https://antigravity.google/download. Download and install the Antigravity app, then open the app and sign in.

## Set up an API-based app
By default, we will use OpenRouter as our API-based inference provider, Visual Studio Code (VS Code) as our coding app, and the Kilo Code extension inside VS Code to manage our agentic coding interactions. But there are some alternatives discussed below.

### 1. Choose an API provider

There are many options. Top three recommendations for this class:

- TensorX, https://tensorx.ai/ (Recommended)

Currently operating only in Finland and Ireland (according to their sales rep). Only has open-weights models (not the big proprietary AI models like GPT, Claude, Gemini). But the proprietary models are generally too expensive to use on a $20 budget anyway, and some of the open-weights models are good enough for our needs.

- Openrouter, https://openrouter.ai/

Openrouter is probably the biggest inference provider because they route to many different back-end providers. They are an aggregator for other providers. Sometimes lower rates, sometimes faster, and 400+ models to choose from. Downside is you don't know where (in the world) your queries are getting sent. It is possible to pin Openrouter inference to Europe-only, by replacing their URL with `https://eu.openrouter.ai`. This does not guarantee very low impact data centers because there are some data centers, especially in southern Europe, that have moderately high water usage. But the European data centers are, on average, much better than US data centers. However, the model options are much more restricted when using only the EU region. For example, at time of writing, GLM 5.3 Flash is not available through Openrouter in EU only, although DeepSeek V4 Flash 0713 is. Still, this would give you the flexibility to switch between EU and global if you found that you needed more variety of models.

- Lyceum, https://lyceum.ai/
Same as TensorX but currently operating only in Finland (according to their sales rep). This one requires more steps to set up below.

Notes on water use:
I include TensorX and Lyceum because they operate in countries (Finland/Ireland) where the impact of running AI on the local water supply is very low, based on my personal research. 

However, please note: the water difference matters, but it's complicated, and the numbers may not be as high as you think. The total water use is roughly 1 gallon of water used per 100 chat threads if you have long threads (e.g. ~200k words), which is common in coding. In comparison, the typical US data center would use roughly 5 gallons per 100 queries. A single typical shower might use 20-40 gallons, so we're not talking about a huge absolute difference in water use. On the other hand, the same usage at the average US data center has roughly 50 times higher water impact on its local ecosystem in Finland or Ireland, because many US data centers are in regions with high water scarcity.

A much longer list of possible providers is available here: https://docs.google.com/document/d/1hrwaeSnSe27CkmOLg7R3QutlrJUw8MYmc_V_vfnmkXA/edit?usp=sharing. Use at your own risk, because I cannot verify that they will work in our workflows.

### 2. Get an API key and load it with $20.

Once you have chosen your API inference provider, sign up for an account, and purchase $20 of credit to use for AI inference on your API key. There will be a page that shows you your API key or that lets you create an API key. Copy this API key and save it somewhere secure, like in a password manager. If possible, just keep this window open while you do the next steps so that you can copy the API key and paste it into another app directly.
 
### 3. Install your code editor
We will use Visual Studio Code. Download and install the app on your computer: [https://code.visualstudio.com](https://code.visualstudio.com/)

### 4. Install an agentic coding extension in VS Code
VS code does offer a built-in agentic coding tool, but they don't easily show your token usage and API spending in real time.

We will use the Kilo Code extension, as follows:

1. Open VS Code
2. Click on the "Extensions" button on the left
3. Type `Kilo` in the search bar
4. Click to install Kilo Code extension
  - <img width="400" alt="install-kilo-code" src="https://github.com/user-attachments/assets/2194eaae-7fc2-4445-a8a6-3df5297c6931" />
  - If required, create an account on kilo.ai and log in to the Kilo Code extension in VS Code
5. If a yellow `Kilo` button does not appear near the top right of your window, quit and repoen VS Code.
6. Click the yellow `Kilo` button near the top right of your window <img height="30" alt="image" src="https://github.com/user-attachments/assets/0dc22fb8-d54f-41c8-ac56-a457eb6e2828" />.
7. In the new tab, click the settings icon top right near the yellow kilo icon. <img height="30" alt="image" src="https://github.com/user-attachments/assets/5e27437d-429b-4d11-8c8a-75b8da8b84e8" />.
8. Click "Providers" on the left. <img height="200" alt="image" src="https://github.com/user-attachments/assets/06eb967f-8566-4800-bad5-f1d449470b00" />.
9. Add your provider
  - If using Openrouter (from above), click "+ Connect" for Openrouter. Paste in the API key from above.
  - If using TensorX, or another provider that is not Lyceum, click "Show more providers," search for the provider's name, and click "+ Connect". Paste in the API key from above.
  - If using Lyceum or a provider you cannot find in the list, 
    - In the new window enter a lowercase name (like `tensorx`), a display name (like `TensorX`)
    - Paste in the URL for that provider's API (often called an *endpoint*), looks like https://api.tensorx.ai/v1
    - Paste in your API key
    - Scroll down and you should see a list of models available, like this: <img height="250" alt="image" src="https://github.com/user-attachments/assets/fc0c1700-468c-431a-9a01-767675c65588" />
    - Scroll down and click "Add models" <img  height="30" alt="image" src="https://github.com/user-attachments/assets/58b6628f-8dd2-4c46-b9a2-0af270a52ff0" />
    - Scroll back up and click "Toggle reasoning for all" and "Toggle image for all" <img height="30" alt="image" src="https://github.com/user-attachments/assets/c0bbf56a-1fa6-49a6-bf57-187abcf7b531" />.
    - Scroll down to the model, "DeepSeek V4 Flash 0731" (if it is there) and deselect "Image" (because we may use that model and it does not handle images). <img height="90" alt="image" src="https://github.com/user-attachments/assets/2419d024-3e35-41a5-bdf0-491cfe664a7f" />.
    - Scroll down to the bottom and click "Submit".

###  5. Test it out.
Make sure your provider is working inside Kilo code extension, inside VS Code.

1. Close the Kilo Code Settings tab if it's open
2. Open a new Kilo Code tab (click the yellow "Kilo Code" top right) if you don't already have one open. 
3. Ask a simple question, like "what model is this?". It should answer, something like this:
<img width="1382" height="951" alt="image" src="https://github.com/user-attachments/assets/ebeaf3c0-32fd-4b50-908a-e5addc225129" />

### 6. Privacy settings
1. VS code doesn't use your data as long as you're not logged in to it and using "Copilot" as your AI. 
2. Kilo does not claim that they can train on your data, but they do say that you are subject to the privacy policy of the API provider you use. Kilo is a harness here, not the actual inference provider. See https://kilo.ai/privacy.
3. If you used TensorX, they claim zero data retention, although it's always good to read their privacy policy:
<img width="1161" height="587" alt="image" src="https://github.com/user-attachments/assets/d6e865c6-70a1-49d9-8caf-884cd41ccde6" />

4. If you used OpenRouter, click your profile name top right, then Privacy, then turn *on* all of the toggles under Zero data retention, and turn *off* all of the toggles under Data Training:
<img height="800" alt="image" src="https://github.com/user-attachments/assets/2a5cf86e-4063-4f05-89c0-c829f917786e" />

5. 
6. s


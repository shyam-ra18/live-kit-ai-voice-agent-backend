Based on the Python setup instructions from the LiveKit Voice AI quickstart, here's a comprehensive README file:

# LiveKit Voice AI Assistant - Python

A simple voice assistant built with LiveKit Agents for Python that you can speak to in your terminal, browser, telephone, or native app.

## 🚀 Quick Start

Build and deploy a voice assistant in less than 10 minutes using LiveKit Agents for Python.

## 📋 Requirements

- **Python** >= 3.9
- **uv** package manager ([installation guide](https://docs.astral.sh/uv/getting-started/installation/))
- **LiveKit Cloud** account ([sign up free](https://cloud.livekit.io/))
- **AI Provider API Keys** (choose one setup below)

## 🛠️ Setup

### 1. Install LiveKit CLI

**macOS:**

```bash
brew install livekit-cli
```

**Linux:**

```bash
curl -sSL https://get.livekit.io/cli | bash
```

**Windows:**

```bash
winget install LiveKit.LiveKitCLI
```

### 2. Authenticate with LiveKit Cloud

```bash
lk cloud auth
```

### 3. Create Project

```bash
uv init livekit-voice-agent --bare
cd livekit-voice-agent
```

## 🔌 AI Provider Setup

### Option A: STT-LLM-TTS Pipeline (Recommended)

**Required API Keys:**

- Deepgram API Key (for speech-to-text)
- OpenAI API Key (for language model)
- Cartesia API Key (for text-to-speech)

**Install dependencies:**

```bash
uv add \
  "livekit-agents[deepgram,openai,cartesia,silero,turn-detector]~=1.2" \
  "livekit-plugins-noise-cancellation~=0.2" \
  "python-dotenv"
```

### Option B: Realtime Model

**Required API Key:**

- OpenAI API Key (for realtime voice model)

**Install dependencies:**

```bash
uv add \
  "livekit-agents[openai]~=1.2" \
  "livekit-plugins-noise-cancellation~=0.2" \
  "python-dotenv"
```

## ⚙️ Configuration

### 1. Load Environment Variables

```bash
lk app env -w
```

### 2. Edit `.env.local`

**For STT-LLM-TTS Pipeline:**

```env
DEEPGRAM_API_KEY=<Your Deepgram API Key>
OPENAI_API_KEY=<Your OpenAI API Key>
CARTESIA_API_KEY=<Your Cartesia API Key>
LIVEKIT_API_KEY=%{apiKey}%
LIVEKIT_API_SECRET=%{apiSecret}%
LIVEKIT_URL=%{wsURL}%
```

**For Realtime Model:**

```env
OPENAI_API_KEY=<Your OpenAI API Key>
LIVEKIT_API_KEY=%{apiKey}%
LIVEKIT_API_SECRET=%{apiSecret}%
LIVEKIT_URL=%{wsURL}%
```

## 💻 Agent Code

Create `agent.py` with the following content:

## 📥 Download Model Files

```bash
uv run agent.py download-files
```

## 🎤 Test Your Agent

### Console Mode (Terminal)

```bash
uv run agent.py console
```

### Development Mode (LiveKit Cloud)

```bash
uv run agent.py dev
```

### Production Mode

```bash
uv run agent.py start
```

## 🚀 Deploy to LiveKit Cloud

```bash
lk agent create
```

## 📚 Next Steps

- [Web and mobile frontends](https://docs.livekit.io/agents/start/frontend.md)
- [Telephony integration](https://docs.livekit.io/agents/start/telephony.md)
- [Testing your agent](https://docs.livekit.io/agents/build/testing.md)
- [Building voice agents](https://docs.livekit.io/agents/build.md)

## 🔗 Resources

- [LiveKit Documentation](https://docs.livekit.io/)
- [Python Starter Project](https://github.com/livekit-examples/agent-starter-python)
- [LiveKit Cloud](https://cloud.livekit.io/)

## 📝 License

This project uses LiveKit Agents. See [LiveKit documentation](https://docs.livekit.io/) for licensing information.

---

_This README is based on LiveKit Voice AI quickstart documentation. For the latest updates, visit the [official docs](https://docs.livekit.io/agents/start/voice-ai.md)._

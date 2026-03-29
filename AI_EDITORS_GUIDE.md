# 🎨 Using AI OS with Any AI Editor

This guide shows you how to use AI OS with different AI-powered editors and platforms.

---

## 📋 Supported Editors & Platforms

| Editor | Best For | Setup Time |
|--------|----------|-----------|
| **Cursor** | Full integration, chat + code | 5 min |
| **ChatGPT** | Quick sessions, no setup | 1 min |
| **Claude** | Long context, deep reasoning | 1 min |
| **VS Code + Copilot** | Existing VS Code users | 5 min |
| **Windsurf** | Fork of Cursor | 5 min |
| **Any LLM API** | Self-hosted or custom | 10 min |

---

## 🎯 Cursor (RECOMMENDED)

### Why Cursor?
- ✅ Native AI integration in editor
- ✅ Sees all your workspace files
- ✅ Chat persists across sessions
- ✅ Can edit code directly
- ✅ Best for full projects

### Setup

```bash
# 1. Install Cursor
# Download from https://www.cursor.sh

# 2. Open AI OS project in Cursor
cd my-project
cursor .

# 3. Start chat (⌘K or Ctrl+K)
```

### Usage

**First message:**
```
I'm using AI OS. Here are my project files:

CONTEXT.md - project definition
PROJECT_PLAN.md - agent configuration
STATE.md - current state
AGENTS.md - boot sequence

Follow AGENTS.md boot sequence. Run /plan
```

**Then:**
```
/build          # Implement current task
/review         # Check quality
/debug [bug]    # Fix bug
/optimize       # Improve performance
```

### Full Guide
See `CURSOR_GUIDE.md` in this project

---

## 💬 ChatGPT (Web or API)

### Why ChatGPT?
- ✅ Instant access via web
- ✅ No setup needed
- ✅ Large context window
- ✅ Good at code generation

### Setup

1. Go to [ChatGPT](https://chat.openai.com)
2. Create new chat
3. Paste prompt (below)

### Usage — First Session

**Paste this (all at once):**
```
I'm using AI OS, a modular agent framework.

Here's my project definition:
[PASTE CONTEXT.md HERE]

Here's my configuration:
[PASTE PROJECT_PLAN.md HERE]

Here's my current state:
[PASTE STATE.md HERE]

Here's the boot sequence I need to follow:
[PASTE AGENTS.md HERE]

Now, follow the boot sequence:
1. Read all files
2. Extract active agents from PROJECT_PLAN.md Section 3
3. Use Section 4 task-to-agent mapping
4. Run /plan to sequence the work

Let's begin.
```

### Usage — Subsequent Tasks

**For building code:**
```
/build the next pending task from STATE.md

Current Focus: [current focus from STATE.md]

Here's the context:
[PASTE relevant file: models.py, schema.sql, etc]
```

**For reviewing code:**
```
/review this component:

[PASTE code to review]

Check for:
- Logic errors
- Security issues (if applicable)
- Performance problems
- Edge cases

Verdict: PASS or BLOCKED?
```

**For fixing bugs:**
```
/debug

Error: [error message]

Here's the code:
[PASTE code]

Root cause?
```

### At End of Session

**Save your progress:**
```
Generate updated STATE.md based on:
- Completed components
- Current focus
- Any decisions made

Format as markdown.
```

**Copy the output** and save to `STATE.md` in your project

### Next Session

Start with:
```
Here's my updated project state:
[PASTE STATE.md]

Continue from Current Focus. /build
```

---

## 🧠 Claude (Anthropic)

### Why Claude?
- ✅ Excellent reasoning
- ✅ Very large context (100k tokens)
- ✅ Long conversations supported
- ✅ Can upload files

### Setup

1. Go to [Claude](https://claude.ai) or use Anthropic API
2. Create new conversation
3. Upload or paste files

### Usage — Method 1: Paste Files

```
I'm using AI OS for development. Here are my files:

[Upload or paste CONTEXT.md]
[Upload or paste PROJECT_PLAN.md]
[Upload or paste STATE.md]
[Upload or paste AGENTS.md]

Follow boot sequence from AGENTS.md.
Run /plan.
```

### Usage — Method 2: Chat-Based

**Start:**
```
I'm using AI OS. My project is:
[describe in 1-2 sentences]

My tech stack:
[list tech]

My MVP goals:
[list 3 goals]

Please act as the AI Development OS.
Read my files (I'll paste them below):

[paste all files]

Boot sequence: /plan
```

**Continue:**
```
/build

Here's what I've built so far:
[optional: paste existing code]
```

### Claude-Specific Tips

- **Use file uploads** instead of pasting for big projects
- **Create a "System" role** with AI OS rules:
  ```
  You are AI Development OS. 
  Use ONLY active agents from PROJECT_PLAN.md Section 3.
  Update STATE.md after every task.
  Follow workflows from WORKFLOWS.md.
  ```

- **Leverage long context** by pasting entire project history
- **Ask for specific formats:**
  ```
  /build in this format:
  
  ## Files to Create
  [list]
  
  ## File 1: [path]
  [code]
  
  ## File 2: [path]
  [code]
  ```

---

## 🆚 VS Code + GitHub Copilot

### Why VS Code + Copilot?
- ✅ Familiar IDE experience
- ✅ Code completion inline
- ✅ Chat panel support
- ✅ Works offline (with context)

### Setup

```bash
# 1. Install VS Code
# Download from https://code.microsoft.com

# 2. Install GitHub Copilot extension
# In VS Code: Extensions → Search "GitHub Copilot" → Install

# 3. Sign in with GitHub account

# 4. Open AI OS project
code my-project
```

### Usage

**Open Copilot Chat:**
- Press `Cmd+Shift+I` (Mac) or `Ctrl+Shift+I` (Windows/Linux)

**First message:**
```
@workspace I'm using AI OS.

Read these files:
- PROJECT_PLAN.md (my configuration)
- CONTEXT.md (my project definition)
- STATE.md (my current state)
- AGENTS.md (boot sequence)

Follow boot sequence. Run /plan
```

**For subsequent tasks:**
```
@workspace /build

Here's my current file:
[Select code in editor, Copilot shows it with @file]

Implement next task.
```

### VS Code + Copilot Tips

- **Use @workspace** to reference all files
- **Use @file path/to/file.py** to reference specific files
- **Select code in editor** then type `@` in chat to reference it
- **Create `.vscode/settings.json`** to configure Copilot behavior:
  ```json
  {
    "github.copilot.enable": {
      "yaml": true,
      "markdown": true,
      "plaintext": true
    }
  }
  ```

---

## 🌊 Windsurf (Codeium)

### Why Windsurf?
- ✅ Based on Cursor architecture
- ✅ Free and open-source
- ✅ Similar workflow to Cursor

### Setup

```bash
# 1. Install Windsurf
# Download from https://codeium.com/windsurf

# 2. Open project
windsurf my-project

# 3. Open chat (similar to Cursor)
```

### Usage

Same as Cursor:
```
Boot sequence: [paste from AGENTS.md]
/plan
/build
/review
```

---

## 🤖 Local LLM (Ollama, LM Studio, etc.)

### Why Local LLM?
- ✅ Privacy (runs on your machine)
- ✅ Free (no API costs)
- ✅ Works offline
- ❌ Slower than cloud APIs

### Setup (Example: Ollama)

```bash
# 1. Install Ollama
# Download from https://ollama.ai

# 2. Pull a model
ollama pull mistral  # or llama2, neural-chat, etc.

# 3. Run Ollama
ollama serve

# 4. In your editor, configure LLM endpoint
# Usually: http://localhost:11434
```

### Usage

**Create a prompt file:**
```
system_prompt.md:

You are an AI Development OS.

Project Definition:
[paste CONTEXT.md]

Configuration:
[paste PROJECT_PLAN.md]

Current State:
[paste STATE.md]

Boot Sequence:
[paste AGENTS.md]

Rules:
1. Read all files
2. Extract active agents from PROJECT_PLAN.md Section 3
3. Route tasks using Section 4 mapping
4. Update STATE.md after every task
5. Follow workflows from WORKFLOWS.md

Available commands: /plan, /build, /review, /debug, /optimize

When user says /plan, generate detailed task sequence.
When user says /build, generate complete, runnable code.
When user says /review, check code quality and security.
When user says /debug, analyze and fix bugs.
When user says /optimize, improve performance.
```

**Use with curl:**
```bash
curl http://localhost:11434/api/generate -d '{
  "model": "mistral",
  "prompt": "Read PROJECT_PLAN.md... /plan",
  "stream": false
}'
```

**Or use Python:**
```python
import requests
import json

def ask_ai(prompt):
    response = requests.post(
        'http://localhost:11434/api/generate',
        json={
            'model': 'mistral',
            'prompt': prompt,
            'stream': False
        }
    )
    return response.json()['response']

# Boot sequence
prompt = open('CONTEXT.md').read() + open('STATE.md').read() + "/plan"
print(ask_ai(prompt))
```

---

## 🔌 Any LLM API (OpenAI, Anthropic, HuggingFace, etc.)

### Setup for OpenAI API

```python
import openai

openai.api_key = "sk-..."

messages = [
    {
        "role": "system",
        "content": """You are AI Development OS.
        
Project files:
[CONTEXT.md content]
[PROJECT_PLAN.md content]
[STATE.md content]
[AGENTS.md content]

Always:
1. Read all files
2. Use only active agents
3. Update STATE.md after tasks
4. Follow workflows
"""
    },
    {
        "role": "user",
        "content": "Boot sequence: /plan"
    }
]

response = openai.ChatCompletion.create(
    model="gpt-4",
    messages=messages
)

print(response['choices'][0]['message']['content'])
```

### Setup for Claude API

```python
import anthropic

client = anthropic.Anthropic(api_key="sk-ant-...")

system_prompt = """You are AI Development OS.

[CONTEXT.md content]
[PROJECT_PLAN.md content]
[STATE.md content]
[AGENTS.md content]

Follow boot sequence. Run /plan.
"""

message = client.messages.create(
    model="claude-3-opus-20240229",
    max_tokens=4096,
    system=system_prompt,
    messages=[
        {
            "role": "user",
            "content": "Boot sequence from AGENTS.md. Run /plan"
        }
    ]
)

print(message.content[0].text)
```

### Setup for HuggingFace API

```python
import requests

API_URL = "https://api-inference.huggingface.co/models/meta-llama/Llama-2-7b-chat-hf"
headers = {"Authorization": f"Bearer hf_..."}

def query(prompt):
    payload = {"inputs": prompt}
    response = requests.post(API_URL, headers=headers, json=payload)
    return response.json()

system_context = open('CONTEXT.md').read() + open('STATE.md').read()
response = query(system_context + "\n/plan")
print(response)
```

---

## 🔄 IDE-Agnostic Workflow

### If You Use a Different Editor

1. **Create a `AIChat.md` file** in your project
2. **Paste bot messages here:**
   ```markdown
   # AI OS Session Log
   
   ## Message 1: Boot Sequence
   [Paste your boot sequence prompt]
   
   ## Response 1: Planning
   [Paste LLM response with /plan output]
   
   ## Message 2: Build Request
   /build
   
   ## Response 2: Code Generated
   [Paste generated code]
   
   [Repeat...]
   ```

3. **Update STATE.md** manually after each session
4. **Reference the chat log** in next session

### Generic Workflow

```
Session Start:
  1. Paste CONTEXT.md + PROJECT_PLAN.md + STATE.md to LLM
  2. Ask for /plan
  3. Follow task sequence

During Development:
  1. Say /build
  2. Get code
  3. Copy to editor
  4. Say /review
  5. Fix any issues
  6. Move to next task

Session End:
  1. Save chat log or ask LLM for updated STATE.md
  2. Save STATE.md to file
  3. Commit to git

Next Session:
  1. Paste updated STATE.md
  2. Continue from Current Focus
  3. Say /build
```

---

## 🚀 Quick Comparison

| Task | Cursor | ChatGPT | Claude | VS Code+Copilot | Local LLM |
|------|--------|---------|--------|-----------------|-----------|
| **Setup time** | 5 min | 1 min | 1 min | 5 min | 15 min |
| **Best for** | Full projects | Quick work | Deep reasoning | IDE users | Privacy |
| **Code integration** | ⭐⭐⭐⭐⭐ | ⭐⭐ | ⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |
| **Context persistence** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ |
| **Speed** | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ |
| **Cost** | $20/mo | $20/mo | $20/mo | Free | Free |

---

## 📝 Universal Tips

### 1. Keep STATE.md Updated
Always update STATE.md after each session:
```markdown
## Last Updated
2024-03-29 - Completed Phase 1: Foundation
```

### 2. Use Markdown Formatting
AI editors love markdown:
```markdown
## /plan output

Phase 1: Foundation

Tasks:
1. Setup
2. Database
3. Auth

## File 1: config.py
[code block]

## File 2: database.py
[code block]
```

### 3. Reference Files Explicitly
Help LLM understand your project:
```
I have these files:
- backend/models.py (User, Todo models)
- backend/routes/auth.py (JWT routes)
- backend/routes/todos.py (CRUD endpoints)

[Show relevant code snippets]

Now /build [next component]
```

### 4. Save Session Logs
Keep records of what was done:
```bash
# Save chat logs
cp AIChat.md AIChat.session-2024-03-29.md
```

### 5. Commit to Git
After each session:
```bash
git add -A
git commit -m "Session: Completed Phase 2 Auth"
```

---

## 🆘 Troubleshooting

### "LLM forgot my project context"
→ Paste CONTEXT.md + STATE.md + AGENTS.md at the start of next message

### "Code generated is incomplete"
→ Ask: "Continue the implementation for [component]"

### "Chat is too large/slow"
→ Start a new chat, paste STATE.md at the top to resume

### "LLM is ignoring my agent setup"
→ Emphasize in every message: "Use ONLY agents from PROJECT_PLAN.md Section 3"

### "Can't copy code from LLM output"
→ Ask LLM to format as code blocks:
```
Please provide all code in markdown code blocks with file paths.
```

---

## 🎓 Final Recommendation

| For | Use |
|-----|-----|
| Best overall | **Cursor** |
| Quick prototyping | **ChatGPT** |
| Deep reasoning | **Claude** |
| Existing VS Code users | **Copilot** |
| Privacy-first | **Local LLM** |
| Cost-conscious | **Local LLM** |

---

**Pick your editor and start building! 🚀**

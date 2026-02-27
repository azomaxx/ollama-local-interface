# Local AI Development Environment

A private AI workspace powered by **AnythingLLM** + **Ollama** for code generation, review, and document analysis.

## 📋 Overview

This setup provides a completely local, offline-capable AI assistant with a professional interface. All processing happens on your machine - no data leaves your computer, giving you complete privacy and control.

**Stack:**
- **AnythingLLM**: Desktop interface for document management and RAG
- **Ollama**: Local LLM runtime and model management

## ⚡ Quick Setup (First Time)

1. **Install Ollama** (if not already installed)
   - Download from [ollama.com](https://ollama.com/)
   - Install and run

2. **Pull the Model**
   ```bash
   ollama pull llama3.2:3b
   ```

3. **Install AnythingLLM**
   - Download from [anythingllm.com/download](https://anythingllm.com/download)
   - Install and launch

4. **Connect AnythingLLM to Ollama**
   - Open AnythingLLM → **Settings → AI Providers**
   - Select **Ollama** (auto-detected)
   - Choose model: **llama3.2:3b**
   - Save

5. **Start Using**
   - Create a workspace
   - Upload code/documents
   - Start chatting!

---

## 🤖 Installed Model

| Model | Size | Purpose |
|-------|------|---------|
| **llama3.2:3b** | ~2 GB | Efficient all-rounder for code generation, pentesting, and document analysis |

**Hardware:** Optimized for systems with ~10GB available RAM

### Why This Model?

**Llama 3.2 (3B)** is specifically chosen for:
- ✅ **Pentesting**: Good understanding of security concepts, vulnerabilities, and exploit patterns
- ✅ **Code Generation**: Proficient in multiple languages (Python, JavaScript, Go, etc.)
- ✅ **Legal Document Analysis**: Strong reading comprehension for contracts, compliance docs, and terms of service
- ✅ **Hardware Efficient**: Only 2GB model size fits comfortably in 10GB RAM systems
- ✅ **Fast Response**: Smaller model = quicker generation

### Alternative Models

If you need more specialized capabilities or have different hardware:

```bash
# Better for pure coding (requires ~4GB RAM)
ollama pull codellama:7b

# Even smaller, code-focused (1.6GB)
ollama pull codegemma:2b

# Alternative reasoning model (2.3GB)
ollama pull phi3:mini

# Larger, more capable (requires 8GB+ available RAM)
ollama pull llama3.2    # 7B version
```

## 🚀 Quick Start

### Using AnythingLLM (Primary Interface)

**Basic Chat:**
1. Launch AnythingLLM
2. Select or create a workspace
3. Start typing in the chat box

**Code Review Workflow:**
1. Create workspace: "Code Review"
2. Upload your code files
3. Ask: "Review this codebase for security issues"
4. The AI analyzes all uploaded files

**Code Generation:**
1. Describe what you need
2. Copy generated code
3. Iterate with follow-up questions

### Direct Ollama CLI (Advanced)

**Start a chat session:**
```bash
ollama run llama3.2:3b
```

**Exit the chat:**
Type `/bye` or press `Ctrl+D`

### Command Line Interface

**Generate a response:**
```bash
ollama run llama3.2:3b "Explain how async/await works in Python"
```

**Pipe input for code review:**
```bash
type myfile.py | ollama run llama3.2:3b "Review this code for bugs and improvements"
```

## 💻 Common Use Cases

### Code Generation
```bash
ollama run llama3.2:3b "Write a Python function that calculates fibonacci numbers with memoization"
```

### Code Review & Security Analysis
```bash
ollama run llama3.2:3b "Review this function for security vulnerabilities: [paste code]"
```

### Pentesting & Security
```bash
ollama run llama3.2:3b "Explain common SQL injection techniques and how to test for them"

ollama run llama3.2:3b "Write a Python script to enumerate subdomains using DNS queries"

ollama run llama3.2:3b "Analyze this web application flow for potential CSRF vulnerabilities"
```

### Legal Document Analysis
- Upload contracts, NDAs, terms of service to AnythingLLM
- Ask: "Summarize the key obligations in this contract"
- Ask: "What are the liability limitations in section 8?"
- Ask: "Identify any unusual or concerning clauses"

### Code Explanation
```bash
ollama run llama3.2:3b "Explain what this regex does: ^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$"
```

### Debugging & Error Analysis
```bash
ollama run llama3.2:3b "I'm getting a 'NullPointerException' in Java. What are common causes and how do I debug it?"
```

## 🛠️ Ollama Commands

### Model Management
```bash
# List all installed models
ollama list

# Show model details
ollama show llama3.2:3b

# Remove a model (to free space)
ollama rm llama3.2:3b

# Pull/download a new model
ollama pull codellama:7b

# Pull a different size variant
ollama pull llama3.2    # 7B version
```

### System Management
```bash
# Check Ollama version
ollama --version

# Stop the Ollama service
# (Close the Ollama app or stop the service)
```

## 🌐 Interface: AnythingLLM

### Installation
1. **Download AnythingLLM Desktop**
   - Visit: [https://anythingllm.com/download](https://anythingllm.com/download)
   - Download Windows installer
   - Run installer and launch application

2. **Connect to Ollama**
   - Open AnythingLLM
   - Go to **Settings → AI Providers**
   - AnythingLLM will autodetect Ollama running locally
   - Select **Ollama** as your LLM provider
   - Choose model: **llama3.2:3b**
   - Save settings

3. **Create Your First Workspace**
   - Click "New Workspace"
   - Name it (e.g., "Code Assistant")
   - Start chatting!

### Key Features

**📁 Document Management**
- Upload files (code, PDFs, docs) to workspaces
- Automatic RAG (Retrieval Augmented Generation)
- The AI references your documents in responses

**💼 Workspaces**
- Organize projects separately
- Different settings per workspace
- Keep code projects isolated

**🔍 RAG for Code**
- Upload your codebase
- Ask questions about your code
- Get context-aware suggestions

**💾 Chat History**
- All conversations saved locally
- Search previous chats
- Export conversations

## 🎯 Quick Start with AnythingLLM

### Upload Code for Review
1. Create workspace: "Code Review"
2. Upload files (drag & drop)
3. Ask: "Review the security issues in auth.py"

### Code Generation
- Simply chat: "Create a REST API in Flask with JWT authentication"
- AnythingLLM maintains context across messages

### Multi-file Analysis
- Upload entire project folders
- Ask: "Find all database queries and suggest optimizations"
- The AI searches across all uploaded files

## 📝 API Usage

Ollama exposes a REST API at `http://localhost:11434`

**Example (curl):**
```bash
curl http://localhost:11434/api/generate -d '{
  "model": "llama3.2:3b",
  "prompt": "Write a hello world in Python"
}'
```

**Example (Python):**
```python
import requests
import json

response = requests.post('http://localhost:11434/api/generate',
    json={
        "model": "llama3.2:3b",
        "prompt": "Explain list comprehensions in Python",
        "stream": False
    })

print(response.json()['response'])
```

## 🔧 Configuration

### Model Parameters
Create a `Modelfile` to customize behavior:
```dockerfile
FROM llama3.2:3b

# Set temperature (0.0-1.0, higher = more creative)
PARAMETER temperature 0.7

# Set context window size
PARAMETER num_ctx 4096

# Set system prompt
SYSTEM You are a security-focused coding assistant specialized in pentesting, secure code review, and legal document analysis.
```

Apply with:
```bash
ollama create my-custom-model -f Modelfile
```

## 💡 Tips for Code Tasks

### In AnythingLLM

1. **Use Workspaces Wisely**
   - One workspace per project/topic
   - Upload relevant documentation
   - Context persists within workspace

2. **Upload Your Codebase**
   - Drag & drop entire folders
   - Supports: .py, .js, .java, .cpp, .go, etc.
   - The AI can reference any uploaded file

3. **Ask Specific Questions**
   - ✅ "Find SQL injection vulnerabilities in api/routes.py"
   - ✅ "Refactor the authentication logic to use JWT"
   - ❌ "Fix my code" (too vague)

4. **Leverage RAG**
   - Upload documentation alongside code
   - Upload error logs for debugging
   - Upload API specs for integration work

5. **Iterate and Refine**
   - Follow up with clarifications
   - Ask for alternatives: "Show me 3 different approaches"
   - Request specific formats: "Add type hints and docstrings"

### Command Line Tips

1. **Be specific**: "Write a Python function that..." is better than "Write code"
2. **Provide context**: Include error messages, relevant code snippets
3. **Request formats**: Ask for "step-by-step", "with comments", "production-ready code"

## 🔄 Common Workflows

### Workflow 1: Full Codebase Review
1. Create workspace: "ProjectName Review"
2. Upload entire project folder
3. Ask: "Analyze this codebase and identify:"
   - Security vulnerabilities
   - Performance bottlenecks
   - Code smell and anti-patterns
   - Missing error handling

### Workflow 2: Feature Development
1. Create workspace: "New Feature - [Feature Name]"
2. Upload relevant existing code
3. Upload requirements/specs document
4. Ask: "Based on the existing code structure, implement [feature]"
5. Review and iterate on the generated code

### Workflow 3: Bug Fixing
1. Create workspace: "Debug - [Issue]"
2. Upload problematic files
3. Upload error logs/stack traces
4. Ask: "Why am I getting this error? Here's the stack trace: [paste]"
5. Get explanation and fix suggestions

### Workflow 4: Documentation Generation
1. Upload code files to workspace
2. Ask: "Generate comprehensive documentation for this module"
3. Ask: "Create API documentation with examples"
4. Export the documentation

### Workflow 5: Code Migration
1. Upload old codebase
2. Ask: "Convert this Python 2.7 code to Python 3.10"
3. Or: "Refactor this JavaScript to TypeScript"
4. Review changes line by line

## 🔒 Privacy & Security

- ✅ All processing happens locally
- ✅ No data sent to external servers
- ✅ Works completely offline
- ✅ No API keys or subscriptions needed

## 📊 System Requirements

**Current Setup:**
- **RAM**: 10GB available (model uses ~2GB)
- **Disk**: 5GB free space (for model + AnythingLLM)
- **CPU**: Multi-core processor (GPU optional but helps)

**Performance Tips:**
- Close unnecessary applications when running
- First response is slower (model loading into RAM)
- Subsequent responses are much faster
- GPU acceleration significantly improves speed if available

## 🐛 Troubleshooting

### AnythingLLM Issues

**Can't connect to Ollama:**
1. Verify Ollama is running: `ollama list`
2. Check AnythingLLM settings: **Settings → AI Providers**
3. Ensure Ollama is detected and selected
4. Try restarting both Ollama and AnythingLLM

**Model not appearing:**
```bash
# Verify model exists
ollama list

# Make sure you selected Ollama as provider in AnythingLLM settings
```

**Uploaded files not being referenced:**
- Check workspace settings → "Enable RAG"
- Try re-uploading files
- Ensure file formats are supported

### Ollama Issues

**Model not responding:**
```bash
# Check if Ollama is running
ollama list

# Restart Ollama service
# Close and reopen the Ollama application
```

**Out of memory errors:**
- Close other applications
- AnythingLLM: Reduce context window in workspace settings
- Consider using a smaller model

**Slow responses:**
- First response is slower (model loading)
- Subsequent responses are faster
- GPU acceleration helps significantly
- In AnythingLLM: Reduce "Max Context Length" in workspace settings

## 📚 Resources

### AnythingLLM
- [AnythingLLM Documentation](https://docs.anythingllm.com/)
- [Desktop Installation Guide](https://docs.anythingllm.com/installation-desktop/overview)
- [Workspace Management](https://docs.anythingllm.com/workspace/workspace-management)
- [AnythingLLM GitHub](https://github.com/Mintplex-Labs/anything-llm)

### Ollama
- [Ollama Documentation](https://github.com/ollama/ollama)
- [Ollama Model Library](https://ollama.com/library)
- [API Documentation](https://github.com/ollama/ollama/blob/main/docs/api.md)

## 📄 License

This setup uses open-source tools. Check individual project licenses for details.

---

**Last Updated**: February 2026  
**Model**: llama3.2:3b (2GB)  
**Optimized for**: Pentesting, Code Generation, Legal Document Analysis
# PythonScrathAi

![Python Version](https://img.shields.io/badge/python-3.8%2B-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![LangChain](https://img.shields.io/badge/LangChain-enabled-orange)

A modular AI research assistant agent built from scratch in Python, leveraging LangChain, Claude 3.5, and various research tools to perform intelligent web searches and generate structured research papers.

## 🎯 Overview

PythonScrathAi is an AI-powered research assistant that combines the power of large language models with practical tools to conduct research, gather information from multiple sources, and save structured outputs. The agent uses Claude 3.5 Sonnet via Anthropic's API to intelligently orchestrate research tasks using web search, Wikipedia queries, and file operations.

## ✨ Features

- **AI-Powered Research**: Utilizes Claude 3.5 Sonnet for intelligent query understanding and response generation
- **Multi-Tool Integration**: Seamlessly combines web search (DuckDuckGo), Wikipedia queries, and file operations
- **Structured Output**: Generates research responses in a structured format with topics, summaries, sources, and tools used
- **Modular Architecture**: Clean separation between agent logic, tools, and configuration for easy maintenance and extension
- **Conversation Memory**: Maintains chat history for context-aware interactions
- **Type-Safe Responses**: Uses Pydantic models for validated, structured outputs
- **Extensible Design**: Easy to add new tools and capabilities to the agent

## 📁 Project Structure

```
PythonScrathAi/
├── main.py              # Main agent execution script with LangChain integration
├── tools.py             # Tool definitions (web search, Wikipedia, file operations)
├── requirements.txt     # Python dependencies
├── sample.env           # Environment variables template
└── README.md           # Project documentation
```

### File Descriptions

- **`main.py`**: The core agent script that:
  - Initializes the Claude 3.5 Sonnet LLM
  - Sets up the research assistant prompt with structured output parsing
  - Creates a tool-calling agent with web search, Wikipedia, and save capabilities
  - Executes user queries and returns structured research responses

- **`tools.py`**: Defines the agent's capabilities:
  - `search_tool`: Web search using DuckDuckGo for real-time information
  - `wiki_tool`: Wikipedia queries for encyclopedic knowledge
  - `save_tool`: Saves research outputs to text files with timestamps

- **`requirements.txt`**: Lists all Python dependencies including LangChain, Anthropic, OpenAI, and community tools

- **`sample.env`**: Template for API keys configuration

## 🔧 Prerequisites

- **Python**: Version 3.8 or higher
- **API Keys**: 
  - Anthropic API key (for Claude 3.5 Sonnet)
  - Optional: OpenAI API key (if using OpenAI models)
- **Internet Connection**: Required for web searches and Wikipedia queries

## 📦 Installation

Follow these steps to set up the project:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/httpEduardo/PythonScrathAi.git
   cd PythonScrathAi
   ```

2. **Create a virtual environment** (recommended):
   ```bash
   python -m venv venv
   
   # On Windows
   venv\Scripts\activate
   
   # On macOS/Linux
   source venv/bin/activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**:
   ```bash
   # Copy the sample environment file
   cp sample.env .env
   
   # Edit .env and add your API keys
   # ANTHROPIC_API_KEY="your-anthropic-api-key-here"
   # OPENAI_API_KEY="your-openai-api-key-here"  # Optional
   ```

## ⚙️ Configuration

The agent requires API keys to function. Set up your `.env` file with the following variables:

```env
ANTHROPIC_API_KEY="your-anthropic-api-key-here"
OPENAI_API_KEY="your-openai-api-key-here"  # Optional, only if using OpenAI models
```

### Getting API Keys

- **Anthropic API Key**: Sign up at [console.anthropic.com](https://console.anthropic.com/) and create an API key
- **OpenAI API Key** (optional): Sign up at [platform.openai.com](https://platform.openai.com/) and create an API key

## 🚀 Usage

Run the research assistant agent:

```bash
python main.py
```

The agent will prompt you with:
```
What can i help you research?
```

### Example Queries

**Example 1: Technology Research**
```
What can i help you research? Latest developments in quantum computing
```

**Example 2: Historical Information**
```
What can i help you research? History and impact of the Apollo 11 mission
```

**Example 3: Current Events**
```
What can i help you research? Recent advancements in renewable energy technology
```

### Output Format

The agent returns structured research responses:

```python
ResearchResponse(
    topic="Your research topic",
    summary="Comprehensive summary of findings",
    sources=["source1.com", "source2.com", ...],
    tools_used=["search", "wiki_tool", "save_text_to_file"]
)
```

Research outputs are automatically saved to `research_output.txt` with timestamps.

## 🛠️ Extending the Agent

### Adding New Tools

To add custom tools, edit `tools.py`:

```python
from langchain.tools import Tool

def my_custom_function(input: str) -> str:
    # Your custom logic here
    return "Result"

my_custom_tool = Tool(
    name="my_custom_tool",
    func=my_custom_function,
    description="Description of what this tool does",
)
```

Then add it to the tools list in `main.py`:

```python
tools = [search_tool, wiki_tool, save_tool, my_custom_tool]
```

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/your-feature-name`
3. **Make your changes**: Implement your feature or bug fix
4. **Test your changes**: Ensure everything works as expected
5. **Commit your changes**: `git commit -m "Add: description of your changes"`
6. **Push to your fork**: `git push origin feature/your-feature-name`
7. **Open a Pull Request**: Submit your changes for review

### Development Guidelines

- Follow PEP 8 style guidelines for Python code
- Add docstrings to functions and classes
- Test new features before submitting
- Keep commits atomic and well-described
- Update documentation for new features

## 📝 License

This project is licensed under the MIT License - feel free to use, modify, and distribute as needed.

## 🙏 Acknowledgments

- Built with [LangChain](https://langchain.com/) framework
- Powered by [Anthropic's Claude 3.5 Sonnet](https://www.anthropic.com/)
- Uses [DuckDuckGo Search](https://duckduckgo.com/) and [Wikipedia](https://www.wikipedia.org/) APIs

## 📧 Contact

For questions, issues, or suggestions, please open an issue on GitHub or contact the repository owner.

---

**Note**: This is an educational project demonstrating how to build an AI agent from scratch with modular architecture and practical tool integration.

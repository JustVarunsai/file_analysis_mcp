This server is certified by [MCP Hub](https://mcphub.com) and listed as a trusted MCP server.

# File Analysis MCP Server

A custom-built MCP (Model Context Protocol) server for text file analysis, also published as a package to PyPI.

## Table of Contents
- [Introduction](#introduction)
- [Features](#features) 
- [Installation and Setup from GitHub](#installation-and-setup-from-github)
- [Claude Desktop Integration](#claude-desktop-integration)
- [Installation from Package](#installation-from-Package)

## Introduction

### What is MCP?

Model Context Protocol (MCP) is an open protocol that standardizes how applications provide context to Large Language Models (LLMs). It creates a consistent interface for AI models like Claude to interact with external tools, data sources, and services.

MCP follows a client-server architecture:
- **MCP Hosts**: Programs like Claude Desktop that initiate connections
- **MCP Clients**: Protocol clients inside the host application
- **MCP Servers**: Lightweight programs (like this one) that expose capabilities
- **Local Data Sources**: Your computer's files, databases, and services

### Why MCP?

MCP helps you build agents and complex workflows with LLMs by providing:
- Standardized interfaces to connect AI models to different data sources
- The flexibility to switch between LLM providers
- Best practices for secure data access

## Features

This File Analysis MCP Server provides:
- Text analysis tools (word count, character frequency, etc.)
- File reading capabilities
- Directory listing
- File content access via MCP resources

Text Analysis Tool (`analyze_text`)

File Reader Tool (`read_file`) 

Directory Browsing Tool (`list_files`)

## Installation and Setup from GitHub

### Step 1: Clone the Repository

Start by cloning the repository to your local machine:

```bash
git clone https://github.com/yourusername/file-analysis-mcp.git
cd file-analysis-mcp
```

### Step 2: Set Up UV Package Manager

This project uses UV, a fast Python package manager. If you don't have it installed:

**For MacOS/Linux:**
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**For Windows:**
```bash
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Remember to restart your terminal after installing UV.

### Step 3: Create a Virtual Environment

```bash
# Create and activate a virtual environment
uv venv
```

**For MacOS/Linux:**
```bash
source .venv/bin/activate
```

**For Windows:**
```bash
.venv\Scripts\activate
```

### Step 4: Install Dependencies

```bash
# Install the required dependencies
uv pip install "mcp[cli]"
```

### Testing and Debugging 

Running with the MCP Inspector:
```bash 
uv run mcp dev path/to/your/server/file
```




## Claude Desktop Integration

The real power of your File Analysis server comes when you connect it to Claude Desktop!

### Setting Up with Claude Desktop

1. **Make sure Claude Desktop is installed**
   - Download from [Claude.ai](https://claude.ai/download) if you don't have it

2. **Locate the configuration file**:
   - **MacOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
   - **Windows**: `%AppData%\Claude\claude_desktop_config.json`
   
   If the file doesn't exist, create it.

3. **Add your server configuration**:

   **For MacOS/Linux**:
   ```json
   {
       "mcpServers": {
           "file-analysis": {
               "command": "uv",
               "args": [
                   "--directory",
                   "/ABSOLUTE/PATH/TO/file-analysis-mcp",
                   "run",
                   "server.py"
               ]
           }
       }
   }
   ```

   **For Windows**:
   ```json
   {
       "mcpServers": {
           "file-analysis": {
               "command": "uv",
               "args": [
                   "--directory",
                   "C:\\ABSOLUTE\\PATH\\TO\\file-analysis-mcp",
                   "run",
                   "server.py"
               ]
           }
       }
   }
   ```

   > **Important**: Replace the path with the actual absolute path to where you cloned the repository. Do not use relative paths.

4. **Restart Claude Desktop**
   - Close and reopen the application completely

5. **Verify the connection**
   - Look for the tools icon (hammer) in the Claude interface
   - Your tools should appear in the list when clicking this icon

### Tips for Using Your Server

- **File Paths**: Always provide absolute file paths for best results
- **Large Files**: Break up analysis of very large files into smaller chunks
- **Permissions**: Ensure Claude has permission to access the files/directories you're analyzing

## Installation from Package

### From PyPI (Recommended)

The simplest way to install File Analysis MCP Server is from PyPI:

```bash
pip install file-analysis-mcp
```

Or using UV (recommended):

```bash
uv pip install file-analysis-mcp
```

**Add your server configuration**
```bash
{
  "mcpServers": {
    "mcp-server": {
      "command": "uv",
      "args": [
        "run",
        "mcp-server"
      ]
    }
  }
}
```
## License

[MIT License](LICENSE)

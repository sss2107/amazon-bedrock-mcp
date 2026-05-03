# Amazon Bedrock Converse API MCP Demo

A small Python demo showing how to connect Anthropic's Model Context Protocol (MCP) tool pattern to Amazon Bedrock through the Converse API. The app runs an interactive CLI agent, discovers MCP tools, sends user messages to Bedrock, and executes tool calls when the model requests them.

## What This Project Shows

- Using Amazon Bedrock Converse API from Python
- Wrapping MCP tool discovery and execution behind a client
- Registering tool schemas for model tool use
- Maintaining a simple interactive chat loop
- Running Bedrock-supported models with external tools

## Tech Stack

- Python
- boto3 / Amazon Bedrock Runtime
- MCP client concepts
- SQLite demo tooling

## Repository Structure

```text
.
├── app.py                 # Interactive CLI entry point
├── converse_agent.py      # Bedrock Converse agent loop
├── converse_tools.py      # Tool registration and execution helpers
├── mcp_client.py          # MCP server communication wrapper
├── requirements.txt       # Python dependencies
├── LICENSE
└── CODE_OF_CONDUCT.md
```

## Prerequisites

- Python 3.8+
- AWS account with Bedrock model access enabled
- AWS credentials configured locally
- A local MCP-compatible tool server or demo setup
- SQLite database if following the original MCP quick-start flow

## Setup

```bash
git clone https://github.com/sss2107/amazon-bedrock-mcp.git
cd amazon-bedrock-mcp
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Configure AWS credentials with one of the standard AWS SDK methods:

```bash
aws configure
```

Or export environment variables:

```bash
export AWS_ACCESS_KEY_ID=...
export AWS_SECRET_ACCESS_KEY=...
export AWS_DEFAULT_REGION=us-west-2
```

## Run

```bash
python app.py
```

Type prompts in the terminal. The agent sends messages to Bedrock, handles model responses, executes requested tools, and keeps the conversation moving until you exit.

## Configuration Notes

The demo defaults can be adapted in code for:

- Bedrock region
- Model ID
- MCP server command / connection settings
- SQLite database path

## Security Notes

- Do not commit AWS credentials or local database secrets.
- Keep tool permissions narrow; MCP tools can expose filesystem, database, or network access depending on the server.
- Review every tool schema before exposing it to a model.

## License

This project is licensed under the terms in [LICENSE](LICENSE).
